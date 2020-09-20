---
$title: Agregar carruseles
$order: 3
description: Otra característica común en las páginas móviles es un carrusel. Puede agregar fácilmente carruseles a las páginas de AMP utilizando el componente amp-carrusel.
---

Otra característica común en las páginas móviles es un carrusel. Puede agregar carruseles fácilmente a las páginas de AMP mediante el componente [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) . Comencemos con un ejemplo simple, como un carrusel de imágenes.

## Carrusel de imágenes simple

Recuerde incluir la biblioteca de componentes [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) **agregando** la siguiente solicitud de JavaScript a la etiqueta `<head>` de su documento:

```html
<script async custom-element="amp-carousel" src="https://cdn.ampproject.org/v0/amp-carousel-0.1.js"></script>
```

A continuación, integremos un carrusel simple de imágenes con un diseño receptivo y un ancho y alto predefinidos. **Agrega** lo siguiente a tu página:

```html
<amp-carousel layout="fixed-height" height="168" type="carousel" >
  <amp-img src="mountains-1.jpg" width="300" height="168"></amp-img>
  <amp-img src="mountains-2.jpg" width="300" height="168"></amp-img>
  <amp-img src="mountains-3.jpg" width="300" height="168"></amp-img>
</amp-carousel>
```

**Actualice** su página y debería ver un carrusel:

{{image ('/ static / img / docs / tutorials / tut-advanced-carousel-simple.png', 412, 403, align = 'center half', caption = 'Carrusel de imágenes simples')}}

El componente [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) se puede configurar de varias formas. Cambiemos la interfaz de usuario para que muestre solo una imagen a la vez y hagamos que el diseño del carrusel sea receptivo.

To do this, first **change** the `type` of the [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) from `carousel` to `slides`, **change** the `layout` to `responsive` and **set** the `width` to 300 (ensuring it has both a `height` and `width` defined).  **Add** the `"layout=responsive"` attribute to the [`amp-img`](../../../../documentation/components/reference/amp-img.md) children of the [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md).

**Vuelve a cargar** tu página. Ahora, en lugar de una lista de elementos que se desplaza, verá un elemento a la vez. Prueba a **deslizar el dedo** horizontalmente para moverte por los elementos. Si desliza el dedo hacia el tercer elemento, no podrá hacerlo más.

A continuación, **agregue** el atributo de `loop` . **Actualice** la página e intente deslizar el dedo hacia la izquierda inmediatamente. El carrusel da vueltas sin cesar.

Por último, hagamos que este carrusel se reproduzca automáticamente a una velocidad de cada 2 segundos. **Agrega** el atributo de `autoplay` y el atributo de `delay` con un valor de `2000` (por ejemplo, `delay="2000"` ) al [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) .

Su resultado final debería verse así:

```html
<amp-carousel layout="responsive" width="300" height="168" type="slides" autoplay delay="2000" loop>
  <amp-img src="mountains-1.jpg" width="300" height="168" layout="responsive"></amp-img>
  <amp-img src="mountains-2.jpg" width="300" height="168" layout="responsive"></amp-img>
  <amp-img src="mountains-3.jpg" width="300" height="168" layout="responsive"></amp-img>
</amp-carousel>
```

**¡Actualiza** la página y dale una vuelta!

[tip type = "note"] **NOTA -** Es posible que haya notado que cuando el [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) tenía el tipo `carousel` tipo de diseño de `fixed-height` . Los tipos de diseño admitidos para el tipo de `carousel` son limitados; por ejemplo, el `carousel` tipo no soporta `responsive` diseño. Como su nombre lo indica, los elementos de altura fija ocupan el espacio disponible para ellos, pero mantienen la altura sin cambios. Para los elementos de altura fija, debe definir el atributo de `height` , mientras que el atributo de `width` debe ser `auto` o no establecido. [/propina]

## Contenido de carrusel mixto

Los carruseles de imágenes son geniales, pero ¿y si queremos que aparezca contenido más complejo en nuestro carrusel? Intentemos mezclar un poco las cosas colocando un anuncio, algo de texto y una imagen en un solo carrusel. ¿Puede [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) realmente manejar tal mezcla de una vez? ¡Absolutamente!

Primero, **agreguemos** este estilo a su `<style amp-custom>` para garantizar que los componentes [`amp-fit-text`](../../../../documentation/components/reference/amp-fit-text.md) y [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) funcionen juntos de manera segura:

```css
amp-fit-text {
    white-space: normal;
}
```

Ahora, **reemplace** su carrusel simple con esto:

```html
<amp-carousel layout="fixed-height" height="250" type="carousel" >
    <amp-img src="blocky-mountains-1.jpg" width="300" height="250"></amp-img>

    <amp-ad width="300" height="250"
      type="doubleclick"
      data-slot="/35096353/amptesting/image/static">
        <div placeholder>This ad is still loading.</div>
    </amp-ad>

    <amp-fit-text width="300" height="250" layout="fixed">
        Big, bold article quote goes here.
    </amp-fit-text>
</amp-carousel>
```

**Actualice** la página y debería ver algo como esto:

{{image ('/ static / img / docs / tutorials / tut-advanced-carousel-complex.gif', 412, 403, align = 'center half', caption = 'Un carrusel de contenido mixto')}}

Para obtener más información, consulte la documentación de referencia del componente [`amp-carousel`](../../../../documentation/components/reference/amp-carousel.md) .

[tip type="note"] **NOTE –**  In our last example you may have noticed the [`amp-ad`](../../../../documentation/components/reference/amp-ad.md) component included a child `div` element with the `placeholder` attribute. Earlier in the tutorial, we encountered a similar scenario with [`amp-ad`](../../../../documentation/components/reference/amp-ad.md) using a `fallback`. What’s the difference between placeholder and fallback? `Fallback` elements appear when the parent element fails to load, i.e. if there was no ad available. `placeholder` elements appear in place of the parent element, while it is loading. In a sense, these elements bookend the loading process of the parent element. You can learn more in [Placeholders & fallbacks](../../../../documentation/guides-and-tutorials/develop/style_and_layout/placeholders.md) guide. [/tip]
