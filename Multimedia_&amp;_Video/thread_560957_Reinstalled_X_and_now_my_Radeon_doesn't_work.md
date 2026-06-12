---
title: "Reinstalled X and now my Radeon doesn't work"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by hoborocket on 2007-09-27
[http://ubuntuforums.org/showthread.php?t=560817](http://ubuntuforums.org/showthread.php?t=560817)

I had to reinstall X and now every time I follow the regular instructions to install fglrx, it just breaks X. No screen found error and I have to restore a backed up xorg.conf. Somebody else did my driver installation last time so I have no idea WHAT they installed. Nothing even relating to ATI appears in my restricted drivers manager.

Relevant lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 LX [Mobility FireGL 7800 M7]

Current xorg.conf (that works): [http://extraball.sunsite.dk/notepad.php?ID=482387](http://extraball.sunsite.dk/notepad.php?ID=482387)

Edit: Minor addition question, but a lot of my text is really frigging big now, is this an X thing or what?

New edit: Tried Envy, same error. To repeat, IT DID WORK BEFORE, so there's a driver for it. I just have no idea what it is x.x

Edit the third: changed the driver in xorg.conf to radeon, and still nothing. It didn't break it though.

---

### Post by hoborocket on 2007-09-27
Bump. Nobody on IRC knows either.

---

### Post by w4ett on 2007-09-27
Your card is not supported by the restricted drivers, but is supported by the xorg-driver-ati:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

To get your driver running properly:
```

sudo apt-get remove fglrx
```

Then  reconfigure your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"] "ati"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

---

### Post by hoborocket on 2007-09-27
Well, I did that, and it didn't break anything, but I still can't use desktop effects or beryl. x.x

---

### Post by w4ett on 2007-09-27
What framerate do you get from the command:

```
glxgears
```

---

### Post by w4ett on 2007-09-27
I have a favorite tutorial for Compiz-Fusion (Beryl is unsupported now since the two projects have merged---hence Fusion):

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

Follow the tutorial, leaving out the sections regarding Envy and the Nvidia driver (not needed for your install) and you should be good to go.

---

### Post by hoborocket on 2007-09-27
My issues with fusion are many and old, suffice to say it has never worked for me and Beryl is fine.

The issue is, Beryl USED to work, as did basic desktop effects. Neither will run now. Effects gives me a "cannot run" error and Beryl crashes and dumps me to Metacity. Those packages have not been altered or updated, so I believe this to be a driver issue.

glxgears:
5351 frames in 5.2 seconds = 1032.270 FPS

It looked very choppy.

---

### Post by w4ett on 2007-09-27
About the last advice I can give you is to hold fire and see if Gusty will help you with the integration of the stable release of compiz-fusion.  I am running an RV280/ATI 9200 SE 64 MB card on this test machine and I have full use of Compiz, to include the  cube, fire and rain effects.  Pretty impressive for such an old card.  

I never could get Beryl to run on this card, but in Gutsy, the automatic configuration of xorg and setup of Compiz-Fusion fusion was effortless.

---

### Post by dmf86 on 2007-10-04
> **w4ett said:**
> About the last advice I can give you is to hold fire and see if Gusty will help you with the integration of the stable release of compiz-fusion.  I am running an RV280/ATI 9200 SE 64 MB card on this test machine and I have full use of Compiz, to include the  cube, fire and rain effects.  Pretty impressive for such an old card.  

I never could get Beryl to run on this card, but in Gutsy, the automatic configuration of xorg and setup of Compiz-Fusion fusion was effortless.

Do you have 3D rendering? If so, how? :)

---

### Post by w4ett on 2007-10-04
I had 3D rendering in Feisty and used only the native Desktop Effects....Google Earth worked without a hitch.  I did nothing special to achieve these results, I just let the default settings as they were and enabled the DEffects by tic'ing the box.

In Gutsy it was seamless.....the new xorg reconfigured my xorg.conf....As I said before, I use Compiz-Fusion, and Kiba-dock.  I'm not a gamer, but I'm sure the 3d capability would not be enough  to 'recreate', but I'm quite satisfied with the drivers as they are.

Follows are my xorg.conf, glxgears and glxinfo:

> w4ett@w4ett-desktop:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "int10"
        Load            "vbe"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "ati"
        Screen  0
        Option          "MergedFB"      "off"
EndSection

Section "Monitor"
        Identifier      "DELL E773c"
        Vendorname      "Dell"
        Modelname       "Dell E773c"
        Horizsync       30.0-70.0
        Vertrefresh     50.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Monitor         "DELL E773c"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1400    1050
                Modes           "800x600@85"    "800x600@60"    "800x600@75"   "832x624@75"     "800x600@72"    "1024x768@85"   "800x600@56"    "1024x768@75"  "640x480@85"     "1024x768@70"   "640x480@75"    "1024x768@60"   "640x480@72"   "1024x768@43"    "640x480@60"    "1152x864@75"   "1280x960@60"   "1280x1024@60" "1400x1050@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "ati"
        Screen  1
        Option          "MergedFB"      "off"
EndSection
Section "screen" # 
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
EndSection
Section "monitor" # 
        Identifier      "monitor1"
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection
w4ett@w4ett-desktop:~$ 

> w4ett@w4ett-desktop:~$ glxgears
3523 frames in 5.0 seconds = 704.572 FPS
3573 frames in 5.0 seconds = 714.560 FPS
3264 frames in 5.0 seconds = 652.473 FPS
3642 frames in 5.0 seconds = 728.316 FPS
3600 frames in 5.0 seconds = 719.886 FPS
3101 frames in 5.0 seconds = 620.083 FPS
w4ett@w4ett-desktop:~$ 



> w4ett@w4ett-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 8x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x6e 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
w4ett@w4ett-desktop:~$ 


---

### Post by dmf86 on 2007-10-04
> **w4ett said:**
> I had 3D rendering in Feisty and used only the native Desktop Effects....Google Earth worked without a hitch.  I did nothing special to achieve these results, I just let the default settings as they were and enabled the DEffects by tic'ing the box.

In Gutsy it was seamless.....the new xorg reconfigured my xorg.conf....As I said before, I use Compiz-Fusion, and Kiba-dock.  I'm not a gamer, but I'm sure the 3d capability would not be enough  to 'recreate', but I'm quite satisfied with the drivers as they are.

Follows are my xorg.conf, glxgears and glxinfo:

Hum, you're using the "ati" driver, if i use that one i get only artifacts ands glitches... :( I'm stuck at "vesa".

---

