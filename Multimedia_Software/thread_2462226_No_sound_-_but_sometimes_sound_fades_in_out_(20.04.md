---
title: "No sound - but sometimes sound fades in/ out (20.04.2)"
date: 2021-05-16
forum: Multimedia Software
---

### Post by ntopas on 2021-05-16
I tried more than 10 different solutions, with no results.

Today I also tried a clean install of Ubuntu 20.04.2, but the problem persists.

today i only tried ```
sudo apt-get remove timidity
``` and i also updated the AMD drivers via (ppa:oibaf/graphics-drivers)



 My ALSA information is located at  

 [URL="http://alsa-project.org/db/?f=0e7b9d5abf7645382cf07c263650683f7fb49c70"]http://alsa-project.org/db/?f=0e7b9d5abf7645382cf07c263650683f7fb49c70


[/URL]

  ```

glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: AMD CARRIZO (DRM 3.38.0, 5.8.0-53-generic, LLVM 12.0.0) (0x9874)
    Version: 21.2.0
    Accelerated: yes
    Video memory: 512MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 37 MB, largest block: 37 MB
    VBO free aux. memory - total: 2713 MB, largest block: 2713 MB
    Texture free memory - total: 37 MB, largest block: 37 MB
    Texture free aux. memory - total: 2713 MB, largest block: 2713 MB
    Renderbuffer free memory - total: 37 MB, largest block: 37 MB
    Renderbuffer free aux. memory - total: 2713 MB, largest block: 2713 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 512 MB
    Total available memory: 3584 MB
    Currently available dedicated video memory: 37 MB
OpenGL vendor string: AMD
OpenGL renderer string: AMD CARRIZO (DRM 3.38.0, 5.8.0-53-generic, LLVM 12.0.0)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 21.2.0-devel (git-6fcf331 2021-05-16 focal-oibaf-ppa)
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6 (Compatibility Profile) Mesa 21.2.0-devel (git-6fcf331 2021-05-16 focal-oibaf-ppa)
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 21.2.0-devel (git-6fcf331 2021-05-16 focal-oibaf-ppa)
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```

---

