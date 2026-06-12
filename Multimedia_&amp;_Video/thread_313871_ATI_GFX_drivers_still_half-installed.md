---
title: "ATI GFX drivers still half-installed?"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-12-06
My PC came with an onboard ATI card, but I added an nVidia GeForce 6200 Turbocache PCIE card and installed the latest graphics drivers via apt-get. I also recently tried running Envy.
My gfx performance is terrible, I can't play any games or do anything requiring 3D rendering and I have the impression there are sill some ATI drivers partially installed.
To give you an idea, the output from **glxgears -printfps** reads like this:
```

glxgears -printfps
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
2995 frames in 5.1 seconds = 587.775 FPS
2964 frames in 5.1 seconds = 581.804 FPS
2964 frames in 5.1 seconds = 578.133 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```

glxinfo begins like this (note the ATI references)
```

name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float, 
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_ARB_multisample
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6200 TurboCache(TM)/PCI/SSE2/3DNOW!
OpenGL version string: 2.0.2 NVIDIA 87.76
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

```

and my xorg.conf has this

```

Section "Device"
    Identifier     "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Driver         "nvidia"
    BusID           "PCI:1:0:0"
    Option          "RenderAccel"           "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option    "TwinView" "True"
    Option    "TwinViewOrientation" "Clone"
    Option    "SecondMonitorHorizSync" "30-50"
    Option    "SecondMonitorVertRefresh" "60"
    Option    "MetaModes" "1024x768, 1024x768; 800x600, 800x600;"
    Option    "TVStandard" "PAL-B"
    Option    "TVOutFormat" "SVIDEO"
    Option    "ConnectedMonitor" "CRT, TV"
    Option    "TVOverScan" "0.4"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Is there some way of checking what exactly is installed, drivers-wise?
One thing I probably should mention is that I installed the 32-bit version of Ubuntu on  64-bit architecture (it was the CD I had to hand). 
I was thinking about reformatting to try and wipe the traces of the ATI card and starting again with Ubuntu 64-bit. It might be quicker than trying to figure out what's up with the card settings, no?

---

### Post by pickarooney on 2006-12-13
Can anyone tell me how to completely remove ATI drivers? Maybe then I can get the installed nvidia drivers to perform adequately.

---

### Post by cblanquer on 2006-12-13
MAybe with ATI instructions to prepare a new ATI installation ([https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.32.5-inst.html):](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.32.5-inst.html):)

Uninstalling the ATI Linux Proprietary Driver

Un-installing the ATI Linux Proprietary Driver is dependent on the mode of initial installation.
Automatic or Custom Driver Installations

If the ATI Proprietary Linux Driver was installed using either the Automatic or Custom options, then do the following:

   1. Launch the Terminal Application/Window and navigate to the /usr/share/ati folder.
   2. With super user permissions, enter the command "sh ./fglrx-uninstall.sh"

---

