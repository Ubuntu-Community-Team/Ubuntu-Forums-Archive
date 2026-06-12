---
title: "No GLX on Natty with Intel Mobile GM965/GL960 Integrated Graphics Controller"
date: 2011-09-14
forum: Multimedia Software
---

### Post by Cryoraptor on 2011-09-14
Seems similar to this [thread]("http://ubuntuforums.org/showthread.php?t=809059"), but for 11.04 Natty.

I get this error when running MineCraft:
```
--- BEGIN ERROR REPORT a1dce528 --------
Generated 9/14/11 8:39 PM

Minecraft: Minecraft Beta 1.8
OS: Linux (amd64) version 2.6.38-11-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:233)
	at net.minecraft.client.Minecraft.run(SourceFile:629)
	at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 6e4c7b2b ----------

```

When I run lspci | grep -i gm -
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)

```

And, glxinfo | grep direct -
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Any ideas on how to troubleshoot, install, and configure GLX? I'm running 64-bit Ubuntu 11.04. I've spent a while on this, and keep running in circles.

Thanks!

---

### Post by BicyclerBoy on 2011-09-15
glxinfo | grep OpenGL

post your log so can see what video driver you're running
/var/log/Xorg.0.log

Have you added any launchpad ppa for later intel i915 drivers ?

---

### Post by Cryoraptor on 2011-09-15
I get the same message as one I posted already.

```

sheridan@guy-laptop:~$ glxinfo | grep OpenGL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
sheridan@guy-laptop:~$ 

Here's the log:

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux guy-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.99.log", Time: Fri May  8 11:21:39 2009
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 10

(--) PCI:*(0@0:2:0) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000efe8/8
List of video drivers:
	siliconmotion
	mga
	vmware
	v4l
	trident
	apm
	radeon
	sisusb
	i128
	ati
	mach64
	openchrome
	sis
	cirrus
	dummy
	s3
	intel
	i810
	s3virge
	tseng
	voodoo
	savage
	glint
	nv
	neomagic
	r128
	ark
	chips
	tdfx
	rendition
	fbdev
	vesa
