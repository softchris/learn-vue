We explored how you can display data on a page through the use of handlebars (`{{}}`). However text on the page is not the only part we may need to make dynamic. A large part of the values we set on a page are done through attributes. Fortunately, Vue.js allows you to bind to attributes through directives.

## Directives

Directives are attributes recognized by Vue.js, and allow you to dynamically set the values of HTML attributes. All directives start with `v-`.

## v-bind

The core directive is `v-bind`, which allows you to bind a data value to an attribute. This could be used to dynamically set the name of a class, the source for an image, or a style.

To use `v-bind`, you place it in front of the attribute you wish to set with a `:`. So to set the `src` attribute for an image you would use `v-bind:src="value"`. The attribute value is then evaluated much in the same way as you would use `{{ }}`.

The following code would generate the HTML element `<img src="./media/sample.jpg">`

```html
<div id="app">
    <img v-bind:src="imageSource" />
</div>

<script src="https://unpkg.com/vue@next"></script>
<script>
    Vue.createApp({
        data() {
            return {
                imageSource: './media/sample.jpg'
            }
        }
    }).mount('app');
</script>
```

> ![NOTE]
> We do not have to maintain a reference to the object we use for our app, but can call `createApp` immediately followed by `mount` as demonstrated above.

## Class and style

One of the most common attributes you may wish to set for an HTML element is its `class` or `style`. To support this, Vue.js includes a shortcut available for these two attributes. `:class` and `:style` are identical to using `v-bind:class` and `v-bind:style` respectively.

Both class and style support object syntax, allowing you to represent more complex or dynamic style by creating JavaScript objects.

### Class objects

Let's say we have an application with two classes - `centered` and `active`. Using HTML we can enable these attributes by using the following HTML:

```html
<div class='centered active'>Hello, Vue!</div>
```

We could represent this with a class object and binding in Vue by using the following:

```html
<div id="app">
    <div :class="classObject">Hello, Vue!</div>
</div>

<script src="https://unpkg.com/vue@next"></script>
<script>
    Vue.createApp({
        data() {
            return {
                classObject: {
                    centered: true,
                    active: true
                }
            }
        }
    }).mount('app');
</script>
```

The boolean values allow us to enable or disable specific classes. Setting `centered` to `false` would render `<div class="active">`.

> ![NOTE]
> When creating a class object, JavaScript naming rules apply. If you have a class name which uses a dash, such as `center-text`, you will have to place the name in quotes (`'center-text': true`) when adding the property.

### Style objects

Setting styles in CSS involves creating different collections of key/value pairs. This is relatively natural to represent with a JavaScript object. We can create objects which Vue.js can use to set style through style objects.

If we wanted to set the background color (`background-color`) of an HTML element's style, we could do this with the following:

```html
<div id="app">
    <div :style="styleObject">Hello, Vue!</div>
</div>

<script src="https://unpkg.com/vue@next"></script>
<script>
    Vue.createApp({
        data() {
            return {
                styleObject: {
                    'background-color': 'red'
                }
            }
        }
    }).mount('app');
</script>
```
