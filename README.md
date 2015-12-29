# whs.preload
Preloading plugin for WhitestormJS


### Usage

Include `preloader.start({Your WHS init object here});` after your `WHS.init` object. After you declared all other WHS objects put `preloader.end();`

```javascript

var preloader = Preloader();

var GAME = new WHS.init(
{
    anaglyph: false,
    helper: true,
    stats: "fps", // fps, ms, mb
    wagner: WAGNER,
    autoresize: true,
    gravity: {
        x: 0,
        y: -200,
        z: 0
    },
    camera: {
        far: 10000,
        y: 10,
        z: 30
    }
});

preloader.start(GAME);

GAME.cube = GAME.addObject("cube",
{
    geometryOptions: {
        width: 10,
        height: 6,
        depth: 1
    },
    mass: 10,
    onlyvis: false,
    materialOptions: {
        vertexColors: THREE.VertexColors,
        shading: THREE.SmoothShading,
        map: api.texture('../assets/textures/backgrounddetailed6.jpg'),
        type: "phong"
    },
    pos: {
        x: 0,
        y: 100,
        z: 0
    },
    rot: {
        x: 45,
        y: 0,
        z: 0
    }
});

GAME.ground = GAME.addGround("smooth",
{
    width: 250,
    height: 250
},
{
        //color: 0x000000,
        vertexColors: THREE.VertexColors,
        shading: THREE.SmoothShading,
        map: api.texture('../textures/grasslight-big.jpg'),
        type: "basic"
},
{
    x: 0,
    y: 0,
    z: 0
});

GAME.light = GAME.addLight("directional", { color: 0xffffff, //0x00ff00,
                                              intensity: 8},
{
    x: 0,
    y: 1,
    z: 3
},
{
    x: 0,
    y: 0,
    z: 0
});

GAME.OrbitControls();

preloader.end();

```