(II) LoadModule: "siliconmotion"
(II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.7.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.4.9
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vmware"
(II) Loading /usr/lib/xorg/modules/drivers//vmware_drv.so
(II) Module vmware: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 10.16.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 0.1.1
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "apm"
(II) Loading /usr/lib/xorg/modules/drivers//apm_drv.so
(II) Module apm: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "sisusb"
(II) Loading /usr/lib/xorg/modules/drivers//sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i128"
(II) Loading /usr/lib/xorg/modules/drivers//i128_drv.so
(II) Module i128: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.3.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "mach64"
(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.5.99.902, module version = 0.2.903
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "cirrus"
(II) Loading /usr/lib/xorg/modules/drivers//cirrus_drv.so
(II) Module cirrus: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "dummy"
(II) Loading /usr/lib/xorg/modules/drivers//dummy_drv.so
(II) Module dummy: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.3.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "s3"
(II) Loading /usr/lib/xorg/modules/drivers//s3_drv.so
(II) Module s3: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.6.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.6.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) UnloadModule: "i810"
(II) Unloading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Failed to load module "i810" (already loaded, 0)
(II) LoadModule: "s3virge"
(II) Loading /usr/lib/xorg/modules/drivers//s3virge_drv.so
(II) Module s3virge: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.10.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "tseng"
(II) Loading /usr/lib/xorg/modules/drivers//tseng_drv.so
(II) Module tseng: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "voodoo"
(II) Loading /usr/lib/xorg/modules/drivers//voodoo_drv.so
(II) Module voodoo: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "savage"
(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "glint"
(II) Loading /usr/lib/xorg/modules/drivers//glint_drv.so
(II) Module glint: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.2.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.12
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "neomagic"
(II) Loading /usr/lib/xorg/modules/drivers//neomagic_drv.so
(II) Module neomagic: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.2.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "ark"
(II) Loading /usr/lib/xorg/modules/drivers//ark_drv.so
(II) Module ark: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.7.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "chips"
(II) Loading /usr/lib/xorg/modules/drivers//chips_drv.so
(II) Module chips: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "tdfx"
(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.4.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "rendition"
(II) Loading /usr/lib/xorg/modules/drivers//rendition_drv.so
(II) Module rendition: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for siliconmotion
(WW) Falling back to old probe method for v4l
(II) v4l driver for Video4Linux
(WW) Falling back to old probe method for trident
(WW) Falling back to old probe method for apm
(WW) Falling back to old probe method for sisusb
(WW) Falling back to old probe method for i128
(WW) Falling back to old probe method for sis
(WW) Falling back to old probe method for cirrus
(II) Loading sub module "cirrus_laguna"
(II) LoadModule: "cirrus_laguna"
(II) Loading /usr/lib/xorg/modules/drivers//cirrus_laguna.so
(II) Module cirrus_laguna: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "cirrus_alpine"
(II) LoadModule: "cirrus_alpine"
(II) Loading /usr/lib/xorg/modules/drivers//cirrus_alpine.so
(II) Module cirrus_alpine: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(WW) Falling back to old probe method for dummy
(WW) Falling back to old probe method for s3
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(WW) Falling back to old probe method for s3virge
(WW) Falling back to old probe method for tseng
(WW) Falling back to old probe method for voodoo
(WW) Falling back to old probe method for glint
(WW) Falling back to old probe method for neomagic
(WW) Falling back to old probe method for ark
(II) FBDEV: driver for framebuffer: fbdev
(II) VESA: driver for VESA chipsets: vesa
(++) Using config file: "/xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
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
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

```

Xorg detected your mouse at device /dev/input/mice.
Please check your config if the mouse is still not
operational, as by default Xorg tries to autodetect
the protocol.

Your xorg.conf file is /xorg.conf.new

To test the server, run 'X -config /xorg.conf.new'

 ddxSigGiveUp: Closing log

Sorry if it takes a while to read it. 
What does Launchpad PPA mean? Because I probably haven't.
Thanks for the quick reply though, I posted this last night!

---

### Post by BicyclerBoy on 2011-09-15
Your kernel version & Xorg etc are older than that used by lucid 10.04.3 LTS....

Are you** sure** this file is the latest (by date) in /var/log/Xorg* ?? It looks 2 years old...

It looks to me that the vesa driver takes control.
The intel driver indicated is i810, should be i915.

---

### Post by jago25_98 on 2011-10-21
I have the same problem. Using "intel" driver, no GLX. Everything should be spanking new. 
GLX loads, dri & dri2 load without issues. Perhaps the libraries think they're NVidia? 

```
Xlib:  extension "NV-GLX" missing on display ":0.0".
Xlib:  extension "NV-GLX" missing on display ":0.0".
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

```
j@laptop:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
Xlib:  extension "NV-GLX" missing on display ":0.0".
Xlib:  extension "NV-GLX" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_fbconfig_packed_float, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_NV_present_video, GLX_NV_copy_image, GLX_NV_multisample_coverage, 
    GLX_NV_video_capture, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness
GLX version: 1.4
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGI_swap_control, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_ARB_get_proc_address
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM x86/MMX/SSE2
OpenGL version string: 1.4 (2.1 Mesa 7.11)
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_texture3D, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_ARB_multitexture, GL_IBM_texture_mirrored_repeat, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_dot3, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_ARB_depth_texture, GL_ARB_occlusion_query, GL_ARB_shadow, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_EXT_stencil_two_side, GL_NV_depth_clamp, 
    GL_NV_vertex_program1_1, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_vertex_program, GL_ATI_draw_buffers, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_wrap, GL_ARB_fragment_program_shadow, GL_ARB_point_sprite, 
    GL_ARB_texture_non_power_of_two, GL_EXT_blend_equation_separate, 
    GL_EXT_texture_env_combine

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x098 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x071  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x072 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x076  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x078  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x083 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x089  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow


```

> 'nvidia-common' is installed to find obsolete versions of the Nvidia driver that could possibly cause problems.

It's quite necessary to prevent breakage on some people's systems, and takes up all of 188 kilobytes. If you had a 20MB HDD it would be a bit of a nuisance, but then you wouldn't be running Ubuntu on a disk that small.
^ from [http://ubuntuforums.org/showthread.php?t=1789376](http://ubuntuforums.org/showthread.php?t=1789376)


```
[  4174.412] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  4174.417] X Protocol Version 11, Revision 0
[  4174.419] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  4174.421] Current Operating System: Linux laptop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[  4174.423] Kernel command line: BOOT_IMAGE=/vmlinuz root=/dev/sda8
[  4174.425] Build Date: 29 September 2011  12:48:48AM
[  4174.427] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[  4174.429] Current version of pixman: 0.22.2
[  4174.431] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  4174.434] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  4174.441] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 21 16:38:57 2011
[  4174.443] (==) Using config file: "/etc/X11/xorg.conf"
[  4174.445] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  4174.447] (==) ServerLayout "X.org Configured"
[  4174.447] (**) |-->Screen "Screen0" (0)
[  4174.447] (**) |   |-->Monitor "Monitor0"
[  4174.447] (**) |   |-->Device "Card0"
[  4174.447] (==) Automatically adding devices
[  4174.447] (==) Automatically enabling devices
[  4174.448] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  4174.448] 	Entry deleted from font path.
[  4174.448] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  4174.448] 	Entry deleted from font path.
[  4174.448] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  4174.448] (**) ModulePath set to "/usr/lib/xorg/modules"
[  4174.448] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  4174.448] (II) Loader magic: 0x823ada0
[  4174.448] (II) Module ABI versions:
[  4174.448] 	X.Org ANSI C Emulation: 0.4
[  4174.448] 	X.Org Video Driver: 10.0
[  4174.448] 	X.Org XInput driver : 12.3
[  4174.448] 	X.Org Server Extension : 5.0
[  4174.449] (--) PCI:*(0:0:2:0) 8086:2a02:1028:0228 rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000efe8/8
[  4174.449] (--) PCI: (0:0:2:1) 8086:2a03:1028:0228 rev 12, Mem @ 0xfeb00000/1048576
[  4174.450] (II) Open ACPI successful (/var/run/acpid.socket)
[  4174.450] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[  4174.450] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[  4174.450] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  4174.450] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[  4174.450] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[  4174.450] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[  4174.450] (II) LoadModule: "dri2"
[  4174.450] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  4174.450] (II) Module dri2: vendor="X.Org Foundation"
[  4174.450] 	compiled for 1.10.4, module version = 1.2.0
[  4174.450] 	ABI class: X.Org Server Extension, version 5.0
[  4174.450] (II) Loading extension DRI2
[  4174.450] (II) LoadModule: "extmod"
[  4174.451] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  4174.451] (II) Module extmod: vendor="X.Org Foundation"
[  4174.451] 	compiled for 1.10.4, module version = 1.0.0
[  4174.451] 	Module class: X.Org Server Extension
[  4174.451] 	ABI class: X.Org Server Extension, version 5.0
[  4174.451] (II) Loading extension MIT-SCREEN-SAVER
[  4174.451] (II) Loading extension XFree86-VidModeExtension
[  4174.451] (II) Loading extension XFree86-DGA
[  4174.451] (II) Loading extension DPMS
[  4174.451] (II) Loading extension XVideo
[  4174.451] (II) Loading extension XVideo-MotionCompensation
[  4174.451] (II) Loading extension X-Resource
[  4174.451] (II) LoadModule: "record"
[  4174.451] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  4174.452] (II) Module record: vendor="X.Org Foundation"
[  4174.452] 	compiled for 1.10.4, module version = 1.13.0
[  4174.452] 	Module class: X.Org Server Extension
[  4174.452] 	ABI class: X.Org Server Extension, version 5.0
[  4174.452] (II) Loading extension RECORD
[  4174.452] (II) LoadModule: "glx"
[  4174.452] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  4174.452] (II) Module glx: vendor="X.Org Foundation"
[  4174.452] 	compiled for 1.10.4, module version = 1.0.0
[  4174.452] 	ABI class: X.Org Server Extension, version 5.0
[  4174.452] (==) AIGLX enabled
[  4174.452] (II) Loading extension GLX
[  4174.452] (II) LoadModule: "dbe"
[  4174.453] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  4174.453] (II) Module dbe: vendor="X.Org Foundation"
[  4174.453] 	compiled for 1.10.4, module version = 1.0.0
[  4174.453] 	Module class: X.Org Server Extension
[  4174.453] 	ABI class: X.Org Server Extension, version 5.0
[  4174.453] (II) Loading extension DOUBLE-BUFFER
[  4174.453] (II) LoadModule: "dri"
[  4174.453] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  4174.453] (II) Module dri: vendor="X.Org Foundation"
[  4174.453] 	compiled for 1.10.4, module version = 1.0.0
[  4174.453] 	ABI class: X.Org Server Extension, version 5.0
[  4174.453] (II) Loading extension XFree86-DRI
[  4174.453] (II) LoadModule: "intel"
[  4174.453] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4174.454] (II) Module intel: vendor="X.Org Foundation"
[  4174.454] 	compiled for 1.10.2.902, module version = 2.15.901
[  4174.454] 	Module class: X.Org Video Driver
[  4174.454] 	ABI class: X.Org Video Driver, version 10.0
[  4174.454] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[  4174.454] (--) using VT number 8

[  4174.464] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  4174.464] drmOpenDevice: node name is /dev/dri/card0
[  4174.464] drmOpenDevice: open result is 9, (OK)
[  4174.464] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  4174.464] drmOpenDevice: node name is /dev/dri/card0
[  4174.464] drmOpenDevice: open result is 9, (OK)
[  4174.464] drmOpenByBusid: drmOpenMinor returns 9
[  4174.464] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  4174.464] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  4174.464] (==) intel(0): RGB weight 888
[  4174.465] (==) intel(0): Default visual is TrueColor
[  4174.465] (**) intel(0): Option "DRI" "true"
[  4174.465] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[  4174.465] (--) intel(0): Chipset: "965GM"
[  4174.465] (**) intel(0): Relaxed fencing enabled
[  4174.465] (**) intel(0): Wait on SwapBuffers? enabled
[  4174.465] (**) intel(0): Triple buffering? enabled
[  4174.465] (**) intel(0): Framebuffer tiled
[  4174.465] (**) intel(0): Pixmaps tiled
[  4174.465] (**) intel(0): 3D buffers tiled
[  4174.465] (**) intel(0): SwapBuffers wait enabled
[  4174.465] (==) intel(0): video overlay key set to 0x101fe
[  4174.465] (II) intel(0): Output LVDS1 using monitor section Monitor0
[  4174.467] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[  4174.488] (II) intel(0): Output VGA1 has no monitor section
[  4174.827] (II) intel(0): Output TV1 has no monitor section
[  4174.828] (II) intel(0): EDID for output LVDS1
[  4174.828] (II) intel(0): Manufacturer: CPT  Model: 141f  Serial#: 0
[  4174.828] (II) intel(0): Year: 2008  Week: 16
[  4174.828] (II) intel(0): EDID Version: 1.3
[  4174.828] (II) intel(0): Digital Display Input
[  4174.828] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[  4174.828] (II) intel(0): Gamma: 2.20
[  4174.828] (II) intel(0): No DPMS capabilities specified
[  4174.828] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  4174.828] (II) intel(0): First detailed timing is preferred mode
[  4174.828] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[  4174.828] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[  4174.828] (II) intel(0): Manufacturer's mask: 0
[  4174.828] (II) intel(0): Supported detailed timing:
[  4174.828] (II) intel(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[  4174.828] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1450 h_border: 0
[  4174.828] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[  4174.828] (II) intel(0): Unknown vendor-specific block f
[  4174.828] (II) intel(0):  TM1210154WB8
[  4174.828] (II) intel(0):  '6AGd&#130;«ÿ
[  4174.828] (II) intel(0): EDID (in hex):
[  4174.828] (II) intel(0): 	00ffffffffffff000e141f1400000000
[  4174.828] (II) intel(0): 	10120103802115780a092d9d564f9027
[  4174.828] (II) intel(0): 	21505400000001010101010101010101
[  4174.828] (II) intel(0): 	010101010101bc1b00aa502010303020
[  4174.828] (II) intel(0): 	36004bcf100000190000000f00000000
[  4174.828] (II) intel(0): 	0000000000206e050f00000000fe0054
[  4174.829] (II) intel(0): 	4d3132313031353457423820000000fe
[  4174.829] (II) intel(0): 	00273641476482abff010120202000e1
[  4174.829] (II) intel(0): EDID vendor "CPT", prod id 5151
[  4174.829] (II) intel(0): Printing DDC gathered Modelines:
[  4174.829] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  4174.829] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[  4174.829] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[  4174.830] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[  4174.830] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  4174.830] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  4174.830] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[  4174.830] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[  4174.830] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[  4174.830] (II) intel(0): Printing probed modes for output LVDS1
[  4174.830] (II) intel(0): Modeline "1280x800"x60.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  4174.830] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4174.830] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4174.830] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  4174.830] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4174.852] (II) intel(0): EDID for output VGA1
[  4175.174] (II) intel(0): EDID for output TV1
[  4175.174] (II) intel(0): Output LVDS1 connected
[  4175.174] (II) intel(0): Output VGA1 disconnected
[  4175.174] (II) intel(0): Output TV1 disconnected
[  4175.174] (II) intel(0): Using exact sizes for initial modes
[  4175.174] (II) intel(0): Output LVDS1 using initial mode 1280x800
[  4175.174] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  4175.174] (II) intel(0): Kernel page flipping support detected, enabling
[  4175.174] (**) intel(0): Display dimensions: (330, 210) mm
[  4175.174] (**) intel(0): DPI set to (98, 96)
[  4175.174] (II) Loading sub module "fb"
[  4175.174] (II) LoadModule: "fb"
[  4175.175] (II) Loading /usr/lib/xorg/modules/libfb.so
[  4175.175] (II) Module fb: vendor="X.Org Foundation"
[  4175.175] 	compiled for 1.10.4, module version = 1.0.0
[  4175.175] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  4175.175] (II) Loading sub module "dri2"
[  4175.175] (II) LoadModule: "dri2"
[  4175.175] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  4175.175] (II) Module dri2: vendor="X.Org Foundation"
[  4175.175] 	compiled for 1.10.4, module version = 1.2.0
[  4175.175] 	ABI class: X.Org Server Extension, version 5.0
[  4175.175] (==) Depth 24 pixmap format is 32 bpp
[  4175.176] (II) intel(0): [DRI2] Setup complete
[  4175.176] (II) intel(0): [DRI2]   DRI driver: i965
[  4175.176] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[  4175.193] (II) UXA(0): Driver registered support for the following operations:
[  4175.193] (II)         solid
[  4175.193] (II)         copy
[  4175.193] (II)         composite (RENDER acceleration)
[  4175.193] (II)         put_image
[  4175.193] (II)         get_image
[  4175.193] (==) intel(0): Backing store disabled
[  4175.193] (==) intel(0): Silken mouse enabled
[  4175.193] (II) intel(0): Initializing HW Cursor
[  4175.216] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  4175.222] (==) intel(0): DPMS enabled
[  4175.222] (==) intel(0): Intel XvMC decoder enabled
[  4175.222] (II) intel(0): Set up textured video
[  4175.222] (II) intel(0): Set up overlay video
[  4175.222] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[  4175.222] (II) intel(0): direct rendering: DRI2 Enabled
[  4175.222] (WW) intel(0): Option "AccelMethod" is not used
[  4175.222] (WW) intel(0): Option "RenderAccel" is not used
[  4175.222] (==) intel(0): hotplug detection: "enabled"
[  4175.223] (--) RandR disabled
[  4175.223] (II) Initializing built-in extension Generic Event Extension
[  4175.223] (II) Initializing built-in extension SHAPE
[  4175.223] (II) Initializing built-in extension MIT-SHM
[  4175.223] (II) Initializing built-in extension XInputExtension
[  4175.223] (II) Initializing built-in extension XTEST
[  4175.223] (II) Initializing built-in extension BIG-REQUESTS
[  4175.223] (II) Initializing built-in extension SYNC
[  4175.223] (II) Initializing built-in extension XKEYBOARD
[  4175.223] (II) Initializing built-in extension XC-MISC
[  4175.223] (II) Initializing built-in extension SECURITY
[  4175.223] (II) Initializing built-in extension XINERAMA
[  4175.223] (II) Initializing built-in extension XFIXES
[  4175.223] (II) Initializing built-in extension RENDER
[  4175.223] (II) Initializing built-in extension RANDR
[  4175.223] (II) Initializing built-in extension COMPOSITE
[  4175.223] (II) Initializing built-in extension DAMAGE
[  4175.223] (II) Initializing built-in extension GESTURE
[  4175.243] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[  4175.247] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  4175.247] (II) AIGLX: enabled GLX_INTEL_swap_event
[  4175.247] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  4175.247] (II) AIGLX: enabled GLX_SGI_make_current_read
[  4175.247] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  4175.247] (II) AIGLX: Loaded and initialized i965
[  4175.247] (II) GLX: Initialized DRI2 GL provider for screen 0
[  4175.248] (II) intel(0): Setting screen physical size to 338 x 211
[  4175.314] (II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  4175.330] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[  4175.330] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  4175.330] (II) LoadModule: "evdev"
[  4175.331] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.332] (II) Module evdev: vendor="X.Org Foundation"
[  4175.332] 	compiled for 1.10.2, module version = 2.6.0
[  4175.332] 	Module class: X.Org XInput Driver
[  4175.332] 	ABI class: X.Org XInput driver, version 12.3
[  4175.332] (II) Using input driver 'evdev' for 'Video Bus'
[  4175.332] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.332] (**) Video Bus: always reports core events
[  4175.332] (**) Video Bus: Device: "/dev/input/event7"
[  4175.332] (--) Video Bus: Found keys
[  4175.332] (II) Video Bus: Configuring as keyboard
[  4175.332] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input7/event7"
[  4175.332] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  4175.332] (**) Option "xkb_rules" "evdev"
[  4175.332] (**) Option "xkb_model" "pc105"
[  4175.332] (**) Option "xkb_layout" "gb"
[  4175.335] (II) XKB: reuse xkmfile /tmp/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[  4175.347] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  4175.347] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  4175.347] (II) Using input driver 'evdev' for 'Power Button'
[  4175.347] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.347] (**) Power Button: always reports core events
[  4175.347] (**) Power Button: Device: "/dev/input/event1"
[  4175.347] (--) Power Button: Found keys
[  4175.347] (II) Power Button: Configuring as keyboard
[  4175.347] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[  4175.347] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  4175.347] (**) Option "xkb_rules" "evdev"
[  4175.347] (**) Option "xkb_model" "pc105"
[  4175.347] (**) Option "xkb_layout" "gb"
[  4175.348] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  4175.348] (II) No input driver/identifier specified (ignoring)
[  4175.349] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[  4175.349] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  4175.349] (II) Using input driver 'evdev' for 'Sleep Button'
[  4175.349] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.349] (**) Sleep Button: always reports core events
[  4175.349] (**) Sleep Button: Device: "/dev/input/event2"
[  4175.349] (--) Sleep Button: Found keys
[  4175.349] (II) Sleep Button: Configuring as keyboard
[  4175.349] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[  4175.349] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  4175.349] (**) Option "xkb_rules" "evdev"
[  4175.349] (**) Option "xkb_model" "pc105"
[  4175.349] (**) Option "xkb_layout" "gb"
[  4175.353] (II) config/udev: Adding input device Broadcom Corp (/dev/input/event4)
[  4175.353] (**) Broadcom Corp: Applying InputClass "evdev keyboard catchall"
[  4175.353] (II) Using input driver 'evdev' for 'Broadcom Corp'
[  4175.353] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.353] (**) Broadcom Corp: always reports core events
[  4175.353] (**) Broadcom Corp: Device: "/dev/input/event4"
[  4175.353] (--) Broadcom Corp: Found keys
[  4175.353] (II) Broadcom Corp: Configuring as keyboard
[  4175.353] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input4/event4"
[  4175.353] (II) XINPUT: Adding extended input device "Broadcom Corp" (type: KEYBOARD)
[  4175.353] (**) Option "xkb_rules" "evdev"
[  4175.354] (**) Option "xkb_model" "pc105"
[  4175.354] (**) Option "xkb_layout" "gb"
[  4175.355] (II) config/udev: Adding input device Broadcom Corp (/dev/input/event5)
[  4175.355] (**) Broadcom Corp: Applying InputClass "evdev pointer catchall"
[  4175.355] (II) Using input driver 'evdev' for 'Broadcom Corp'
[  4175.355] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.355] (**) Broadcom Corp: always reports core events
[  4175.355] (**) Broadcom Corp: Device: "/dev/input/event5"
[  4175.355] (--) Broadcom Corp: Found 3 mouse buttons
[  4175.355] (--) Broadcom Corp: Found relative axes
[  4175.355] (--) Broadcom Corp: Found x and y relative axes
[  4175.355] (II) Broadcom Corp: Configuring as mouse
[  4175.355] (**) Broadcom Corp: YAxisMapping: buttons 4 and 5
[  4175.355] (**) Broadcom Corp: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  4175.355] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input5/event5"
[  4175.355] (II) XINPUT: Adding extended input device "Broadcom Corp" (type: MOUSE)
[  4175.355] (II) Broadcom Corp: initialized for relative axes.
[  4175.355] (**) Broadcom Corp: (accel) keeping acceleration scheme 1
[  4175.355] (**) Broadcom Corp: (accel) acceleration profile 0
[  4175.355] (**) Broadcom Corp: (accel) acceleration factor: 2.000
[  4175.355] (**) Broadcom Corp: (accel) acceleration threshold: 4
[  4175.356] (II) config/udev: Adding input device Broadcom Corp (/dev/input/mouse0)
[  4175.356] (II) No input driver/identifier specified (ignoring)
[  4175.357] (II) config/udev: Adding input device HDA Intel Mic at Ext Left Jack (/dev/input/event11)
[  4175.357] (II) No input driver/identifier specified (ignoring)
[  4175.358] (II) config/udev: Adding input device HDA Intel HP Out at Ext Left Jack (/dev/input/event12)
[  4175.358] (II) No input driver/identifier specified (ignoring)
[  4175.361] (II) config/udev: Adding input device MLK Trust Mouse 15313 (/dev/input/event6)
[  4175.361] (**) MLK Trust Mouse 15313: Applying InputClass "evdev pointer catchall"
[  4175.361] (**) MLK Trust Mouse 15313: Applying InputClass "evdev keyboard catchall"
[  4175.361] (II) Using input driver 'evdev' for 'MLK Trust Mouse 15313'
[  4175.361] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.361] (**) MLK Trust Mouse 15313: always reports core events
[  4175.361] (**) MLK Trust Mouse 15313: Device: "/dev/input/event6"
[  4175.361] (--) MLK Trust Mouse 15313: Found 9 mouse buttons
[  4175.361] (--) MLK Trust Mouse 15313: Found scroll wheel(s)
[  4175.361] (--) MLK Trust Mouse 15313: Found relative axes
[  4175.361] (--) MLK Trust Mouse 15313: Found x and y relative axes
[  4175.361] (--) MLK Trust Mouse 15313: Found absolute axes
[  4175.361] (II) evdev-grail: failed to open grail, no gesture support
[  4175.361] (--) MLK Trust Mouse 15313: Found keys
[  4175.361] (II) MLK Trust Mouse 15313: Configuring as mouse
[  4175.361] (II) MLK Trust Mouse 15313: Configuring as keyboard
[  4175.361] (II) MLK Trust Mouse 15313: Adding scrollwheel support
[  4175.361] (**) MLK Trust Mouse 15313: YAxisMapping: buttons 4 and 5
[  4175.361] (**) MLK Trust Mouse 15313: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  4175.361] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input6/event6"
[  4175.361] (II) XINPUT: Adding extended input device "MLK Trust Mouse 15313" (type: KEYBOARD)
[  4175.361] (**) Option "xkb_rules" "evdev"
[  4175.361] (**) Option "xkb_model" "pc105"
[  4175.361] (**) Option "xkb_layout" "gb"
[  4175.361] (II) MLK Trust Mouse 15313: initialized for relative axes.
[  4175.361] (WW) MLK Trust Mouse 15313: ignoring absolute axes.
[  4175.362] (**) MLK Trust Mouse 15313: (accel) keeping acceleration scheme 1
[  4175.362] (**) MLK Trust Mouse 15313: (accel) acceleration profile 0
[  4175.362] (**) MLK Trust Mouse 15313: (accel) acceleration factor: 2.000
[  4175.362] (**) MLK Trust Mouse 15313: (accel) acceleration threshold: 4
[  4175.362] (II) config/udev: Adding input device MLK Trust Mouse 15313 (/dev/input/mouse1)
[  4175.362] (II) No input driver/identifier specified (ignoring)
[  4175.364] (II) config/udev: Adding input device Laptop Integrated Webcam (/dev/input/event8)
[  4175.364] (**) Laptop Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[  4175.364] (II) Using input driver 'evdev' for 'Laptop Integrated Webcam'
[  4175.364] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.364] (**) Laptop Integrated Webcam: always reports core events
[  4175.364] (**) Laptop Integrated Webcam: Device: "/dev/input/event8"
[  4175.364] (--) Laptop Integrated Webcam: Found keys
[  4175.364] (II) Laptop Integrated Webcam: Configuring as keyboard
[  4175.364] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input8/event8"
[  4175.364] (II) XINPUT: Adding extended input device "Laptop Integrated Webcam" (type: KEYBOARD)
[  4175.364] (**) Option "xkb_rules" "evdev"
[  4175.364] (**) Option "xkb_model" "pc105"
[  4175.364] (**) Option "xkb_layout" "gb"
[  4175.372] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  4175.372] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  4175.372] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  4175.372] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.372] (**) AT Translated Set 2 keyboard: always reports core events
[  4175.372] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  4175.372] (--) AT Translated Set 2 keyboard: Found keys
[  4175.372] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  4175.372] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  4175.372] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  4175.372] (**) Option "xkb_rules" "evdev"
[  4175.372] (**) Option "xkb_model" "pc105"
[  4175.372] (**) Option "xkb_layout" "gb"
[  4175.373] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[  4175.373] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  4175.373] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  4175.373] (II) LoadModule: "synaptics"
[  4175.373] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  4175.373] (II) Module synaptics: vendor="X.Org Foundation"
[  4175.373] 	compiled for 1.10.4, module version = 1.4.1
[  4175.373] 	Module class: X.Org XInput Driver
[  4175.373] 	ABI class: X.Org XInput driver, version 12.3
[  4175.373] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  4175.373] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  4175.373] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  4175.374] (**) Option "Device" "/dev/input/event9"
[  4175.374] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[  4175.374] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[  4175.374] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  4175.374] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  4175.374] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[  4175.376] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4175.376] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  4175.392] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[  4175.392] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  4175.392] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  4175.392] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  4175.392] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[  4175.392] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  4175.392] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  4175.392] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  4175.392] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  4175.392] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[  4175.392] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4175.393] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[  4175.393] (II) No input driver/identifier specified (ignoring)
[  4175.403] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[  4175.403] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  4175.403] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[  4175.403] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  4175.403] (**) Dell WMI hotkeys: always reports core events
[  4175.403] (**) Dell WMI hotkeys: Device: "/dev/input/event10"
[  4175.403] (--) Dell WMI hotkeys: Found keys
[  4175.403] (II) Dell WMI hotkeys: Configuring as keyboard
[  4175.403] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[  4175.403] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[  4175.403] (**) Option "xkb_rules" "evdev"
[  4175.403] (**) Option "xkb_model" "pc105"
[  4175.403] (**) Option "xkb_layout" "gb"
[  4176.519] (II) intel(0): EDID vendor "CPT", prod id 5151
[  4176.519] (II) intel(0): Printing DDC gathered Modelines:
[  4176.519] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  4177.239] (II) intel(0): EDID vendor "CPT", prod id 5151
[  4177.239] (II) intel(0): Printing DDC gathered Modelines:
[  4177.239] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  4177.685] (II) XKB: generating xkmfile /tmp/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  4177.712] (II) intel(0): EDID vendor "CPT", prod id 5151
[  4177.712] (II) intel(0): Printing DDC gathered Modelines:
[  4177.712] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  4178.660] (II) intel(0): EDID vendor "CPT", prod id 5151
[  4178.660] (II) intel(0): Printing DDC gathered Modelines:
[  4178.660] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  4181.229] (II) XKB: generating xkmfile /tmp/server-5550814D3DE81657FB75A6E398FC443242E652DD.xkm
[  4185.488] (II) AIGLX: Suspending AIGLX clients for VT switch
[  4196.253] (II) Open ACPI successful (/var/run/acpid.socket)
[  4196.253] (II) AIGLX: Resuming AIGLX clients after VT switch
[  4196.264] (II) intel(0): EDID vendor "CPT", prod id 5151
[  4196.264] (II) intel(0): Printing DDC gathered Modelines:
[  4196.264] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1450  800 803 809 816 -hsync -vsync (49.0 kHz)
[  4196.621] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[  4196.621] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  4196.910] (II) XKB: reuse xkmfile /tmp/server-5550814D3DE81657FB75A6E398FC443242E652DD.xkm

```

Reinstall mesa?

---

### Post by BicyclerBoy on 2011-10-21
Nothing like the same problem..
Cryoraptor has posted a 2 yr old log file

You seem to have nVidia GLX lib install messing up the intel driver.

Get rid of nvidia-common..
Maybe you have to re-install mesa to fix the symlinks etc..

Can only think nvidia-common that would help with nVidia h/w by installing the model-aliases which identifies GPU h/w from the PCI ids.

---

### Post by turshija on 2011-11-25
Any update on this ?
I'm getting the same problem on my brand new [Acer Aspire 5750ZG](http://notebook.miotec.net/product-5284/acer-aspire_5750zg_b943g32mnbb) running 64bit Ubuntu 11.10 ...
I've tried two versions of drivers I'm being offered in Additional Drivers (both current and post-release updates) with same result ...

```
--- BEGIN ERROR REPORT a1dce528 --------
Generated 11/26/11 12:22 AM

Minecraft: Minecraft 1.0.0
OS: Linux (amd64) version 3.0.0-13-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
at
org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
at org.lwjgl.opengl.Display.create(Display.java:854)
at org.lwjgl.opengl.Display.create(Display.java:784)
at org.lwjgl.opengl.Display.create(Display.java:765)
at net.minecraft.client.Minecraft.a(SourceFile:237)
at net.minecraft.client.Minecraft.run(SourceFile:644)
at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT e74a24ee ----------
```

---

### Post by MoreOrLess on 2011-11-26
> **turshija said:**
> Acer Aspire 5750ZG
You have a hybrid graphics notebook, a.k.a nvidia optimus. (lucky you...)
[https://launchpad.net/~mj-casalogic/+archive/ironhide/](https://launchpad.net/~mj-casalogic/+archive/ironhide/)

---

### Post by turshija on 2011-11-26
> **MoreOrLess said:**
> You have a hybrid graphics notebook, a.k.a nvidia optimus. (lucky you...)
[https://launchpad.net/~mj-casalogic/+archive/ironhide/](https://launchpad.net/~mj-casalogic/+archive/ironhide/)

I'm not sure if that "lucky you" is ironic or not ^_^
Is nvidia optimus good ?
what should I do with the link you provided (n00b explanation plz) ? :)

---

