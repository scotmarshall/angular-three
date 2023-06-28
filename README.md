# A Step-by-Step Guide to Installing Three.js with Angular Framework

## Introduction
Three.js is a powerful JavaScript library that allows developers to create and display 3D graphics in web browsers. When combined with the Angular framework, it becomes even more versatile and provides an excellent platform for building interactive and visually stunning web applications. In this guide, we will walk you through the necessary steps to install Three.js and integrate it into an Angular project, enabling you to harness the full potential of 3D graphics in your Angular applications.

## Prerequisites
Before we dive into the installation process, make sure you have the following prerequisites set up:

1. Node.js: Ensure that you have Node.js installed on your system. You can download it from the official website (https://nodejs.org) and follow the installation instructions specific to your operating system.

2. Angular CLI: Install the Angular Command Line Interface (CLI) globally on your system. Open your terminal or command prompt and run the following command:
```
npm install -g @angular/cli
```

Now that you have the prerequisites in place, let's proceed with the installation and integration of Three.js into your Angular project.

## Step 1: Setup a New GitHub Repository
This step is optional. Once complete clone repositoryusing this command:
```
git clone <repository-link>
```

## Step 2: Change Directory
Change into the project directory by running:
```
cd <repository-name>
```

## Step 3: Create a New Angular Project
To start, open your terminal or command prompt and navigate to the directory where you want to create your Angular project. Run the following command to generate a new project using the Angular CLI, omitting `--directory ./` if not using a GitHub repository.:
```
ng new <repository-name> --directory ./
```

Now, install the Three.js package using npm:
```
npm install three
```

## Step 4: Configure TypeScript
Three.js is written in TypeScript, so we need to configure our Angular project to work with it. Using the following command will install the necessary packages:
```
npm install --save-dev @types/three
```
<!-- Three.js is written in TypeScript, so we need to configure our Angular project to work with it. Open the `tsconfig.json` file located in the root directory of your project and add the following lines under the `"compilerOptions"` section:
```json
"types": [
  "three"
]
``` -->

## Step 5: Import Three.js in Angular Component
Next, we need to import Three.js in a component to utilize its functionalities. For this example, let's assume we want to create a 3D cube. Open the `src/app/app.component.ts` file and import the necessary Three.js modules:
```typescript
import * as THREE from 'three';
```

## Step 6: Use Three.js in Angular Component
After importing Three.js, we can now use its features within our Angular component. Modify the component class as follows:
```typescript
export class AppComponent implements OnInit {
  ngOnInit(): void {
    // Create a scene
    const scene = new THREE.Scene();

    // Create a camera
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    camera.position.z = 5;

    // Create a renderer
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(renderer.domElement);

    // Create a cube
    const geometry = new THREE.BoxGeometry();
    const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
    const cube = new THREE.Mesh(geometry, material);
    scene.add(cube);

    // Animate the cube
    function animate() {
      requestAnimationFrame(animate);

      cube.rotation.x += 0.01;
      cube.rotation.y += 0.01;
      
      renderer.render(scene, camera);
    }

    animate();
  }
}
```

*** Remember to import the `OnInit` package! ***

## Step 7: Update Angular Component Template
Now that we have the Three.js logic in place, let's update the component template to render the 3D scene. Open the `src/app/app.component.html` file and replace its content with the following:
```html
<div style="text-align: center;">
  <h1>Welcome to my Three.js Angular App!</h1>
</div>
```

## Step 8: Additional Styling
To remove unwanted borders and margins while ensuring HTML elements are displayed correctly. Open the `src/styles.css` file and replace its content with the following:
```css
@import url('https://fonts.googleapis.com/css2?family=Agdasima&display=swap');

body {
    margin: 0;
    background-color: #ffdca8;
    font-size: 24px;
    font-family: 'Agdasima', sans-serif;
    text-shadow: 2px 2px #000000;
}

canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
}

#insideTitle {
    text-align: center;
    color: white;
}
```

## Step 9: Run the Application
Finally, it's time to run our Angular application and see the Three.js magic in action. In the terminal or command prompt, run the following command:
```
ng serve --open
```

Open your web browser and navigate to `http://localhost:4200`. You should see the text "Welcome to my Three.js Angular App!" displayed along with a rotating 3D cube.

## Conclusion:
In this guide, we have walked through the step-by-step process of installing Three.js and integrating it into an Angular project. By following these instructions, you now have the necessary setup to create and display stunning 3D graphics within your Angular applications. Feel free to explore the vast capabilities of Three.js and unleash your creativity in building immersive and interactive web experiences. Happy coding!