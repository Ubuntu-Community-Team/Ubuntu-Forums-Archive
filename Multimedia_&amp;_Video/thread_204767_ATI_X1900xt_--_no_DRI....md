---
title: "ATI X1900xt -- no DRI..."
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by lir on 2006-06-27
Hey guys,

I've got Dapper installed with all the modules for my ATI card as it seems
but I have no DRI for some reason... I'll post some indications to be more helpful
(I'm trying to play Americas Army but it fails: Xlib:  extension "XFree86-DRI" missing on display ":1.0".)



lsmod | grep fglrx
```

fglrx                 388908  21
agpgart                34888  1 fglrx

```


glxgears -printfps
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
11577 frames in 5.0 seconds = 2308.721 FPS
146077 frames in 5.0 seconds = 29214.201 FPS
260227 frames in 5.0 seconds = 52045.340 FPS

```

glxinfo
```

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string:  Generic
OpenGL version string: 1.2 (2.0.5814 (8.25.18))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

```

dpkg -l *fglrx*
```

un  fglrx-driver                      <none>                            (no description available)
un  xfree86-driver-fglrx              <none>                            (no description available)
ii  xorg-driver-fglrx                 7.0.0-8.25.18+2.6.15.11-2         Video driver for ATI graphics accelerators

```


dpkg -l *lib*dri*
```

ii  libgl1-mesa-dri                   6.5.1-0ubuntu15                   A free implementation of the OpenGL API -- DRI modules
un  xlibmesa-dri                      <none>                            (no description available)

```



xorg.conf
```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "fglrx"
        Option      "no_accel" "no"
        Option      "no_dri" "no"
        Option      "DynamicClocks" "on"
        Option      "mtrr" "on"
        Option      "DesktopSetup" "Single"
        Option      "ScreenOverlap" "0"
        Option      "Capabilities" "0x00000000"
        Option      "CapabilitiesEx" "0x00000000"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "CenterMode" "off"
        Option      "PseudoColorVisuals" "off"
        Option      "Stereo" "off"
        Option      "StereoSyncEnable" "1"
        Option      "FSAAEnable" "no"
        Option      "FSAAScale" "1"
        Option      "FSAADisableGamma" "no"
        Option      "FSAACustomizeMSPos" "no"
        Option      "FSAAMSPosX0" " 0.000000"
        Option      "FSAAMSPosY0" "0.000000"
        Option      "FSAAMSPosX1" "0.000000"
        Option      "FSAAMSPosY1" "0.000000"
        Option      "FSAAMSPosX2" " 0.000000"
        Option      "FSAAMSPosY2" "0.000000"
        Option      "FSAAMSPosX3" "0.000000"
        Option      "FSAAMSPosY3" "0.000000"
        Option      "FSAAMSPosX4" " 0.000000"
        Option      "FSAAMSPosY4" "0.000000"
        Option      "FSAAMSPosX5" "0.000000"
        Option      "FSAAMSPosY5" "0.000000"
        Option      "UseFastTLS" "0"
        Option      "BlockSignalsOnLock" "on"
        Option      "UseInternalAGPGART" "no"
        Option      "ForceGenericCPU" "no"
        Option      "KernelModuleParm" "agplock=0"
        Option      "PowerState" "1"
        BusID           "PCI:5:0:0"

EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. ATI Default Card"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

lscpi | grep ATI
```

0000:05:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7249
0000:05:00.1 Display controller: ATI Technologies Inc: Unknown device 7269

```


cat Xorg.94.log | grep DRI
```

(II) Loading extension XFree86-DRI
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): NoDRI = NO
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete

```




(btw because i logged in through ssh to do these tests remotely i've set
 DISPLAY=:1.0 which could explain the 1:0 display on some results).

If anyone has any clue why DRI isn't working i'll be glad to hear.



Thanks.

---

### Post by whatever on 2006-06-27
are you using Xgl? There is no DRI in Xgl...

---

### Post by lir on 2006-06-27
[QUOTE=whatever]are you using Xgl? There is no DRI in Xgl...[/QUOTE]

I do have XGL installed but I've got it seperated.
I can choose to run my session with xgl and without it, and i've done
those tests when i'm without xgl.

---

