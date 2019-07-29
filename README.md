# ngx-currency - Decimal point variation

P.S. This fork of the projects makes the user input the decimal point manually. Credit goes to original creator.

[![GitHub issues](https://img.shields.io/github/issues/pawlufelice/ngx-currency.png)](https://github.com/pawlufelice/ngx-currency/issues)
[![GitHub stars](https://img.shields.io/github/stars/pawlufelice/ngx-currency.png)](https://github.com/pawlufelice/ngx-currency/stargazers)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.png)](https://raw.githubusercontent.com/pawlufelice/ngx-currency/master/LICENSE)

## Demo

https://pawlufelice.github.io/ngx-currency/

## Table of contents

- [About](#about)
- [Installation](#installation)
- [Documentation](https://pawlufelice.github.io/ngx-currency/docs/)
- [Development](#development)
- [License](#license)

## About

## Getting Started

### Installing and Importing

Install the package by command:

```sh
    npm install ngx-currency --save
```

Import the module

```ts
import { NgxCurrencyModule } from "ngx-currency";

@NgModule({
    imports: [
        ...
        NgxCurrencyModule
    ],
    declarations: [...],
    providers: [...]
})
export class AppModule {}
```

### Using 

```html
    <input currencyMask formControlName="value" />
```

 * `ngModel` An attribute of type number. If is displayed `'$ 25.63'`, the attribute will be `'25.63'`.

### Options 

You can set options...

```html
    <!-- example for pt-BR money -->
    <input currencyMask formControlName="value" [options]="{ prefix: 'R$ ', thousands: '.', decimal: ',' }"/>
```  

Available options: 

 * `align` - Text alignment in input. (default: `right`)
 * `allowNegative` - If `true` can input negative values.  (default: `true`)
 * `decimal` -  Separator of decimals (default: `'.'`)
 * `precision` - Number of decimal places (default: `2`)
 * `prefix` - Money prefix (default: `'$ '`)
 * `suffix` - Money suffix (default: `''`)
 * `thousands` - Separator of thousands (default: `','`)
 * `nullable` - when true, the value of the clean field will be `null`, when false the value will be `0`

You can also set options globally...

```ts
import { NgxCurrencyModule } from "ngx-currency";

export const customCurrencyMaskConfig = {
    align: "right",
    allowNegative: true,
    allowZero: true,
    decimal: ",",
    precision: 2,
    prefix: "R$ ",
    suffix: "",
    thousands: ".",
    nullable: true
};

@NgModule({
    imports: [
        ...
        NgxCurrencyModule.forRoot(customCurrencyMaskConfig)
    ],
    declarations: [...],
    providers: [...],
    bootstrap: [AppComponent]
})
export class AppModule {}
```

## Quick fixes

### Ionic 2-3

Input not working on mobile keyboard

```html
<!-- Change the type to 'tel' -->
    <input currencyMask type="tel" formControlName="value" />
```

Input focus get hide by the mobile keyboard

on HTML
```html
<!-- Change the type to 'tel' -->
    <input currencyMask type="tel" formControlName="value" [id]="'yourInputId' + index" (focus)="scrollTo(index)" />
```

on .ts
```ts
import { Content } from 'ionic-angular';

export class...

    @ViewChild(Content) content: Content;
  
    scrollTo(index) {
        let yOffset = document.getElementById('yourInputId' + index).offsetTop;
        this.content.scrollTo(0, yOffset + 20);
    }
```

## Development

### Prepare your environment
* Install [Node.js](http://nodejs.org/) and NPM
* Install local dev dependencies: `npm install` while current directory is this repo

### Development server
Run `npm start` or `npm run demo` to start a development server on port 8000 with auto reload + tests.

### Testing
Run `npm test` to run tests once or `npm run test:watch` to continually run tests.

## License

MIT @ Neri Bez Fontana
