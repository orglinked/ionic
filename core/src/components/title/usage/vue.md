```html
<template>
  <!-- Default title -->
  <ion-toolbar>
    <ion-title>Default Title</ion-title>
  </ion-toolbar>

  <!-- Small title -->
  <ion-toolbar>
    <ion-title size="small">Small Title above a Default Title</ion-title>
  </ion-toolbar>
  <ion-toolbar>
    <ion-title>Default Title</ion-title>
  </ion-toolbar>

  <!-- Large title -->
  <ion-toolbar>
    <ion-title size="large">Large Title</ion-title>
  </ion-toolbar>
</template>
```

### Collapsible Large Titles

Ionic provides a way to create the collapsible titles that exist on stock iOS apps. Getting this setup requires configuring your `ion-title`, `ion-header`, and (optionally) `ion-buttons` elements.

```html
<template>
  <ion-header translucent="true">
    <ion-toolbar>
      <ion-title>Settings</ion-title>
    </ion-toolbar>
  </ion-header>

  <ion-content fullscreen="true">
    <ion-header collapse="condense">
      <ion-toolbar>
        <ion-title size="large">Settings</ion-title>
      </ion-toolbar>
      <ion-toolbar>
        <ion-searchbar></ion-searchbar>
      </ion-toolbar>
    </ion-header>

    ...

  </ion-content>
</template>
```

In the example above, notice there are two `ion-header` elements. The first `ion-header` represents the "collapsed" state of your collapsible header, and the second `ion-header` represents the "expanded" state of your collapsible header. Notice that the second `ion-header` must have `collapse="condense"` and must exist within `ion-content`. Additionally, in order to get the large title styling, `ion-title` must have `size="large"`.

```html
<template>
  <ion-header translucent="true">
    <ion-toolbar>
      <ion-buttons collapse="true" slot="end">
        <ion-button>Click Me</ion-button>
      </ion-buttons>
      <ion-title>Settings</ion-title>
    </ion-toolbar>
  </ion-header>

  <ion-content fullscreen="true">
    <ion-header collapse="condense">
      <ion-toolbar>
        <ion-buttons collapse="true" slot="end">
          <ion-button>Click Me</ion-button>
        </ion-buttons>
        <ion-title size="large">Settings</ion-title>
      </ion-toolbar>
      <ion-toolbar>
        <ion-searchbar></ion-searchbar>
      </ion-toolbar>
    </ion-header>

    ...

  </ion-content>
</template>
```

In this example, notice that we have added two sets of `ion-buttons` both with `collapse` set to `true`. When the secondary header collapses, the buttons in the secondary header will hide, and the buttons in the primary header will show. This is useful for ensuring that your header buttons always appear next to an `ion-title` element.

`ion-buttons` elements that do not have `collapse` set will always be visible, regardless of collapsed state. When using the large title and `ion-buttons` elements inside of `ion-content`, the `ion-buttons` elements should always be placed in the `end` slot.

When styling the large title, you should target the large title globally as opposed to within the context of a particular page or tab, otherwise its styles will not be applied during the navigation animation.

```css
ion-title.large-title {
  color: purple;
  font-size: 30px;
}
```

> When using collapsible large titles, it is required that `fullscreen` is set to `true` on `ion-content` and `translucent` is set to `true` on the main `ion-header`.