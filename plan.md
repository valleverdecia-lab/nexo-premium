# Nexo Premium — Plan de implementación

## Dirección elegida

**Movimiento:** mesa de trabajo editorial 2.5D, inspirada en la referencia de ensamblaje interactivo y refinada hacia un showroom de interiorismo premium.

**Principios:** el espacio es la tienda; la interacción es directa y táctil; el catálogo permanece visible sin competir; cada acción produce una respuesta física breve.

**Paleta:** carbón y grafito para el escenario, crema para lectura, azul aqua como señal propia de Nexo y ámbar mínimo para estados de selección. El azul se usa como luz y no como decoración gratuita.

**Layout:** escenario central de gran tamaño con perspectiva, bandeja de productos lateral en escritorio y bottom sheet en móvil; navegación por espacios, no por un grid de tarjetas como pantalla principal.

**Motivos:** plano técnico fino, sombras de contacto y halos de luz que siguen el escenario activo.

**Interacción:** seleccionar o arrastrar un producto lo “eleva” y al soltarlo cae con squash/settle; los objetos seleccionados muestran controles compactos para mover, girar, escalar y eliminar.

**Animación:** solo transform y opacity; entrada de productos en 260–420 ms; cambio de escenario con deslizamiento y morph de iluminación; respetar reduced-motion.

**Tipografía:** Instrument Serif/Georgia para titulares cortos; Inter Tight/Arial para interfaz y precios; JetBrains Mono/monospace para etiquetas técnicas.

**Esencia de marca:** un showroom donde cada compra se prueba en contexto. Precisa, sensorial, práctica.

**Voz:** “Pruebe la composición antes de pedirla.” / “Tres piezas. Un espacio que ya se siente suyo.”

**Marca:** wordmark Nexo Premium acompañado de un punto aqua que pulsa como un sensor de espacio.

## Arquitectura

- `index.html`: shell accesible, navegación de espacios, panel de catálogo, escenario y modal de producto.
- `styles.css`: tokens, escenarios, 2.5D, responsive y motion-safe.
- `app.js`: estado de escenario, clasificación, drag/pointer interactions, transform controls, share/reset/WhatsApp y rendering incremental.
- `data/products.js`: subset completo del catálogo original transformado a la nueva taxonomía; las imágenes viven en `assets/products/`.
- `public/manus-routes.json`: ruta raíz declarada para Preview.
- `TODO.md`: resultados y criterios de aceptación.

## Decisiones de rendimiento

Se reutilizan fotos reales optimizadas del catálogo original, se mantiene el límite de tres objetos, se carga la imagen solo cuando la ficha entra en el viewport y se evita Three.js/modelos GLB permanentes. Los escenarios usan CSS 2.5D con capas de perspectiva, textura, grid y sombras.
