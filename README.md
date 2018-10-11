# ES6 - Overview

ECMAScript (ES) is a scripting language specification standardized by ECMAScript International.

ECMAScript 6 is also known as `ES6` or `ECMAScript 2015`

Current browsers don’t support all the new ES6 features yet [(see comptability table)](http://kangax.github.io/compat-table/es6/). You need to use a compiler (transpiler) to transform your `ES6` code to `ES5` compatible code. `Babel` has become the standard to compile ES6 applications. `Babel` can also compile other versions of `ECMAScript` as well as `React’s JSX`.

Now we are going to set up a development environment to develop and run an ES6 application using Babel.

### Step 1: Set Up Babel

we set up `Babel` so that we can start using ECMAScript 6 features.

- Open a command prompt, and navigate to the `ES6` directory.
- Type the following command to create a `package.json` file:

```
npm init
```
Press the `Enter` or `Return` key in response to all the questions to accept the default values.

- Type the following command to install the babel-cli and babel-core modules:

```
npm install babel-cli babel-core --save-dev
```

- Type the following command to install the `ECMAScript 2015 preset`:

```
npm install babel-preset-es2015 --save-dev
```

*In Babel 6, every transformer is a plugin that can be installed separately. A preset is a group of related plugins. Using a preset, you don’t have to install and update dozens of plugins individually.
*

- Install [http-server](https://github.com/indexzero/http-server) in your project. `http-server` is a lightweight web server we use to run the application locally during development.

```
npm install http-server --save-dev
```

- Open `package.json` in your favorite code editor. In the scripts section, remove the **test** script, and add two new scripts: a script named `babel` that compiles our `.js` files to a version of ECMAScript that can run in current browsers, and a script named `start` that starts the local web server. The scripts section should now look like this:

```js
"scripts": {
    "babel": "babel --presets es2015 js/main.js -o build/main.bundle.js",
    "start": "http-server"
},
```

If port `8080` is already in use on your computer, modify the start script in `package.json` and specify a port that is available on your computer. 

For example:

```js
"scripts": {
    "babel": "babel --presets es2015 js/main.js -o build/main.bundle.js",
    "start": "http-server -p 9009"
},
```

- In the `ES6` directory, create a `build` folder to host the compiled version of the application.

### Step 2: Build and Run

- On the command line, make sure you are in the `ES6` directory, and type the following command to run the babel script and compile all your `.js` files.

```
npm run babel
```

- Open `index.html` in your code editor, and add the `<script>` tag as `build/bundle.js` to load the compiled version of `js/main.js`:

```html
<script src="build/bundle.js"></script>
```

- Open a new command prompt. Navigate to the `ES6` directory, and type the following command to start `http-server`.

```
npm start
```

- Open a browser and access `http://localhost:9009`
- Open `build/bundle.js` in your code editor and notice that the generated code is virtually identical to the source code `js/main.js`

Sample folder structure is

![image](https://user-images.githubusercontent.com/6780840/46797075-d0054080-cd6b-11e8-9483-9e58b25d7eb7.png)
