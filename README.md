# Learning Angular

Learning Angular - A Full Angular Application Template Fully Configured with Material Design Components installed

Hello Boot Campers, I hope everyone is doing well. After scouring 100 of jobs, I noticed that our new found learning of React.js would be more useful if it was replaced with Angular.js. 

So in an effort to learn and teach myself the framework, I thought it would be pretty cool if I shared my knowledge along the way. 

Guys and Gals.. guess what? It's not that hard. I have created and documented all the steps below for you to create your very first Angular Single Page Application. If you want to have an api back end running on a node express 4 app then all you do is put this code in the client folder just like you did with your React apps.

If you clone this repo you will have everything you need to get started except for the Angular CLI which you will need to download and install. 

## Don't Worry

I'm going to go step by step in that process of creating this skeleton app, everything from beginning to end.

First here are a list of recourses to help if you want more information they are here for convenience.
 
[Angular Official Site](https://angular.io/)

[Angular Material (Material Design components for Angular)](https://material.angular.io/)

## Begin

- Step 1: Okay the first thing to do is to install Angular CLI, this will install the 'ng' command globally so you can use it anywhere :

(Hint: I have only tested these commands to work on a Windows PC using git bash.) 

bash
```
$ npm install -g @angular/cli
```

- Step 2: Next, let's make a new workspace (Kinda similar to create-react-app)

(Hint: cd into a directory where you keep all your code, this will make a new folder with the name of learning-angular.)

(Hint: 'ng' is the name of the command you run to access the Angular CLI (Similar to using node) 

bash
```
$ ng new learning-angular
```

- Step 3: cd into learning-angular and test the app

bash
```
$ cd learning-angular
$ ng serve --open
```

## TADA! That was it. Now we are going to add Material Design Components, animations and icons 

Stop your server- let's go ahead and press 'ctrl-c' to stop the Angular server and continue to add to our template

- Step 1: make sure you are in the learning-angular folder. Then go ahead and open this folder in VSCode. We will be changing some of the code in a couple of the files. Plus you need to take a look at the app structure because it is different from React in this aspect.
- Step 1b. Install Material Design Components

bash
```
$ npm install --save @angular/material @angular/cdk @angular/animations
```

The above line installs three things (More on what they do later):
- '@angular/material'
- '@angular/cdk'
- '@angular/animations'

- Step 2: Configure animations

Open the learning-angular/src/app/app.module.ts file and paste the code below

javascript
```
// paste this below the import { AppComponent } from './app.component' line
import {BrowserAnimationsModule} from '@angular/platform-browser/animations';


// Next add 'BrowserAnimationsModule' to your imports by making your @NgModule Imports look like this:

  //...
  imports: [
		BrowserModule,
		BrowserAnimationsModule
		],
	//	...


```


- Step 3: Import the component modules


in the same file from above learning-angular/src/app/app.module.ts, paste the code below

javascript
```
// paste these imports below the animations imports you just did from above 

import {MatButtonModule} from '@angular/material/button';
import {MatCheckboxModule} from '@angular/material/checkbox';


// Next add 'MatButtonModule' and 'MatCheckboxModule' to your imports by making your @NgModule Imports look like this:

  //...
  imports: [
		BrowserModule,
		BrowserAnimationsModule,
		MatButtonModule,
		MatCheckboxModule
		],
	//	...


```

Basically you should end up with a file that looks like this:

javascript
```
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
import { MatButtonModule } from '@angular/material/button';
import { MatCheckboxModule } from '@angular/material/checkbox';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    BrowserAnimationsModule,
    MatButtonModule,
    MatCheckboxModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```


- Step 4: Include a theme

Including a theme is required to apply all of the core and theme styles to your application.

To get started with a prebuilt theme, include one of Angular Material's prebuilt themes globally in your application. add this to your learning-angular/src/styles.css file :

css
```
@import "~@angular/material/prebuilt-themes/indigo-pink.css";
```

Step 5: Gesture Support
Some components (mat-slide-toggle, mat-slider, matTooltip) rely on HammerJS for gestures. In order to get the full feature-set of these components, HammerJS must be loaded into the application.

to do this install hammerjs 

bash
```
$ npm install --save hammerjs
```

Then add the import in your learning-angular/src/main.ts file so that your file looks like this

javascript
```
import { enableProdMode } from '@angular/core';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app/app.module';
import { environment } from './environments/environment';
import 'hammerjs';

if (environment.production) {
  enableProdMode();
}

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
```

Then last but not least add the meterial Icons to the index.html file in the learning-angular/src/ folder so that your file looks like this:

html
```
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>LearningAngular</title>
  <base href="/">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
</head>
<body>
  <app-root></app-root>
</body>
</html>
```


