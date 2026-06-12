---
title: "Ati Driver &amp; 3d Acceleration"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by Alyus on 2006-07-25
I have been having a terrible time trying to get the 3d accelleration to work with my system. I had been trying with breezy and decided to try upgrading (via clean install) to dapper hoping my problem would be magically fixed. However it wasn't. I have a somewhat different system (set up as a home theater pc) and it is attached to my hdtv via svideo connection. Any help would be greatly appreciated.

I have followed the instructions [here ]("http://ubuntuforums.org/showthread.php?t=204910")(the drivers in the repositories didn't work either).

I appologize - I don't know how to put in those cool little "code" boxes so big text files are attached.

-System Details:-
Radeon 9800 pro Hooked to tv via svideo
Asus K8n-e deluxe MB latest bios installed
Dual booting w/win2k

-dmesg | grep fglrx-
[17179598.724000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179598.724000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179598.724000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0
[17179602.416000] [fglrx] Internal AGP is not supported in 2.6 kernel.
[17179602.416000] [fglrx:firegl_unlock] *ERROR* Process 4877 using kernel context 0

-glxinfo-
name of display: :0.0
display: :0 screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
GLX_SGIX_fbconfig
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x23 24 tc 0 24 0 r y . 8 8 8 0 0 16 0 0 0 0 0 1 0 None
0x24 24 tc 0 24 0 r y . 8 8 8 0 0 16 8 16 16 16 0 1 0 None
0x25 24 tc 0 32 0 r y . 8 8 8 8 0 16 8 16 16 16 16 1 0 None
0x26 24 tc 0 32 0 r . . 8 8 8 8 0 16 8 16 16 16 16 1 0 None
0x27 24 dc 0 24 0 r y . 8 8 8 0 0 16 0 0 0 0 0 1 0 None
0x28 24 dc 0 24 0 r y . 8 8 8 0 0 16 8 16 16 16 0 1 0 None
0x29 24 dc 0 32 0 r y . 8 8 8 8 0 16 8 16 16 16 16 1 0 None
0x2a 24 dc 0 32 0 r . . 8 8 8 8 0 16 8 16 16 16 16 1 0 None

Xorg.conf = xorg.txt
xorg.0.log & kern.log are in archive.zip

Thank You very much in advance!!

Alyus

---

### Post by .Maleficus. on 2006-07-25
I don't know much about ATi, but it seems the kernel you're using doesn't support internal AGP.  Maybe if you update your kernel and then install the drivers it might work.  I don't know anything about updating kernels, so I can't help you there.

Please someone correct me if I'm wrong on this.

Also, to get the cool code boxes, type ["CODE"] at the beginning and [/"CODE"] at the end (without the quotes).

---

### Post by Alyus on 2006-07-25
Thank you Maleficus. I saw that part too, but does that mean nobody can get 3d accel. working with their agp card? is there a workaround?

---

### Post by Alyus on 2006-07-25
And thank you for the code box tip!

---

### Post by rocketman768 on 2006-07-26
Download kernel source for one of the kernels...it can even be a package provided by the ubuntu repositories. Configure it with "agpgart" built in. Then, don't follow the wiki. It does not get the OpenGL to work (at least for you and I). Just go to ATI's website and install the driver according to their directions (not hard at all), but make sure you uninstall the xorg-driver-fglrx package first. Maybe you can do an 'insmod agpgart' instead of compiling yourself a new kernel, but a custom kernel is the first thing I do with any Linux distro to make sure support for all my junk is built into the kernel. Then, no problems.

---

### Post by Alyus on 2006-07-27
rocketman-
I compiled a new kernel last night and am going to try reinstalling fglrx later tonight, so we'll see.  Unfortunately now running that new kernel I can't access my ntfs drive and kern.log mentions something about not loading modules.  Do you have a good guide you could reccommend on kernel compiling for dapper?

---

### Post by rocketman768 on 2006-07-27
You can google a million tutorials for a 2.6 kernel compile. But, it's pretty much as simple as this:

sudo make menuconfig
sudo make && sudo make modules_install && sudo make install

When you are configuring your kernel in menuconfig, SCOUR the options to make sure you have included the code needed by your hardware. I.e. they say [y] instead of [m] or []. This is the part most people screw up on (including me). Also, you say that you do not have ntfs support now, you can also find this in the filesystems section of menuconfig. Hope this helps! Let me know.

You say the kernel complains about loading modules? I'll bet you didn't do 'sudo make modules_install'.

Oh, btw...if you don't know what a particular module is for, when it's highlighted you can press the '?' key to get more info.

---

### Post by lemody on 2006-07-28
I think the problem is this :
------8<-------------------------
server glx vendor string: SGI
client glx vendor string: ATI
------8<-------------------------

I don't know how to get both to ATI though. Propably some symlink to some library in some place.

---

### Post by rocketman768 on 2006-07-28
The main problem is:

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Mesa is a sucky driver that does not take advantage of the capabilities of the card. This should read ATI when Alysus makes a custom kernel and uses ATI's installer.

---

### Post by rjz35 on 2006-07-28
my problem was solved after reading trough many post, most important one i think was the /usr/lib/fglrx/libGL.so.1.2  and usr/lib/fglrx/libGL.so.1.2.xlibmesa the first need to be of an older version.
I doesn't exists in the usr/lib directory.
but is works for me now.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5879 (8.26.18)

---

### Post by rjz35 on 2006-07-28
my: dmesg | grep fglrx


[17179587.960000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179587.960000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179587.960000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0
[17179600.384000] [fglrx:drm_parse_option] *ERROR* "agplock" is not a valid option
[17179600.384000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179600.388000] [fglrx] total      GART = 134217728
[17179600.392000] [fglrx] free       GART = 118226944
[17179600.392000] [fglrx] max single GART = 118226944
[17179600.392000] [fglrx] total      LFB  = 61730816
[17179600.392000] [fglrx] free       LFB  = 55439360
[17179600.392000] [fglrx] max single LFB  = 55439360
[17179600.392000] [fglrx] total      Inv  = 0
[17179600.392000] [fglrx] free       Inv  = 0
[17179600.392000] [fglrx] max single Inv  = 0
[17179600.392000] [fglrx] total      TIM  = 0

---

### Post by rjz35 on 2006-07-28
my /etc/X11/xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver		"fglrx"
   	Option       "no_accel" "no"
   	Option       "no_dri" "no"
   	Option       "DynamicClocks" "on"
   	Option       "mtrr" "on"
   	Option       "DesktopSetup" "Single"
   	Option       "ScreenOverlap" "0"
   	Option       "Capabilities" "0x00000000"
   	Option       "CapabilitiesEx" "0x00000000"
   	Option       "VideoOverlay" "on"
   	Option       "OpenGLOverlay" "off"
   	Option       "CenterMode" "off"
   	Option       "PseudoColorVisuals" "off"
   	Option       "Stereo" "off"
   	Option       "StereoSyncEnable" "1"
   	Option       "FSAAEnable" "no"
   	Option       "FSAAScale" "1"
   	Option       "FSAADisableGamma" "no"
   	Option       "FSAACustomizeMSPos" "no"
   	Option       "FSAAMSPosX0" "0.000000"
   	Option       "FSAAMSPosY0" "0.000000"
   	Option       "FSAAMSPosX1" "0.000000"
   	Option       "FSAAMSPosY1" "0.000000"
   	Option       "FSAAMSPosX2" "0.000000"
   	Option       "FSAAMSPosY2" "0.000000"
   	Option       "FSAAMSPosX3" "0.000000"
   	Option       "FSAAMSPosY3" "0.000000"
   	Option       "FSAAMSPosX4" "0.000000"
   	Option       "FSAAMSPosY4" "0.000000"
   	Option       "FSAAMSPosX5" "0.000000"
   	Option       "FSAAMSPosY5" "0.000000"
   	Option       "UseFastTLS" "0"
   	Option       "BlockSignalsOnLock" "on"
   	Option       "UseInternalAGPGART" "no"
   	Option       "ForceGenericCPU" "no"
   	Option       "KernelModuleParm" "agplock=0"
   	Option       "PowerState" "1"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


any comments, although it's working. Don't ask me why or what it all stands for.

---

### Post by Alyus on 2006-07-31
Wow!  Thanks guys for all the tips!!  I stopped getting email notices on this thread and thought it had died.. I also needed a break from this prob. as I was getting pretty frustrated.  I did the whole kernel thing and then couldn't read my ntfs partitions, then amarok got messed up and so I took a break and started with the small stuff using my old kernel.  Found a new guide and am going to try compiling a kernel again to see if i  can make it work this time.  
Thanks again it's so awesome to have all this support! I'll keep you updated.
Alyus

---

### Post by lemody on 2006-07-31
> Mesa is a sucky driver that does not take advantage of the capabilities of > the card. This should read ATI when Alysus makes a custom kernel and uses

The whole point of MESA is to be a software implementation of OpenGL .. that does not mean it's 'sucky' :) But you cannot have direct rendering with it.

---

### Post by ricesteam on 2006-07-31
I'm not sure if this will solve your problem, but I got rid of MESA by removing xserver-xorg-driver-ati and xserver-xorg-driver-all packages via apt-get.  I used the this guide [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910) to install my ATI drivers.

I'm using Ubuntu 6.06 Drapper with ATI 8.27.10 drivers for my ATI X800XT.  I successfully managed to get an XGL/Compiz session going, but I'm still testing it.

I don't have the numbers now, but I got pretty decent framerates via glxgears in my XGL session.

---

### Post by Alyus on 2006-07-31
Thank you ricesteam! I'll try that before I start trying to install the drivers again tonight.  I'm also curious to try the /libGL.so.1.2 trick rjz35 mentioned. 
I made a custom kernel (had some trouble compiling a few usb drivers but they looked unneccessary so I took them out in menuconfig) and it's up and running now with ntfs partitions being read. So we're making headway.  Only annoying thing now is that when linux is booting/loading I don't get that pretty splash screen or text until kdm starts up.  Minor detail though.  

I also thought I should mention that I use a vga=771 option in my grub menu b/c otherwise I get a scrambled screen. Hopefully that wasn't a vital detail I left out earlier!!  I'll get back to you guys after I install the fglrx drivers from ati (I have the installer make deb's so I can remove it easily if I have t)
Muchos gracias

p.s. if anyone is familiar with kernel compiling with nforce3 motherboards could tell me if I should have compiled nvidia-kernel-source while doing kernel compile that would be great! I did not b/c from what I could figure out it looked only important to do if you use a nvidia gfx card.

---

### Post by Alyus on 2006-08-01
Yea! I think I'm in business.  The GlxGears are finally spinning!  One last question before I get too excited.  
After I select my custom kernel in grub my screen goes blank until kdm starts.  If I hit ctrl-alt-(f1-5) i get a blank screen also. Is there anyway to get my console display working again?
I'll post my outputs again if necessary.  Thanks!

Alyus

---

### Post by Alyus on 2006-08-01
Alright here are my results:

GlxGears average fps~ 530. (seems slow for a 9800pro but at least those little gears are spinning finally!)

demsg | grep fglrx
```

[4294693.710000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294693.712000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[4294693.712000] [fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
[4294694.773000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294694.773000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294694.773000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[4294694.773000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294694.783000] [fglrx] total      GART = 134217728
[4294694.783000] [fglrx] free       GART = 118222848
[4294694.783000] [fglrx] max single GART = 118222848
[4294694.783000] [fglrx] total      LFB  = 130117632
[4294694.783000] [fglrx] free       LFB  = 126095360
[4294694.783000] [fglrx] max single LFB  = 126095360
[4294694.783000] [fglrx] total      Inv  = 0
[4294694.783000] [fglrx] free       Inv  = 0
[4294694.783000] [fglrx] max single Inv  = 0
[4294694.783000] [fglrx] total      TIM  = 0
[4294973.174000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294973.174000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294973.174000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[4294973.175000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294973.185000] [fglrx] total      GART = 134217728
[4294973.185000] [fglrx] free       GART = 118222848
[4294973.185000] [fglrx] max single GART = 118222848
[4294973.185000] [fglrx] total      LFB  = 130117632
[4294973.185000] [fglrx] free       LFB  = 126095360
[4294973.185000] [fglrx] max single LFB  = 126095360
[4294973.185000] [fglrx] total      Inv  = 0
[4294973.185000] [fglrx] free       Inv  = 0
[4294973.185000] [fglrx] max single Inv  = 0
[4294973.185000] [fglrx] total      TIM  = 0
[4299346.381000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4299346.381000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4299346.381000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[4299346.381000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4299346.392000] [fglrx] total      GART = 134217728
[4299346.392000] [fglrx] free       GART = 118222848
[4299346.392000] [fglrx] max single GART = 118222848
[4299346.392000] [fglrx] total      LFB  = 130117632
[4299346.392000] [fglrx] free       LFB  = 126095360
[4299346.392000] [fglrx] max single LFB  = 126095360
[4299346.392000] [fglrx] total      Inv  = 0
[4299346.392000] [fglrx] free       Inv  = 0
[4299346.392000] [fglrx] max single Inv  = 0
[4299346.392000] [fglrx] total      TIM  = 0

```

GlxInfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5946 (8.27.10)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

```

The openGl screensavers don't work, but I'm just happy to be making progress!  Any comments / suggestions are appreciated and thank you guys so much for getting me this far!

Alyus

---

### Post by Dubbayoo on 2006-08-01
Here are my results with a Radeon 8500, which is about 3-4 years old?
I believe the driver version is 8.26.18-1

steve@ubu:/data/shared_files$ **glxgears**
14558 frames in 5.0 seconds = 2911.442 FPS
14590 frames in 5.0 seconds = 2917.855 FPS
14589 frames in 5.0 seconds = 2917.687 FPS
14590 frames in 5.0 seconds = 2917.822 FPS
14590 frames in 5.0 seconds = 2917.834 FPS
steve@ubu:/data/shared_files$ **fgl_glxgears**
Using GLX_SGIX_pbuffer
2053 frames in 5.0 seconds = 410.600 FPS
2137 frames in 5.0 seconds = 427.400 FPS
2134 frames in 5.0 seconds = 426.800 FPS
2147 frames in 5.0 seconds = 429.400 FPS
2144 frames in 5.0 seconds = 428.800 FPS


steve@ubu:/media$  **fglrxinfo**
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 DDR Generic
OpenGL version string: 1.3.1080 (X4.3.0-8.26.6)


**This is my xorg.conf file:**

> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "false"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Viewsonic pf790"
	DisplaySize  364	275
	HorizSync    30.0 - 97.0
	VertRefresh  50.0 - 160.0
	ModeLine     "1600x1200@75" 245.7 1600 1632 2560 2592 1200 1223 1238 1261
	ModeLine     "1400x1050@75" 176.6 1400 1432 2096 2128 1050 1070 1083 1103
	ModeLine     "1280x960@75" 142.8 1280 1312 1848 1880 960 978 990 1009
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	ModeLine     "1600x1200@75" 245.7 1600 1632 2560 2592 1200 1223 1238 1261
	ModeLine     "1400x1050@75" 176.6 1400 1432 2096 2128 1050 1070 1083 1103
	ModeLine     "1280x960@75" 142.8 1280 1312 1848 1880 960 978 990 1009
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	203	# 1280x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	318	# 1600x1200 96dpi
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R200 QL [Radeon 8500 LE]"
	Driver      "fglrx"
	VideoRam    131072
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	VideoRam    131072
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R200 QL [Radeon 8500 LE]"
	Monitor    "Viewsonic pf790"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1400x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1400x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1400x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1400x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1400x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1400x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1400x1050" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



---

### Post by Alyus on 2006-08-01
Wow!! Okay so my 530fps is obviously very slow. Any ideas on what to tweak next?

Right now I'm trying to recompile a kernel from kernel.org
The line:
```

[4294973.174000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294973.174000] [fglrx] Have to use kernel AGP support to avoid conflicts.

```

was sticking out at me.I'm going to try configuring this kernel without AGP (hopefully some option will stick out to me-maybe it will be a load AGP from module or something...)  any other ideas or am I going down the wrong path here??

thanks!
Alyus

---

### Post by Alyus on 2006-08-02
Ugh... So frustrated.  Still getting the same error with dmesg | grep fglrx, and now I cannot read ntfs (or any drive but the booting one).  On the positive I got my fps up to 1000. Still not where it seems it should be, but better.  The ntfs thing is crucial though (all my media is on a ntfs partition).  It's late and I've been at this for pretty close to a day solid (recompiling etc.)

Heres the dmesg | grep ata

```

Memory: 1030956k/1048320k available (1853k kernel code, 16572k reserved, 570k data, 220k init, 130816k highmem)
libata version 1.20 loaded.
sata_nv 0000:00:0a.0: version 0.8
ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD000 irq 177
ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD008 irq 177
ata1: SATA link up 1.5 Gbps (SStatus 113)
ata1: dev 0 cfg 49:2f00 82:74eb 83:7fea 84:4023 85:74e9 86:3c02 87:4023 88:203f
ata1: dev 0 ATA-6, max UDMA/100, 488397168 sectors: LBA48
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device removed
ata1: dev 0 configured for UDMA/100
scsi0 : sata_nv
ata2: SATA link down (SStatus 0)
scsi1 : sata_nv
sata_sil 0000:02:0c.0: version 0.9
ata3: SATA max UDMA/100 cmd 0xF8856880 ctl 0xF885688A bmdma 0xF8856800 irq 185
ata4: SATA max UDMA/100 cmd 0xF88568C0 ctl 0xF88568CA bmdma 0xF8856808 irq 185
ata5: SATA max UDMA/100 cmd 0xF8856A80 ctl 0xF8856A8A bmdma 0xF8856A00 irq 185
ata6: SATA max UDMA/100 cmd 0xF8856AC0 ctl 0xF8856ACA bmdma 0xF8856A08 irq 185
ata3: SATA link down (SStatus 0)
scsi2 : sata_sil
ata4: SATA link down (SStatus 0)
scsi3 : sata_sil
ata5: SATA link down (SStatus 0)
scsi4 : sata_sil
ata6: SATA link down (SStatus 0)
scsi5 : sata_sil
EXT3-fs: mounted filesystem with ordered data mode.

```

Just in case someone has experience like this.  Otherwise I'll retry compiling the kernel, but this time from the repo's, with the same options and see if that gives me the same fps, while still letting me have my ntfs partitions...

---

### Post by Alyus on 2006-08-02
I give up. :confused:  I've tried compiling the kernel a bunch of different ways (with agpgart loaded as a module, not loaded as module, part of kernel...vanilla kernels, kernels from repo's)  and I still cant get a decent fps w/glxgears and ntfs working. (Ntfs wasnt happening with vanilla kernel from kernel.org even with ntfs selected as compile in kernel and compile as module, and glxgears was still slow).  I've been installing the ati drivers with the script from ati rather than making .deb's because that wasn't working either.

I also tried uninstalling xserver-xorg-drivers-all (& ati) before installing ati... and other random suggestions I've found through google..

I didn't try the library replacement because I have no idea where to get the appropriate file and if I remember correctly that was a solution for the amd_64 kernel's. And I have no idea how to deal with that problem of mismatched glx server/client's either.

Here's the output from various commands while running the last kernel I compiled and ati's driver installed.

dmesg | grep agp
```

Linux agpgart interface v0.101 (c) Dave Jones

```

dmesg | grep fglrx
```

fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
[fglrx] Internal AGP is not supported in 2.6 kernel.
[fglrx:firegl_unlock] *ERROR* Process 4738 using kernel context 0

```

lsmod
```

Module                  Size  Used by
fglrx                 387756  0
agpgart                29000  1 fglrx
ppdev                   8068  0
ipv6                  247360  6
cpufreq_userspace       3736  0
cpufreq_stats           4420  0
freq_table              3460  1 cpufreq_stats
cpufreq_powersave       1472  0
cpufreq_ondemand        5404  0
cpufreq_conservative     6372  0
video                  14084  0
tc1100_wmi              5188  0
sony_acpi               4172  0
pcc_acpi               10240  0
hotkey                  9380  0
dev_acpi                8836  0
container               3136  0
button                  4816  0
acpi_sbs               18124  0
battery                 7748  1 acpi_sbs
ac                      3524  1 acpi_sbs
i2c_acpi_ec             4032  1 acpi_sbs
nls_utf8                1664  1
nls_cp437               5440  2
ntfs                  103984  3
af_packet              17032  2
dm_mod                 51896  1
md_mod                 60628  0
sr_mod                 14244  0
cdrom                  37984  1 sr_mod
sbp2                   21380  0
lp                      9476  0
psmouse                36420  0
serio_raw               5764  0
3c59x                  41064  0
mii                     4928  1 3c59x
parport_pc             32900  1
parport                33736  3 ppdev,lp,parport_pc
snd_mpu401              5192  0
snd_mpu401_uart         5888  1 snd_mpu401
usbhid                 37728  0
floppy                 57476  0
snd_rawmidi            20320  1 snd_mpu401_uart
snd_seq_device          7116  1 snd_rawmidi
snd_intel8x0           30044  2
snd_ac97_codec         94688  1 snd_intel8x0
snd_ac97_bus            1792  1 snd_ac97_codec
rtc                     9908  0
snd_pcm_oss            49824  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                80392  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              20612  1 snd_pcm
analog                 10464  0
gameport               11208  1 analog
pcspkr                  1476  0
shpchp                 43776  0
pci_hotplug            24692  1 shpchp
snd                    46692  14 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               7328  1 snd
snd_page_alloc          8584  2 snd_intel8x0,snd_pcm
i2c_nforce2             5696  0
evdev                   7680  0
sg                     34336  0
ext3                  122120  2
jbd                    49492  1 ext3
ide_generic             1024  0
ohci1394               31988  0
ieee1394              290744  2 sbp2,ohci1394
ehci_hcd               28488  0
ohci_hcd               18820  0
usbcore               116804  4 usbhid,ehci_hcd,ohci_hcd
sata_sil                6468  0
ide_disk               15424  3
generic                 4164  0
sd_mod                 15184  5
amd74xx                13916  0 [permanent]
sata_nv                 6788  8
libata                 71504  2 sata_sil,sata_nv
scsi_mod              124968  5 sr_mod,sbp2,sg,sd_mod,libata
thermal                10824  0
processor              18688  1 thermal
fan                     3268  0
vga16fb                12232  0
cfbcopyarea             3520  1 vga16fb
vgastate                9088  1 vga16fb
cfbimgblt               2624  1 vga16fb
cfbfillrect             3648  1 vga16fb

```

kern.log
```

Aug  2 20:01:05 dvine kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug  2 20:02:01 dvine kernel: Loaded 19966 symbols from /boot/System.map-2.6.15.7-ubuntu1-kustom4.
Aug  2 20:02:01 dvine kernel: Symbols match kernel version 2.6.15.
Aug  2 20:02:01 dvine kernel: No module symbols loaded - kernel modules not enabled. 
Aug  2 20:02:01 dvine kernel: sable)
Aug  2 20:02:01 dvine kernel: Console: colour VGA+ 80x25
Aug  2 20:02:01 dvine kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug  2 20:02:01 dvine kernel: mtrr: v2.0 (20020519)
Aug  2 20:02:01 dvine kernel: CPU: AMD Athlon(tm) 64 Processor 3000+ stepping 00
Aug  2 20:02:01 dvine kernel: Boot video device is 0000:01:00.0
Aug  2 20:02:01 dvine kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Aug  2 20:02:01 dvine kernel: pnp: PnP ACPI init
Aug  2 20:02:01 dvine kernel: pnp: PnP ACPI: found 14 devices
Aug  2 20:02:01 dvine kernel: PnPBIOS: Disabled by ACPI PNP
Aug  2 20:02:01 dvine kernel: PCI: Using ACPI for IRQ routing
Aug  2 20:02:01 dvine kernel: PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug  2 20:02:01 dvine kernel: vga16fb: initializing
Aug  2 20:02:01 dvine kernel: vga16fb: mapped to 0xc00a0000
Aug  2 20:02:01 dvine kernel: fb0: VGA16 VGA frame buffer device
Aug  2 20:02:01 dvine kernel: ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD000 irq 177
Aug  2 20:02:01 dvine kernel: ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD008 irq 177
Aug  2 20:02:01 dvine kernel: ata1: dev 0 cfg 00:045a 49:2f00 82:74eb 83:7fea 84:4023 85:74e9 86:3c02 87:4023 88:203f 93:0000
Aug  2 20:02:01 dvine kernel: ata1: dev 0 ATA-6, max UDMA/100, 488397168 sectors: LBA48
Aug  2 20:02:01 dvine kernel: sata_get_dev_handle: SATA dev addr=0xa0000, handle=0xdffe73e0
Aug  2 20:02:01 dvine kernel: nv_sata: Primary device added
Aug  2 20:02:01 dvine kernel: nv_sata: Primary device removed
Aug  2 20:02:01 dvine kernel: nv_sata: Secondary device removed
Aug  2 20:02:01 dvine kernel: ata1: dev 0 configured for UDMA/100
Aug  2 20:02:01 dvine kernel: sata_get_dev_handle: SATA dev addr=0xa0000, handle=0xdffe73e0
Aug  2 20:02:01 dvine kernel: scsi0 : sata_nv
Aug  2 20:02:01 dvine kernel: ata2: no device found (phy stat 00000000)
Aug  2 20:02:01 dvine kernel: scsi1 : sata_nv
Aug  2 20:02:01 dvine kernel:   Vendor: ATA       Model: HDS722525VLSA80   Rev: V36O
Aug  2 20:02:01 dvine kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
Aug  2 20:02:01 dvine kernel: NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
Aug  2 20:02:01 dvine kernel: NFORCE3-250: chipset revision 162
Aug  2 20:02:01 dvine kernel: NFORCE3-250: not 100%% native mode: will probe irqs later
Aug  2 20:02:01 dvine kernel: NFORCE3-250: BIOS didn't set cable bits correctly. Enabling workaround.
Aug  2 20:02:01 dvine kernel: NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
Aug  2 20:02:01 dvine kernel:     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
Aug  2 20:02:01 dvine kernel:     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
Aug  2 20:02:01 dvine kernel: Probing IDE interface ide0...
Aug  2 20:02:01 dvine kernel: Driver 'sd' needs updating - please use bus_type methods
Aug  2 20:02:01 dvine kernel: SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Aug  2 20:02:01 dvine kernel: SCSI device sda: drive cache: write back
Aug  2 20:02:01 dvine kernel: SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
Aug  2 20:02:01 dvine kernel: SCSI device sda: drive cache: write back
Aug  2 20:02:01 dvine kernel:  sda: sda1 sda2 < sda5 sda6 sda7 >
Aug  2 20:02:01 dvine kernel: sd 0:0:0:0: Attached scsi disk sda
Aug  2 20:02:01 dvine kernel: hda: SAMSUNG SP1614N, ATA DISK drive
Aug  2 20:02:01 dvine kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Aug  2 20:02:01 dvine kernel: Probing IDE interface ide1...
Aug  2 20:02:01 dvine kernel: hda: max request size: 1024KiB
Aug  2 20:02:01 dvine kernel: hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(100)
Aug  2 20:02:01 dvine kernel: hda: cache flushes supported
Aug  2 20:02:01 dvine kernel:  hda: hda1 hda2 < hda5 >
Aug  2 20:02:01 dvine kernel: sata_sil 0000:02:0c.0: version 0.9
Aug  2 20:02:01 dvine kernel: **** SET: Misaligned resource pointer: dfb84c42 Type 07 Len 0
Aug  2 20:02:01 dvine kernel: ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19
Aug  2 20:02:01 dvine kernel: ACPI: PCI Interrupt 0000:02:0c.0[A] -> Link [LNKC] -> GSI 19 (level, low) -> IRQ 185
Aug  2 20:02:01 dvine kernel: usbcore: registered new driver usbfs
Aug  2 20:02:01 dvine kernel: usbcore: registered new driver hub
Aug  2 20:02:01 dvine kernel: ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Aug  2 20:02:01 dvine kernel: **** SET: Misaligned resource pointer: dfb84942 Type 07 Len 0
Aug  2 20:02:01 dvine kernel: ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
Aug  2 20:02:01 dvine kernel: ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 21 (level, low) -> IRQ 193
Aug  2 20:02:01 dvine kernel: PCI: Setting latency timer of device 0000:00:02.0 to 64
Aug  2 20:02:01 dvine kernel: i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
Aug  2 20:02:01 dvine kernel: i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5040
Aug  2 20:02:01 dvine kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  2 20:02:01 dvine kernel: shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  2 20:02:01 dvine kernel: input: PC Speaker as /class/input/input0
Aug  2 20:02:01 dvine kernel: Real Time Clock Driver v1.12
Aug  2 20:02:01 dvine kernel: **** SET: Misaligned resource pointer: df863542 Type 07 Len 0
Aug  2 20:02:01 dvine kernel: ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 21
Aug  2 20:02:01 dvine kernel: ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LAUI] -> GSI 21 (level, low) -> IRQ 193
Aug  2 20:02:01 dvine kernel: PCI: Setting latency timer of device 0000:00:06.0 to 64
Priority:-1 extents:1 across:1004020k
Aug  2 20:02:01 dvine kernel: EXT3 FS on sda1, internal journal
Aug  2 20:02:01 dvine kernel: md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Aug  2 20:02:01 dvine kernel: md: bitmap version 4.39
Aug  2 20:02:01 dvine kernel: device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
Aug  2 20:02:01 dvine kernel: NET: Registered protocol family 17
Aug  2 20:02:01 dvine kernel: kjournald starting.  Commit interval 5 seconds
Aug  2 20:02:01 dvine kernel: EXT3 FS on sda6, internal journal
Aug  2 20:02:01 dvine kernel: EXT3-fs: mounted filesystem with ordered data mode.
Aug  2 20:02:01 dvine kernel: NTFS driver 2.1.25 [Flags: R/O MODULE].
Aug  2 20:02:01 dvine kernel: NTFS volume version 3.1.
Aug  2 20:02:01 dvine last message repeated 2 times
Aug  2 20:02:01 dvine kernel: ACPI: Power Button (FF) [PWRF]
Aug  2 20:02:01 dvine kernel: ACPI: Power Button (CM) [PWRB]
Aug  2 20:02:01 dvine kernel: ibm_acpi: ec object not found
Aug  2 20:02:01 dvine kernel: pcc_acpi: loading...
Aug  2 20:02:01 dvine kernel: powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
Aug  2 20:02:01 dvine kernel: powernow-k8: BIOS error - no PSB or ACPI _PSS objects
Aug  2 20:02:02 dvine kernel: NET: Registered protocol family 10
Aug  2 20:02:02 dvine kernel: lo: Disabled Privacy Extensions
Aug  2 20:02:02 dvine kernel: IPv6 over IPv4 tunneling driver
Aug  2 20:02:02 dvine kernel: ppdev: user-space parallel port driver
Aug  2 20:02:03 dvine kernel: apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug  2 20:02:03 dvine kernel: apm: overridden by ACPI.
Aug  2 20:02:08 dvine kernel: Linux agpgart interface v0.101 (c) Dave Jones
Aug  2 20:02:08 dvine kernel: fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Aug  2 20:02:08 dvine kernel: [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Aug  2 20:02:08 dvine kernel: [fglrx] module loaded - fglrx 8.27.10 [Jul 27 2006] on minor 0
Aug  2 20:02:08 dvine kernel: **** SET: Misaligned resource pointer: f7f0ea82 Type 07 Len 0
Aug  2 20:02:08 dvine kernel: ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 17
Aug  2 20:02:08 dvine kernel: ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 17 (level, low) -> IRQ 217
Aug  2 20:02:12 dvine kernel: [fglrx] Internal AGP is not supported in 2.6 kernel.
Aug  2 20:02:12 dvine kernel: [fglrx:firegl_unlock] *ERROR* Process 4738 using kernel context 0
Aug  2 20:02:13 dvine kernel: eth0: no IPv6 routers present

```

glxinfo
```

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```

I'd be happy to run one of the standard kernels and post the results of those as well if anyone is still willing to help and has any fresh ideas.

I am at my wit's end, or perhaps my wit ended a long time ago and I'm just at the end of my patience.  The gears don't even spin now, and I probably should take a shower!

Thanks everyone for trying.

Alyus

---

### Post by ricesteam on 2006-08-03
Alyus, have you tried reinstalling Dapper?

I don't think I had to recompile the kernel to get Ati acceleration going.  In my Xorg.conf, my AGP ATI is recognized as "PCI:1:0:0"

---

### Post by Alyus on 2006-08-03
I haven't reinstalled dapper yet. I'm not looking foreward to reinstalling all my special stuff (icewm & customizations, multimedia codec's, dvd stuff, etc etc)

I gues what was really getting me in customizing the kernel was the  agpgart part (just leave it as a module or compile it in kernel or leave it out altogeather) and there was two other places I found radeon (under rendering and under grafics something or another) that I had similar uncertainty.  

Sorry I can't be more specific, I'm away from my ubuntu machine..

---

