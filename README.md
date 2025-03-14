# tadva

Tahoma2D and OpenToonz allows creating your own effects using GLSL.
Shaders is just one part of VFX OpenToonz/Tahoma2D. There is actually a pipline:  
![](RenderingPipeline.png?raw=true)

You'll be working with either .vert (Vertex Shaders) or .frag (Fragment Shaders).


A few things to remember:  
There are 3 main coordinate spaces to work wtih. World, Output, and Input.
* World Space - The entire canvas you'll be working with.
* Input Space - The space area of your input images.
* Output Space - The area the effects are created on as an output.

worldToOutput converts coordinates from the world space to output space, such as when you want to do a blur radius from world units to pixels. outputToInput converts coordnates from outpsace space to input space, such as when sampling the source image. ouputToWorld converts coordinates from output space back to world space, useful for when you need to compare effect coordinates with world-space parameters.

Verbose how to install information as well as extra documentation is available in the other readme.txt file.

```
WARNING: Toonz requires that *output* colors must be 
         'premultiplied' - that is, common RGB components
         (in the range [0, 1]) must be stored multiplied
         by their alpha component.
```

OpenToonz and Tahoma2D can use anything already provided by GLSL such as sin(). The ONLY thigs predefined by T2D/OT for GLSL shaders are:
* uniform mat3 worldToOutput.
* uniform mat3 outputToWorld.
* uniform vec4 outputRect.
* varying vec4 inputRect[ports].
* varying vec4 worldToInput[ports].
* unform Sampler2D inputImage[n].
* uniform mat3 outputToInput[n].
* uniform mat3 inputToOutput[n].
* uniform float time.
* uniform float frame.
* uniform vec2 inputSize.
* uniform vec2 pixelSize.
* uniform vec2 outputSize.

There are no additional extra functions provided by OT/T2D. You'll have to write them yourself.
