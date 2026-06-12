---
title: "Direct Rendering on ATI Rage Mobility P/M AGP 2x"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by Old Pink on 2007-07-22
Hi,

[http://ubuntuforums.org/showthread.php?t=504558](http://ubuntuforums.org/showthread.php?t=504558)

**PLEASE **help me get this sorted, seems to be beyond the intelligence level of the beginner room. Nothing about this on the ATI site. Only few seem to have got it working. It's borked up my glxinfo, which now just crashes. 

$10 via PayPal goes to the person who fixes my glxinfo and gets direct rendering working with a decent ATI driver.

Matt

---

### Post by dougfractal on 2007-07-22
Hi Matt
 I hope to help you out. I've just helped  moallen; [http://ubuntuforums.org/showthread.php?t=505453](http://ubuntuforums.org/showthread.php?t=505453)
I need to know more about your laptop, ie what is it?
and  can you send "cat /var/log/Xorg.0.log" in quote.

Doug

---

### Post by kjander on 2007-07-22
Yes im experiencing the same frustration. glxinfo hasnt gone as badly as Old Pink's but still, cant get any current info on getting direct rendering working, on my Dell Inspiron 7000 with the ati rage mobility LE. since the 2 cards use similar chipsets i was hoping any info that would help old pink would help me as well

---

### Post by dougfractal on 2007-07-22
So am I right is saying 
X is fine.
Direct rendering: No

and you want an opengl desktop?

You've got 1024x764 screen and 8mb video ram?

---

### Post by kjander on 2007-07-22
Thats correct. sounds simple, no?
> 
kristoffer@kristoffer-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
00:04.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


> 
kristoffer@kristoffer-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
kristoffer@kristoffer-laptop:~$ 


---

### Post by dougfractal on 2007-07-22
do this we are going to use the radeon driver and not ati or flgrx 

```

sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.ati
```

/etc/X11/xorg.conf
```
Section "ServerLayout"
        Identifier     "Default Layout"
        Option          "AIGLX"         "true"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Synaptics" "AlwaysCore"
EndSection

Section "Files"
        RgbPath      "/usr/X11R6/lib/X11/rgb"
        FontPath     "unix/:7100"
EndSection

Section "Module"
        Load  "dbe"
        Load  "extmod"
        Load  "fbdevhw"
        Load  "glx"
        Load  "record"
        Load  "freetype"
        Load  "type1"
        Load  "synaptics"
        Load  "dri"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "gb"
EndSection


Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "IMPS/2"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "yes"
EndSection
Section "InputDevice"
        Identifier  "Synaptics"
        Driver      "synaptics"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "auto-dev"
        Option      "Emulate3Buttons" "yes"
        Option      "SHMconfig" "on"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "LCD Panel 1024x768"
        HorizSync    31.5 - 90.0
        VertRefresh  60.0 - 60.0
        Option      "dpms"
EndSection

Section "Device"
      	Identifier  "Videocard0"     # ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)
     	Driver "radeon"
	boardname "ATI Radeon"
	vendorname "ATI"
	option "MergedFB" "off"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "true"
	Option "EnablePageFlip" "True"
	Option "UseInternalAGPGART" "no"
	Option "backingstore" "true"
	Option "AllowGLXWithComposite" "true"
	Option "RenderAccel" "true"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
	Viewport   0 0
        Depth     24
        Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Group        0
        Mode         0666
EndSection

```

install
```
sudo apt-get install beryl beryl-manager
```

post the output of
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

```
beryl
```

---

### Post by Old Pink on 2007-07-22
> **dougfractal said:**
> Hi Matt
 I hope to help you out. I've just helped  moallen; [http://ubuntuforums.org/showthread.php?t=505453](http://ubuntuforums.org/showthread.php?t=505453)
I need to know more about your laptop, ie what is it?
and  can you send "cat /var/log/Xorg.0.log" in quote.

Doug

cat /var/log/Xorg.0.log:
> 
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux matt-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 22 14:15:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc Rage Mobility P/M AGP 2x"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/X11R6/lib/X11/fonts/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/X11R6/lib/X11/fonts/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.1
    X.Org XInput driver : 0.7
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7190 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,80,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 03 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 1013,6005 card 1028,00dc rev 01 class 04,01,00 hdr 00
(II) PCI: 00:0a:0: chip 104c,ac50 card 1000,0000 rev 01 class 06,07,00 hdr 02
(II) PCI: 00:0d:0: chip 10b7,9200 card 1028,00dc rev 78 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 11c1,0448 card 1668,2500 rev 01 class 07,80,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4c4d card 1028,00dc rev 64 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,4320 card 1154,032e rev 03 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x008c (VGA_EN is set)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[b]
    [1] -1    0    0x0000e400 - 0x0000e4ff (0x100) IX[b]
    [2] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b]
    [3] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfd000000 - 0xfecfffff (0x1d00000) MX[b]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0x28000000 - 0x280fffff (0x100000) MX[b]
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,5), BCTRL: 0x0500 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x00001000 - 0x000010ff (0x100) IX[b]
    [1] -1    0    0x00001400 - 0x000014ff (0x100) IX[b]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0x24000000 - 0x27ffffff (0x4000000) MX[b]
(II) Bus 2 prefetchable memory range:
    [0] -1    0    0x20000000 - 0x23ffffff (0x4000000) MX[b]
