*💉*SerumJS💉** is a lightweight dependency injection module written in es6, inspired by Krasimir Tsonev's blog post http://krasimirtsonev.com/blog/article/Dependency-injection-in-JavaScript

## Usage

Using SerumJS is very straightforward. Write your services and register live instances with Resolver:
```JavaScript
   import Resolver, { Service } from 'serumjs'
   
   class DeliveryService {
     deliver(item, address) {
       ....
     }
   }

   Resolver.register(new DeliveryService()) //<-- note the "new" keyword
```

Then inject your dependencies by inheriting the `Service` class like so:
```JavaScript
   import ShoppingCard extends Service {
     constructor() {
      super('DeliveryService')
     }

     checkOut() {
      this.DeliveryService.delivery('🍪🍪🍪🍪', 'My home address')
     }
   }
```

Alternatively, you may also inject dependencies in functions using `Resolver.resolve`:
```JavaScript
   const doSomething = Resolver.resolve(['DeliveryService'], function(additionalParams) {
    this.DeliveryService.deliver('🎮', 'My work address')
    console.log(additionalParams)
   })

   doSomething(42)
```

That's it!

## Motivation

This library can be used in es5 and ES6 projects

## Installation

Install with `npm install serumjs --save` or `yarn add serumjs`

## API Reference

The Resolver is a singleton that provides `get`, `getAll`, `register`, and `resolve` functions.
Check out the `./examples` folder for more examples on how to use the `Resolver` in various scenarios.

## Contributors

Created and maintained by Novium
- Nicholas Credli [credli](https://github.com/credli).
- Jamal Mheidly [jmheidly](https://github.com/jmheidly).

## License

Copyright (c) 2011-2017 Novium SARL

MIT License

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.