(--) PCI:*(1:0:0) ATI Technologies Inc Rage Mobility P/M AGP 2x rev 100, Mem @ 0xfd000000/24, 0xfecfe000/12, I/O @ 0xe800/8
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
    [0] -1    0    0x24000000 - 0x24001fff (0x2000) MX[b]
    [1] -1    0    0xfeded800 - 0xfeded8ff (0x100) MX[b]
    [2] -1    0    0xfededc00 - 0xfededc7f (0x80) MX[b]
    [3] -1    0    0xfedf0000 - 0xfedfffff (0x10000) MX[b]
    [4] -1    0    0xfedef000 - 0xfedeffff (0x1000) MX[b]
    [5] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [6] -1    0    0xfecfe000 - 0xfecfefff (0x1000) MX[b](B)
    [7] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
    [8] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[b]
    [9] -1    0    0x0000fcc8 - 0x0000fccf (0x8) IX[b]
    [10] -1    0    0x0000fc00 - 0x0000fc7f (0x80) IX[b]
    [11] -1    0    0x0000fce0 - 0x0000fcff (0x20) IX[b]
    [12] -1    0    0x0000fcd0 - 0x0000fcdf (0x10) IX[b]
    [13] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0x24000000 - 0x24001fff (0x2000) MX[b]
    [1] -1    0    0xfeded800 - 0xfeded8ff (0x100) MX[b]
    [2] -1    0    0xfededc00 - 0xfededc7f (0x80) MX[b]
    [3] -1    0    0xfedf0000 - 0xfedfffff (0x10000) MX[b]
    [4] -1    0    0xfedef000 - 0xfedeffff (0x1000) MX[b]
    [5] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [6] -1    0    0xfecfe000 - 0xfecfefff (0x1000) MX[b](B)
    [7] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
    [8] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[b]
    [9] -1    0    0x0000fcc8 - 0x0000fccf (0x8) IX[b]
    [10] -1    0    0x0000fc00 - 0x0000fc7f (0x80) IX[b]
    [11] -1    0    0x0000fce0 - 0x0000fcff (0x20) IX[b]
    [12] -1    0    0x0000fcd0 - 0x0000fcdf (0x10) IX[b]
    [13] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x23ffffff (0x23f00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x23ffffff (0x23f00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x24000000 - 0x24001fff (0x2000) MX[b]
    [5] -1    0    0xfeded800 - 0xfeded8ff (0x100) MX[b]
    [6] -1    0    0xfededc00 - 0xfededc7f (0x80) MX[b]
    [7] -1    0    0xfedf0000 - 0xfedfffff (0x10000) MX[b]
    [8] -1    0    0xfedef000 - 0xfedeffff (0x1000) MX[b]
    [9] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [10] -1    0    0xfecfe000 - 0xfecfefff (0x1000) MX[b](B)
    [11] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
    [12] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [13] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [14] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[b]
    [15] -1    0    0x0000fcc8 - 0x0000fccf (0x8) IX[b]
    [16] -1    0    0x0000fc00 - 0x0000fc7f (0x80) IX[b]
    [17] -1    0    0x0000fce0 - 0x0000fcff (0x20) IX[b]
    [18] -1    0    0x0000fcd0 - 0x0000fcdf (0x10) IX[b]
    [19] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.2.0, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 6.6.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
    compiled for 4.2.0, module version = 1.0.0
    Module class: XFree86 XInput Driver
    ABI class: XFree86 XInput driver, version 0.3
(II) ATI: ATI driver (version 6.6.3) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
    ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
    ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
    ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
    ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
    ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
    ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
    ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
    ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
    ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
    ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
    ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330/340/350 (A4) 4137,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
    ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP),
    ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
    ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
    ATI FireGL RV360 AV (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
    ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
    ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE),
    ATI Radeon Mobility X600 (M24) 3150 (PCIE),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE),
    ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
    ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
    ATI Radeon AIW X800 VE (R420) JT (AGP),
    ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
    ATI Radeon X850 5D4C (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies Inc Rage Mobility P/M AGP 2x".
(II) ATI:  Shared PCI/AGP Mach64 in slot 1:0:0 detected.
(II) ATI:  Shared PCI/AGP Mach64 in slot 1:0:0 assigned to active "Device" section "ATI Technologies Inc Rage Mobility P/M AGP 2x".
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x23ffffff (0x23f00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x24000000 - 0x24001fff (0x2000) MX[b]
    [5] -1    0    0xfeded800 - 0xfeded8ff (0x100) MX[b]
    [6] -1    0    0xfededc00 - 0xfededc7f (0x80) MX[b]
    [7] -1    0    0xfedf0000 - 0xfedfffff (0x10000) MX[b]
    [8] -1    0    0xfedef000 - 0xfedeffff (0x1000) MX[b]
    [9] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [10] -1    0    0xfecfe000 - 0xfecfefff (0x1000) MX[b](B)
    [11] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
    [12] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [13] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [14] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[b]
    [15] -1    0    0x0000fcc8 - 0x0000fccf (0x8) IX[b]
    [16] -1    0    0x0000fc00 - 0x0000fc7f (0x80) IX[b]
    [17] -1    0    0x0000fce0 - 0x0000fcff (0x20) IX[b]
    [18] -1    0    0x0000fcd0 - 0x0000fcdf (0x10) IX[b]
    [19] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
(II) Loading sub module "atimisc"
(II) LoadModule: "atimisc"
(II) Loading /usr/lib/xorg/modules/drivers//atimisc_drv.so
(II) Module atimisc: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 6.6.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x23ffffff (0x23f00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x24000000 - 0x24001fff (0x2000) MX[b]
    [5] -1    0    0xfeded800 - 0xfeded8ff (0x100) MX[b]
    [6] -1    0    0xfededc00 - 0xfededc7f (0x80) MX[b]
    [7] -1    0    0xfedf0000 - 0xfedfffff (0x10000) MX[b]
    [8] -1    0    0xfedef000 - 0xfedeffff (0x1000) MX[b]
    [9] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [10] -1    0    0xfecfe000 - 0xfecfefff (0x1000) MX[b](B)
    [11] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
    [12] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [13] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [14] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [15] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [16] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [17] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[b]
    [18] -1    0    0x0000fcc8 - 0x0000fccf (0x8) IX[b]
    [19] -1    0    0x0000fc00 - 0x0000fc7f (0x80) IX[b]
    [20] -1    0    0x0000fce0 - 0x0000fcff (0x20) IX[b]
    [21] -1    0    0x0000fcd0 - 0x0000fcdf (0x10) IX[b]
    [22] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
    [23] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [24] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(==) ATI(0): Chipset:  "ati".
(**) ATI(0): Depth 24, (--) framebuffer bpp 32
(==) ATI(0): Using XAA acceleration architecture
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) ATI(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) ATI(0): VESA BIOS detected
(II) ATI(0): VESA VBE Version 2.0
(II) ATI(0): VESA VBE Total Mem: 4096 kB
(II) ATI(0): VESA VBE OEM: ATI MACH64
(II) ATI(0): VESA VBE OEM Software Rev: 1.0
(II) ATI(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) ATI(0): VESA VBE OEM Product: MACH64RM
(II) ATI(0): VESA VBE OEM Product Rev: 01.00
(II) ATI(0): VESA VBE DDC supported
(II) ATI(0): VESA VBE DDC Level none
(II) ATI(0): VESA VBE DDC transfer in appr. 2 sec.
(II) ATI(0): VESA VBE DDC read failed
(II) ATI(0): BIOS Data:  BIOSSize=0x10000, ROMTable=0x0108.
(II) ATI(0): BIOS Data:  ClockTable=0x09FA, FrequencyTable=0x09D4.
(II) ATI(0): BIOS Data:  LCDTable=0x0174, LCDPanelInfo=0xBE66.
(II) ATI(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x0152.
(II) ATI(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.
(--) ATI(0): ATI 3D Rage Mobility graphics controller detected.
(--) ATI(0): Chip type 4C4D "LM", version 4, foundry TSMC, class 0, revision 0x01.
(--) ATI(0): AGP bus interface detected;  block I/O base is 0xE800.
(--) ATI(0): ATI Mach64 adapter detected.
(!!) ATI(0): For information on using the multimedia capabilities
    of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) ATI(0): Internal RAMDAC (subtype 1) detected.
(==) ATI(0): RGB weight 888
(==) ATI(0): Default visual is TrueColor
(==) ATI(0): Using gamma correction (1.0, 1.0, 1.0)
(II) ATI(0): Using Mach64 accelerator CRTC.
(--) ATI(0): 1024x768 panel (ID 5) detected.
(--) ATI(0): Panel model LG LP121X1-A2.
(--) ATI(0): Panel clock is 65.146 MHz.
(II) ATI(0): Using digital flat panel interface.
(II) ATI(0): Storing hardware cursor image at 0xFD3FFC00.
(II) ATI(0): Using 8 MB linear aperture at 0xFD000000.
(!!) ATI(0): Virtual resolutions will be limited to 4095 kB
 due to linear aperture size and/or placement of hardware cursor image area.
(II) ATI(0): Using Block 0 MMIO aperture at 0xFECFE400.
(II) ATI(0): Using Block 1 MMIO aperture at 0xFECFE000.
(==) ATI(0): Write-combining range (0xfd000000,0x400000)
(II) ATI(0): MMIO write caching enabled.
(--) ATI(0): 4096 kB of SGRAM (2:1) 32-bit detected (using 4095 kB).
(WW) ATI(0): Cannot shadow an accelerated frame buffer.
(II) ATI(0): Engine XCLK 62.227 MHz;  Refresh rate code 1.
(--) ATI(0): Internal programmable clock generator detected.
(--) ATI(0): Reference clock 29.500 MHz.
(WW) ATI(0): Extraneous XF86Config HorizSync specification(s) ignored.
(!!) ATI(0): Conflicting XF86Config VertRefresh specification(s) ignored.
(II) ATI(0): Maximum clock: 124.00 MHz
(II) ATI(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) ATI(0): Not using default mode "640x480" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) ATI(0): Not using default mode "640x480" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ATI(0): Not using default mode "640x512" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ATI(0): Not using default mode "640x512" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) ATI(0): Not using default mode "640x512" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x600" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ATI(0): Not using default mode "896x672" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) ATI(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ATI(0): Not using default mode "928x696" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) ATI(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "1280x768" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1280x800" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "640x400" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1152x768" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "576x432" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "700x525" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "700x525" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "700x525" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "700x525" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) ATI(0): Not using default mode "720x450" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) ATI(0): Not using default mode "800x512" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) ATI(0): Not using default mode "840x525" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x600" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x600" (exceeds panel dimensions)
(II) ATI(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) ATI(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) ATI(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) ATI(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) ATI(0): Virtual size is 1024x768 (pitch 1024)
(**) ATI(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) ATI(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) ATI(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) ATI(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) ATI(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) ATI(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) ATI(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) ATI(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) ATI(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) ATI(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) ATI(0):  Built-in mode "Native panel mode": 65.1 MHz, 62.6 kHz, 81.4 Hz
(II) ATI(0): Modeline "Native panel mode"   65.15  1024 1024 1032 1040  768 768 769 770
(**) ATI(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) ATI(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) ATI(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) ATI(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) ATI(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) ATI(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) ATI(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) ATI(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) ATI(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) ATI(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) ATI(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) ATI(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) ATI(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) ATI(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) ATI(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) ATI(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) ATI(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) ATI(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) ATI(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) ATI(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) ATI(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) ATI(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) ATI(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) ATI(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) ATI(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) ATI(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) ATI(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) ATI(0):  Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) ATI(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) ATI(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) ATI(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) ATI(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) ATI(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) ATI(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) ATI(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) ATI(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) ATI(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) ATI(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) ATI(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) ATI(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) ATI(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) ATI(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) ATI(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) ATI(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) ATI(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) ATI(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) ATI(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) ATI(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) ATI(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) ATI(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) ATI(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) ATI(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) ATI(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) ATI(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) ATI(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) ATI(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) ATI(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) ATI(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(==) ATI(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.1
(II) ATI(0): I2C bus "Mach64" initialized.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xfecfe000 - 0xfecfefff (0x1000) MS[b]
    [1] 0    0    0xfd000000 - 0xfdffffff (0x1000000) MS[b]
    [2] -1    0    0x00100000 - 0x23ffffff (0x23f00000) MX[b]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [6] -1    0    0x24000000 - 0x24001fff (0x2000) MX[b]
    [7] -1    0    0xfeded800 - 0xfeded8ff (0x100) MX[b]
    [8] -1    0    0xfededc00 - 0xfededc7f (0x80) MX[b]
    [9] -1    0    0xfedf0000 - 0xfedfffff (0x10000) MX[b]
    [10] -1    0    0xfedef000 - 0xfedeffff (0x1000) MX[b]
    [11] -1    0    0xf8000000 - 0xf7ffffff (0x0) MX[b]O
    [12] -1    0    0xfecfe000 - 0xfecfefff (0x1000) MX[b](B)
    [13] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[b](B)
    [14] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
    [15] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
    [16] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
    [17] 0    0    0x0000e800 - 0x0000e8ff (0x100) IS[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [20] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[b]
    [21] -1    0    0x0000fcc8 - 0x0000fccf (0x8) IX[b]
    [22] -1    0    0x0000fc00 - 0x0000fc7f (0x80) IX[b]
    [23] -1    0    0x0000fce0 - 0x0000fcff (0x20) IX[b]
    [24] -1    0    0x0000fcd0 - 0x0000fcdf (0x10) IX[b]
    [25] -1    0    0x0000e800 - 0x0000e8ff (0x100) IX[b](B)
    [26] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [27] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(==) ATI(0): Write-combining range (0xfd000000,0x400000)
(WW) ATI(0): DRI static buffer allocation failed -- need at least 7680 kB video memory
(II) ATI(0): Largest offscreen areas (with overlaps):
(II) ATI(0):     1024 x 255 rectangle at 0,768
(II) ATI(0):     768 x 256 rectangle at 0,768
(II) ATI(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Offscreen Pixmaps
    Setting up tile and stipple cache:
        8 128x128 slots
(==) ATI(0): Backing store disabled
(==) ATI(0): Silken mouse enabled
(**) Option "dpms"
(**) ATI(0): DPMS enabled
(II) ATI(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?It's a [Dell Latitude L400]("http://www.mbhoy.com/21-07-2007/dell-latitude-l400-laptop"). Should I follow the guide you wrote above? And yes, it's an 8MB card. :smile:

---

### Post by Old Pink on 2007-07-22
lspci:
> 00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01)
**01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)**
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by kjander on 2007-07-23
got an error for the very first step
> 
kristoffer@kristoffer-laptop:~$ sudo apt-get install --reinstall libgl1-mesa
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgl1-mesa is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgl1-mesa has no installation candidate


---

### Post by dougfractal on 2007-07-23
> **kjander said:**
> got an error for the very first step

sorry incomplete package name. ( If I do it again, use synaptic and search, then look for similar packages) 

```
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```

now using guide from
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by Old Pink on 2007-07-23
> **dougfractal said:**
> sorry incomplete package name. ( If I do it again, use synaptic and search, then look for similar packages) 

```
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```now using guide from
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Any idea about *my *problem? Seems kjander just stole my thread, and he doesn't even have the same equipment.

---

### Post by kjander on 2007-07-23
Sorry old pink, didnt mean to steal the thread completely away

---

### Post by dougfractal on 2007-07-23
> Any idea about my problem? Seems kjander just stole my thread, and he doesn't even have the same equipment.

You've both got 8mb  ati card and want  Direct Rendering. This is a community forum where more people than yourselves may find this useful. I've only had one personal experience of installing beryl on an Ati card, as I use nvidia. But I feel confident that I can help you. 

Follow the suggestions, tell me what happens. I'm sorry this is a process of exprimentation. 
I'm not going to ask you to download this, compile that. Just edit the xorg.conf and use apt-get.

Matt I've seen that you've been asked in the past to do all sorts. My guide will assume that thing are as vanilia as possible.  You may need to "sudo apt-get remove xorg-driver-fglrx"

So backup your xorg.conf, get used to  [ctl]+[alt]+[f1] to goto terminal
"cd /etc/X11"  to change directory.
"sudo cp xorg.conf xorg.conf.ati"   to copy a backup
"sudo nano /etc/X11/xorg.conf"  to edit a file in text
"sudo /etc/init.d/gdm restart"  to restart X
"sudo cp xorg.conf xorg.conf.mymod"   to copy modded xorg that didn't work
"sudo cp xorg.conf.ati xorg.conf"   to restore from backup and get it back to how it was.
[ctl]+[alt]+[f7] to goto graphical

hopefully It will be plain sailing and you will have no problems. Please follow the instructions.

```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.ati
```

/etc/X11/xorg.conf
```
Section "ServerLayout"
        Identifier     "Default Layout"
        Option          "AIGLX"         "true"
        Screen        "Screen0" 
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Synaptics" "AlwaysCore"
EndSection

Section "Files"
        RgbPath      "/usr/X11R6/lib/X11/rgb"
        FontPath     "unix/:7100"
EndSection

Section "Module"
        Load  "dbe"
        Load  "extmod"
        Load  "fbdevhw"
        Load  "glx"
        Load  "record"
        Load  "freetype"
        Load  "type1"
        Load  "synaptics"
        Load  "dri"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "gb"
EndSection


Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "IMPS/2"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "yes"
EndSection
Section "InputDevice"
        Identifier  "Synaptics"
        Driver      "synaptics"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "auto-dev"
        Option      "Emulate3Buttons" "yes"
        Option      "SHMconfig" "on"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "LCD Panel 1024x768"
        HorizSync    31.5 - 90.0
        VertRefresh  60.0 - 60.0
        Option      "dpms"
EndSection

Section "Device"
      	Identifier  "Videocard0"     # ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)
     	Driver "radeon"
	boardname "ATI Radeon"
	vendorname "ATI"
	option "MergedFB" "off"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "true"
	Option "EnablePageFlip" "True"
	Option "UseInternalAGPGART" "no"
	Option "backingstore" "true"
	Option "AllowGLXWithComposite" "true"
	Option "RenderAccel" "true"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
	Viewport   0 0
        Depth     24
        Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Group        0
        Mode         0666
EndSection
```

install

```
sudo apt-get install beryl beryl-manager
```

post the output of
******************************************
* Beryl system compatiblity check *
******************************************

```
beryl
```

Good luck, keep me posted
Doug


[http://www.howtoforge.com/ubuntu_fei...ryl_ati_radeon](http://www.howtoforge.com/ubuntu_fei...ryl_ati_radeon)

---

### Post by Old Pink on 2007-07-23
It's not a radeon card, and as expected, the radeon driver didn't work.

---

### Post by dougfractal on 2007-07-23
> It's not a radeon card, and as expected, the radeon driver didn't work.
didn't work as in no X.   
The radeon driver along with ati driver are the open source drivers for ATI  cards.
so were you all right in getting X back working?

Ok send "beryl" output when using the 'driver "ati" '.

The only thing that kept me going when I was trying to setup 3d Effects, was seeing  it work on my ati laptop with the Live CD  "kororaa-xgl-livecd-0.2.iso". google search it. It was a live cd that ran compiz, when compiz had just come out.   
> 
and as expected
And please Matt, you've been tring this for a while, imagine what it's like with out the computer infront  of you.

Get the CD. Tell me if it can run compiz.

---

### Post by dougfractal on 2007-07-23
[B]DON'T EVEN GO HERE!  
THERE BE DRAGONS.

I'M working on an up date give me time[/B]

from [http://doc.gwos.org/index.php/3daccelleration_-_mach64](http://doc.gwos.org/index.php/3daccelleration_-_mach64)
> HOWTO: enable 3d acceleration w/ Rage Mobility (mach64)

I have been struggling w/ this for the past two weeks....and I finally got 3d acceleration to work w/ my ati rage mobility. I'm using xorg, but I beleive that it works w/ xfree86 as well. first of all, here's my card according to lspci

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

it uses the mach64 chipset.

now here's how I got direct rendering to work: 

follow the guide. You'll have to run the install script every kernal upgrade so keep the files handy maybe in "~/.mach64". I was hoping for somthing more ubuntu, but hey, if it works.

Let me know how you get on.
Doug

---

### Post by Old Pink on 2007-07-23
> **dougfractal said:**
> [B]DON'T EVEN GO HERE!  
THERE BE DRAGONS.

I'M working on an up date give me time[/B]

from [http://doc.gwos.org/index.php/3daccelleration_-_mach64](http://doc.gwos.org/index.php/3daccelleration_-_mach64)


follow the guide. You'll have to run the install script every kernal upgrade so keep the files handy maybe in "~/.mach64". I was hoping for somthing more ubuntu, but hey, if it works.

Let me know how you get on.
Doug
That was the first guide I follwed, the common part installs well, but the mach64 part complains of needing latest kernel modules. Even though I have them. Thanks for working on an update.

> **dougfractal said:**
> didn't work as in no X.   
The radeon driver along with ati driver are the open source drivers for ATI  cards.
so were you all right in getting X back working?

Ok send "beryl" output when using the 'driver "ati" '.

The only thing that kept me going when I was trying to setup 3d Effects, was seeing  it work on my ati laptop with the Live CD  "kororaa-xgl-livecd-0.2.iso". google search it. It was a live cd that ran compiz, when compiz had just come out.   

And please Matt, you've been tring this for a while, imagine what it's like with out the computer infront  of you.

Get the CD. Tell me if it can run compiz.I'll try the CD tomorrow. And yes, didn't work as in no X, blue screen with grey dialog asking me to view outputs, etc.

And I'm familiar with command line, I just used nano in sudo to modify the file back. :)

---

### Post by dougfractal on 2007-07-25
> **kfazz said:**
> in order to get dri working for mach 64 theres two things you need to do: 
Much thanks to Kfazz for creating an easy basic guide.
-----------------------------------------------------------------------------------------

In order to get DRI working for Mach64 you need to:

This is untested because I don't have a Mach64 card. It does compile.
Please let me know if in the Section "driver": driver "ati" needs to be : driver "mach64"

The steps:
Setup compiler and libraries
make a new directory to hold the drm and ati source
download, build install and latest drm from freedesktop.org
download, build install and latest ati driver


Activate sudo
```
sudo echo "activating sudo rights"
```

And now to business. Copy and paste into terminal.
```

sudo apt-get install linux-headers-generic build-essential
sudo apt-get install autoconf-archive xorg-dev
SRCPATH=`pwd` 
cd $SRCPATH 
if [ -d 'src' ]; then echo -n ""; else mkdir src ; fi
cd src
if [ "$GIT" -neq '1' ] ; then git clone git://anongit.freedesktop.org/git/mesa/drm ; fi
cd drm/linux-core
make DRM_MODULES="mach64" 
if [ -f mach64.ko ] ; then echo -e "\nSuccess\n" ; \
sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/;  \
sudo depmod -a; \
sudo modprobe mach64; \
else \ 
echo -e '\nIn a previous error I needed to comment out "/*  .... */" function static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,  unsigned long pfn) in drm/linux-core/drm_compat.c  lines 189-198 \n If this is the same error then do it.\nnano src/drm/linux-core/drm_compat.c\n'; \ 
GIT='1'; \
cd $SRCPATH;\
sleep 5; \
fi

```

If you get an error do the edit and then run the first script again.
I needed to comment out "/*  .... */" function static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,  unsigned long pfn) in drm/linux-core/drm_compat.c  lines 189-198
gedit src/drm/linux-core/drm_compat.c

```

# part two
cd $SRCPATH/src
if [ -f 'xf86-video-ati-6.6.192.tar.bz2' ]; then echo "already have xf86-video-ati"; else \
	wget http://xorg.freedesktop.org/archive/individual/driver/xf86-video-ati-6.6.192.tar.bz2 ;     \
	tar xvjf xf86-video-ati-6.6.192.tar.bz2  ;\
fi
cd xf86-video-ati-6.6.192
./configure --prefix=/usr
make clean
make
sudo make install
cd $SRCPATH/
echo -e "\nsudo /etc/init.d/gdm restart\n"

```

Keep this script as you will need it every kernel upgrade.

---

### Post by Old Pink on 2007-07-25
Couple of lines in:> matt@matt-laptop:~/src$ if [ "$GIT" -neq '1' ] ; then git clone git://anongit.freedesktop.org/git/mesa/drm ; fi
bash: [: -neq: binary operator expected

---

### Post by Old Pink on 2007-07-25
> **Old Pink said:**
> Couple of lines in:
Continued using **git clone git://anongit.freedesktop.org/git/mesa/drm **which seemed to work.> matt@matt-laptop:~/src$ if [ "$GIT" -neq '1' ] ; then git clone git://anongit.freedesktop.org/git/mesa/drm ; fi
bash: [: -neq: binary operator expected
matt@matt-laptop:~/src$ git clone git://anongit.freedesktop.org/git/mesa/drm
destination directory 'drm' already exists.
matt@matt-laptop:~/src$ rm drm -fr
matt@matt-laptop:~/src$ git clone git://anongit.freedesktop.org/git/mesa/drm
remote: Generating pack...
remote: Done counting 24114 objects.
remote: Deltifying 24114 objects.
remote:  100% (24114/24114) done
Indexing 24114 objects.
remote: Total 24114 (delta 18318), reused 20316 (delta 15298)
 100% (24114/24114) done
Resolving 18318 deltas.
 100% (18318/18318) done
Checking files out...
 100% (379/379) doneWent into drm/linux-core:> matt@matt-laptop:~/src$ cd drm/linux-coreDid the next bit and got a huge error:> matt@matt-laptop:~/src/drm/linux-core$ make DRM_MODULES="mach64" 
sh ../scripts/create_linux_pci_lists.sh < ../shared-core/drm_pciids.txt
make -C /lib/modules/2.6.20-16-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/matt/src/drm/linux-core/drm_auth.o
  CC [M]  /home/matt/src/drm/linux-core/drm_bufs.o
  CC [M]  /home/matt/src/drm/linux-core/drm_context.o
  CC [M]  /home/matt/src/drm/linux-core/drm_dma.o
  CC [M]  /home/matt/src/drm/linux-core/drm_drawable.o
  CC [M]  /home/matt/src/drm/linux-core/drm_drv.o
  CC [M]  /home/matt/src/drm/linux-core/drm_fops.o
  CC [M]  /home/matt/src/drm/linux-core/drm_ioctl.o
  CC [M]  /home/matt/src/drm/linux-core/drm_irq.o
  CC [M]  /home/matt/src/drm/linux-core/drm_lock.o
  CC [M]  /home/matt/src/drm/linux-core/drm_memory.o
  CC [M]  /home/matt/src/drm/linux-core/drm_proc.o
  CC [M]  /home/matt/src/drm/linux-core/drm_stub.o
  CC [M]  /home/matt/src/drm/linux-core/drm_vm.o
  CC [M]  /home/matt/src/drm/linux-core/drm_sysfs.o
  CC [M]  /home/matt/src/drm/linux-core/drm_pci.o
  CC [M]  /home/matt/src/drm/linux-core/drm_agpsupport.o
  CC [M]  /home/matt/src/drm/linux-core/drm_scatter.o
  CC [M]  /home/matt/src/drm/linux-core/drm_memory_debug.o
  CC [M]  /home/matt/src/drm/linux-core/ati_pcigart.o
  CC [M]  /home/matt/src/drm/linux-core/drm_sman.o
  CC [M]  /home/matt/src/drm/linux-core/drm_hashtab.o
  CC [M]  /home/matt/src/drm/linux-core/drm_mm.o
  CC [M]  /home/matt/src/drm/linux-core/drm_object.o
  CC [M]  /home/matt/src/drm/linux-core/drm_compat.o
/home/matt/src/drm/linux-core/drm_compat.c:190: error: static declaration of ‘vm_insert_pfn’ follows non-static declaration
include/linux/mm.h:1126: error: previous declaration of ‘vm_insert_pfn’ was here
make[2]: *** [/home/matt/src/drm/linux-core/drm_compat.o] Error 1
make[1]: *** [_module_/home/matt/src/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2Going to comment out that line now.

---

### Post by Old Pink on 2007-07-25
And then this happened:> matt@matt-laptop:~/src/drm/linux-core$ make DRM_MODULES="mach64" 
make -C /lib/modules/2.6.20-16-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/matt/src/drm/linux-core/drm_compat.o
/home/matt/src/drm/linux-core/drm_compat.c:188:2: error: invalid preprocessing directive #static
/home/matt/src/drm/linux-core/drm_compat.c:189:6: error: invalid preprocessing directive #unsigned
/home/matt/src/drm/linux-core/drm_compat.c:190:2: error: invalid preprocessing directive #{
/home/matt/src/drm/linux-core/drm_compat.c:191:3: error: invalid preprocessing directive #int
/home/matt/src/drm/linux-core/drm_compat.c:192:5: error: invalid preprocessing directive #(
/home/matt/src/drm/linux-core/drm_compat.c:193:4: error: invalid preprocessing directive #return
/home/matt/src/drm/linux-core/drm_compat.c:195:3: error: invalid preprocessing directive #ret
/home/matt/src/drm/linux-core/drm_compat.c:196:3: error: invalid preprocessing directive #return
/home/matt/src/drm/linux-core/drm_compat.c:197:2: error: invalid preprocessing directive #}
make[2]: *** [/home/matt/src/drm/linux-core/drm_compat.o] Error 1
make[1]: *** [_module_/home/matt/src/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2
matt@matt-laptop:~/src/drm/linux-core$ gedit drm_compat.c 
matt@matt-laptop:~/src/drm/linux-core$ make DRM_MODULES="mach64" 
make -C /lib/modules/2.6.20-16-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/matt/src/drm/linux-core/drm_compat.o
/home/matt/src/drm/linux-core/drm_compat.c:188:3: error: invalid preprocessing directive #static
/home/matt/src/drm/linux-core/drm_compat.c:189:6: error: invalid preprocessing directive #unsigned
/home/matt/src/drm/linux-core/drm_compat.c:190: error: expected identifier or &#8216;(&#8217; before &#8216;{&#8217; token
make[2]: *** [/home/matt/src/drm/linux-core/drm_compat.o] Error 1
make[1]: *** [_module_/home/matt/src/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2


---

### Post by Old Pink on 2007-07-25
I'd been using # to comment out, my mistake. I just deleted those lines and we were back in business.

---

### Post by Old Pink on 2007-07-25
Well, finished the guide, and > matt@matt-laptop:~$ lsmod | grep "mach64"
mach64                 51840  0 
drm                   138264  1 mach64the mach64 module is loaded but> matt@matt-laptop:~$ glxinfo | grep "direct"
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX IndirectLet's see what happens after a reboot. :)

---

### Post by Old Pink on 2007-07-25
After a reboot:> matt@matt-laptop:~$ glxinfo | grep "direct"
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
matt@matt-laptop:~$ lsmod | grep "mach64"
mach64                 51840  0 
drm                   138264  1 mach64
matt@matt-laptop:~$ 
Still no luck, although everything is installed correctly. What about "XFree86-DRI" missing on display ":0.0"." - does that mean anything?

---

### Post by dougfractal on 2007-07-25
Check this

First of all, disable composition at xorg.  it is enable by default but ati driver doesn't support it yet.

Add this at the end of xorg.conf file:
```

Section "Extensions"
Option "Composite" "0"
EndSection
```

in Section "Module"

```
load "dri"
```

and in Section "device"    replace driver (exprimental)
```
driver "mach64"
```



I also need to see your /etc/X11/xorg.conf

---

### Post by Old Pink on 2007-07-25
> **dougfractal said:**
> 
Add this at the end of xorg.conf file:
```

Section "Extensions"
Option "Composite" "0"
EndSection
```Tried that, no change.> **dougfractal said:**
> in Section "Module"

```
load "dri"
```Always been there, no change when removed.> **dougfractal said:**
> and in Section "device"    replace driver (exprimental)
```
driver "mach64"
```Tried that, X won't start, blue screen, complains mach64 doesn't exist.

Also tried using:
driver "ati"
chipset "mach64" 

No luck, X won't start.

> **dougfractal said:**
>  I also need to see your /etc/X11/xorg.conf
Attached:

---

### Post by dougfractal on 2007-07-25
I've added to the driver section and module
It's a shame you were so rude about kfazz's howto, because his help right now would be really useful.


can give the output to these:-
dmesg | grep drm
dmesg | grep agp
grep -i "Direct rendering" /var/log/Xorg.0.log
ldd /usr/X11R6/bin/glxinfo

---

### Post by dougfractal on 2007-07-25
from [http://ubuntuforums.org/showthread.php?t=7200&page=14](http://ubuntuforums.org/showthread.php?t=7200&page=14) thanks spieslikeus

> I found out what was wrong when I tried:

export LIBGL_DEBUG=verbose
glxinfo

It told me that the library /usr/X11R6/lib/modules/dri/mach64_dri.so couldn't be found."

Yes yes this is what I get too thanks rarefluid!

I did:

cd /usr/X11R6/lib/modules/dri
sudo ln -s /usr/lib/dri/mach64_dri.so mach64_dri.so

"then glxinfo said Direct Rendering: Yes."






---

### Post by kjander on 2007-07-25
Thank you so much for this guide, it worked perfectly for me, i believe. I do have one question... my glxinfo is this:
> 
kristoffer@kristoffer-laptop:~$ glxinfo
name of display: :0.0
DISPATCH ERROR! _glapi_add_dispatch failed to add glAreTexturesResident!
DISPATCH ERROR! _glapi_add_dispatch failed to add glGenTextures!
DISPATCH ERROR! _glapi_add_dispatch failed to add glIsTexture!
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: Gareth Hughes, Leif Delgass, Jos&#65533; Fonseca
OpenGL renderer string: Mesa DRI Mach64 [Rage Pro] 20051019 AGP 2x x86/MMX
OpenGL version string: 1.2 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_subtexture, GL_EXT_texture, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2f 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
kristoffer@kristoffer-laptop:~$ glxgears
DISPATCH ERROR! _glapi_add_dispatch failed to add glAreTexturesResident!
DISPATCH ERROR! _glapi_add_dispatch failed to add glGenTextures!
DISPATCH ERROR! _glapi_add_dispatch failed to add glIsTexture!
977 frames in 5.3 seconds = 185.964 FPS
1056 frames in 5.0 seconds = 211.137 FPS
905 frames in 5.0 seconds = 180.995 FPS
kristoffer@kristoffer-laptop:~$ 


are those dispatch errors important? seems to work despite them, as you can see from my glxgears output. anyone know a way to eliminate the errors?

---

### Post by Old Pink on 2007-07-25
> **dougfractal said:**
> 
can give the output to these:-
dmesg | grep drm
dmesg | grep agp
grep -i "Direct rendering" /var/log/Xorg.0.log
ldd /usr/X11R6/bin/glxinfo
> matt@matt-laptop:~$ dmesg | grep drm
[   49.848000] [drm] Initialized drm 1.1.0 20060810
[   49.916000] [drm] Initialized mach64 2.0.0 20060718 on minor 0
matt@matt-laptop:~$ dmesg | grep agp
[   44.056000] Linux agpgart interface v0.102 (c) Dave Jones
[   44.076000] agpgart: Detected an Intel 440BX Chipset.
[   44.084000] agpgart: AGP aperture is 64M @ 0xf8000000
matt@matt-laptop:~$ grep -i "Direct rendering" /var/log/Xorg.0.log
(II) ATI(0): Direct rendering disabled
matt@matt-laptop:~$ ldd /usr/X11R6/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ecd000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d8c000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c9b000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c8d000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c76000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c72000)
        /lib/ld-linux.so.2 (0xb7f7b000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c6e000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c69000)
Looking into your second post now.

Regards

---

### Post by Old Pink on 2007-07-25
Neither the modified xorg.conf file you created nor the fix from "spieslikeus" working on direct rendering, with the only difference being slightly worse coloring on the splash screen after login when using your Xorg.conf.

Thanks for all the effort you're putting in here :)

---

### Post by dougfractal on 2007-07-26
> **kjander said:**
> Thank you so much for this guide, it worked perfectly for me, i believe. I do have one question... my glxinfo is this:


are those dispatch errors important? seems to work despite them, as you can see from my glxgears output. anyone know a way to eliminate the errors?

I don't know about the errors,I guess some features are missing on the card.  But 180+ fps is good for this card.
Have you got beryl or compiz running?

Please could you quote which parts of the guide worked for you and send your xorg.conf as I am trying to create yet another howto with one script.

---

### Post by dougfractal on 2007-07-26
**[SIZE="4"]Direct Rendering on Mach64 (Feisty)[/SIZE]**
 
This is a script to use as a last resort, when all other guides have failed!
It is meant to be easy but it does use snapshots that are over a year old so may cause problems later. 

Copy and paste in one big swoop into the terminal
```

echo -e "You need sudo active for this script\nIf you need to enter the password, do so and run this script again\n"
sudo apt-get install linux-headers-generic build-essential
cd /usr/src/linux-headers-`uname -r`/include/linux
if [ -f 'config.h' ] ; then echo -n ''; else sudo ln -s autoconf.h config.h; fi
cd /usr/src
if ! [ -d 'mach64_dri' ] ; then sudo mkdir mach64_dri; sudo chown $UID mach64_dri; fi
cd mach64_dri
if ! [ -d 'common-20060403-linux.i386' ] ; then  \
   wget http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2 ;\
   tar xjvf common-20060403-linux.i386.tar.bz2 ; \
fi
if ! [ -d 'mach64-20060403-linux.i386' ] ; then  \
    wget http://dri.freedesktop.org/snapshots/mach64-20060403-linux.i386.tar.bz2 ; \
    tar xjvf mach64-20060403-linux.i386.tar.bz2  ; \
    sed -i '87s\__put_page\put_page\'  /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c  ; \
    sed -i -e '51a\*/' -e   '51i\/*' /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/drm_stub.c ; \
fi
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
sudo sed -i 's\DefaultDepth    24\DefaultDepth    16\'  /etc/X11/xorg.conf
echo -n "sudo echo -e '\nYou must run this script as root.\n';
cd /usr/src/mach64_dri/common-20060403-linux.i386
sudo ./install.sh
cd  /usr/src/mach64_dri/mach64-20060403-linux.i386
sudo ./install.sh
echo -e '\nRestart X-Windows to activate driver\n'
echo -e 'type:    sudo /etc/init.d/gdm restart\n' " > ~/mach64driver.sh
sed -i '1i\#!/bin/bash' ~/mach64driver.sh
chmod 755 ~/mach64driver.sh
cat ~/mach64driver.sh
sudo ~/mach64driver.sh

```


This script will self-make  a script called **~/mach64driver.sh** that you will need to run every kernel upgrade.


**_check with_**
```
glxinfo | grep direct
glxgears
```


**_FeedBack_**

Could you please list your working card model.
```
lspci | grep -i vga
```

I would really appreciate it if posts were concise, and what troubleshooting steps where made to get it working.


[B][U]
Troubleshooting[/U][/B]

linux-image-686|k7|386 has been obsoleted by: linux-image-generic
```
sudo apt-get install linux-image-generic
```

xorg and other packages have been so messed up you need to start a fresh before running the script
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx 
```


```
export LIBGL_DEBUG=verbose
glxinfo
```
It told me that the library /usr/X11R6/lib/modules/dri/mach64_dri.so couldn't be found."
```
cd /usr/X11R6/lib/modules/dri
sudo ln -s /usr/lib/dri/mach64_dri.so mach64_dri.so
```

```
cat /var/log/Xorg.0.log | grep EE
```
If the output has this somewheres...:
> (EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least xxxxx kB of video memory needed at this resolution and depth.
Change your bit depth to 16 instead of the default 24...look for this line in your /etc/X11/xorg.conf file under the "Screen" section
```
DefaultDepth    16
```

I wanted 24 bit display not the 16bit you forced on me.
sorry I naively thought your card only had 8meg ram
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
sudo sed -i 's\DefaultDepth    16\DefaultDepth    24\'  /etc/X11/xorg.conf

```



*This howto has been put together off the backs of so many other members.*

---

### Post by dougfractal on 2007-07-26
Matt please reinstall xorg

> **dougfractal said:**
> **[SIZE="4"]Direct Rendering on Mach64 (Feisty)[/SIZE]**
 
[B][U]
Troubleshooting[/U][/B]

xorg and other packages have been so messed up you need to start a fresh
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa-dri xlibmesa-dri
```



---

### Post by Old Pink on 2007-07-26
> **dougfractal said:**
> Matt please reinstall xorgHave done, many times, still no luck. :(

---

### Post by dougfractal on 2007-07-26
> **dougfractal said:**
> Matt please reinstall xorg
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa-dri xlibmesa-dri

maybe libgl1-mesa-dri and xlibmesa-dri are actually getting in the way of the new script. After all the script is meant to make its own dri, I think.

So can you "**sudo apt-get remove libgl1-mesa-dri xlibmesa-dri**"
I'm sure it's a problem from a previous attempt that hasn't been purged from your system.

From synaptic I found that  libgl1-mesa-dri conflicts with xlibmesa-dri, so i you need to reinstall only do "sudo apt-get install libgl1-mesa-dri "

Did the script run alright for you?
Did t installed all the new drivers?

I do hope this all works for you as it's my first script with "sed" [img]http://ubuntuforums.org/images/smilies/icon_smile.gif[/img]

---

### Post by Old Pink on 2007-07-26
Remember the error here is **Xlib:  extension "XFree86-DRI" missing on display ":0.0".**> matt@matt-laptop:~$ glxinfo | grep "direct"
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by dougfractal on 2007-07-27
Matt (old pig) the fact you don't answer the questions I put to you make it very hard to help you.
I'm unsure that you are following the instructions.

1. reinstall xorg packages and xorg.conf
2. run the script from #33 (copy and paste into terminal)
3. Test
4 .Troubleshooting
> export LIBGL_DEBUG=verbose
glxinfo

It told me that the library /usr/X11R6/lib/modules/dri/mach64_dri.so couldn't be found."

cd /usr/X11R6/lib/modules/dri
sudo ln -s /usr/lib/dri/mach64_dri.so mach64_dri.so

5. Report whether  kororaa-xgl-livecd-0.2.iso worked
6.  Give up and install a diferent flavor of linux
Aparently Mepis (also debian base) dri for mach64 works straight out.
I hear Mint is very good.

---

### Post by i386DX on 2007-07-27
@Dougfractal

Tested your script in Feisty (kernel 2.6.20-16-generic). It worked without any problems!

**Extra info**

_VGA-card_
ATI-Technologies Inc Rage Mobility P/M 2x (rev64) 
(Compaq Armada E500)

_Glxinfo_
LibGL warning:  3D driver claims to not support visual 0x4b
direct rendering: Yes

_Glxgears_
LibGL warning:  3D driver claims to not support visual 0x4b
Smooth and about 136 fps ;-)

---

### Post by Old Pink on 2007-07-28
So I just paste the entirety of #33's code in one big swoop into the terminal?

---

### Post by dougfractal on 2007-07-28
> **Old Pink said:**
> So I just paste the entirety of #33's code in one big swoop into the terminal?

**YES**

copy the "code" then paste into terminal.

how do I make it clearer?

---

### Post by Old Pink on 2007-07-29
Right, post #33 seemed to work well, restarting X now, please wait for output...

---

### Post by Old Pink on 2007-07-29
> (EE) module ABI major version (0) doesn't match the server's version (1)
(EE) Failed to load module "ati" (module requirement mismatch, 0)
(EE) No drivers available

Fatal server error:
No screens found

Great script, that one. 

So great, dpkg-reconfigure xserver-xorg doesn't fix it. And nor does your created mach64driver.sh script. And yes, I've tried replacing "ati" with "mach64" - same error.

Please, fix my system.

---

### Post by Old Pink on 2007-07-29
Oh, and I love the "dri-old.ati" driver backup thing it made.

Another fantastic fatal server error from that one too.

---

### Post by Old Pink on 2007-07-29
So I guess I'm just without a laptop until you get back.

Oh and it's great you managed to prevent the use of apt-get due to WiFi's configuration being GUI based, meaning I can't get on my network.

---

### Post by Old Pink on 2007-07-29
Purged xserver-xorg-video-all and xserver-xorg-video-ati

Downloaded them to memory stick on other PC

Mounted in terminal and reinstalled from there.

X working again. 

In future, don't help someone if the effect could be as devastating as that. If I didn't have another PC, or didn't have that knowledge, I'd be stuck for good. Without even access to tell you so.

---

### Post by Old Pink on 2007-07-29
By the way, after all that:> direct rendering: No

---

### Post by dougfractal on 2007-07-29
**ATI-Technologies Inc Rage Mobility P/M 2x (rev64) SOVLED but not for Old Pink**

> **i386DX said:**
> @Dougfractal

Tested your script in Feisty (kernel 2.6.20-16-generic). It worked without any problems!

**Extra info**

_VGA-card_
ATI-Technologies Inc Rage Mobility P/M 2x (rev64) 
(Compaq Armada E500)

_Glxinfo_
LibGL warning:  3D driver claims to not support visual 0x4b
direct rendering: Yes

_Glxgears_
LibGL warning:  3D driver claims to not support visual 0x4b
Smooth and about 136 fps ;-)

Dear old pink i'm sorry that it doesn't work for you. But i386DX has confirmed that it works for your card with no problems, so there is nothing more that i can do. I guess i386DX had a fresh feisty install, as i believe that problem is in damage to the files from previous attempts or incomplete troubleshooting.

---

