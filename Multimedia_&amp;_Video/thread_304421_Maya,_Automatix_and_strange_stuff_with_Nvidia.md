---
title: "Maya, Automatix and strange stuff with Nvidia"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by J-Rod on 2006-11-21
Ok, first off I am kinda new to all this, and I am usually a pretty quick learner. However I really need some insight as to what the deal is with my current setup. 

I have Wings3d and Maya 8 installed on Dapper. When I originally set up the system, I knew I should have jumped into all the hardware stuff first, but after reading a bit on installing new nvidia drivers I couldn't stomach it at the time. Anyways, I found Automatix, and decided I would give that a shot. It seemed to work fine, "nvidia" is in my xorg.conf, and GLX is working. I don't know how to check for my exact driver version, but it maybe 8772 or so? The latest that are available from the repository. For a look at what kind of weirdness I got when I loaded up my 3d apps, check this thread for pics:

[http://www.ubuntuforums.org/showthread.php?t=303688](http://www.ubuntuforums.org/showthread.php?t=303688)

So, I decided I would have a whack at running the latest set from Nvidia's website, I tihnk that was 9629. After 4 hours of trying all kinds of great tutorials from this site, and broken X, I never got them working. Here's where I am going to likely not make much sense.

If I uninstall nvidia drivers from automatix, and ensure synaptic is clear, x will not load. At that point I can restore an older version of xorg.conf from the terminal after x defecates in my mouth, and run startx, I'll get back into X fine. It's a bit borked though, it looks like some kind of issue with GDM when I check the logs. This happens even when I change the "nvidia" to "nv". When I am loaded into the borked version of X, Maya and Wings3d work great, even though I had loaded an old version of xorg that should have had just "nv". 

So yes, this is getting long. What I really need to know is what do I need to do to get all this previous crap cleaned out, back to regular soft nvidia, so I can try some other stuff to get GLX working, with drivers that play nice with my 3d apps. Thanks for any help you all can provide!

*edit* I forgot to mention, when I had uninstalled the automatix installation of nvidia, x never boots quite right. The only way I can get the system running with GDM working correctly (where I get my login manager, and the shutdown button has all the options) is if I install the nvidia again through automatix. Something tells me I should have avoided that altogether.

-JC

---

### Post by Mongoose on 2006-11-21
BTW glxinfo is pretty useful command for OpenGL information on your system.  ;)

If you think think you have a mixed version kernel module and x driver, and want to know a quick fix:

Login to a console < Alt > < Ctrl < F1 >

/etc/init.d/gdm stop  <-- stop X

cd /usr/lib/xorg/modules/drivers
ls nvidia*

if you see two modules nvidia_drv.so and nvidia_drv.o look at the dates.  If you see a difference try:

mv nvidia_drv.so nvidia_drv.so-oldass
mv nvidia_drv.o nvidia_drv.so

/etc/init.d/gdm start  <-- Start X service back up

glxinfo <-- check your GL version

This is typically a problem with ubuntu if you install nvidia packaged drivers sometimes.  Not really that big of a deal.

---

### Post by J-Rod on 2006-11-21
Thanks for your reply, I'll give that a try either tonight or tomorrow mornign and report what I've got going on!

---

### Post by J-Rod on 2006-11-22
Okay, well I just checked for the files. Right now I am running the 8772 driver installed via automatix, and GDM works, but 3d programs don't. I have nv_drv.so and nvidia_drv.o in my /usr/lib/xorg/modules/drivers. If I uninstall 8772 from automatix, it looks like GDM breaks, and I am back to the issues I had in my original post.

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce3/AGP/SSE/3DNOW!
OpenGL version string: 1.2 (1.5.6 NVIDIA 87.76)

I have read in some other posts that 8762 worked ok. Is there a way I can get those intalled instead of 8776?

---

### Post by J-Rod on 2006-11-22
Me again. Here is my current state of affairs. I have followed step 2 of this *[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)* tutorial to the T, no errors. Before I started it, I did a 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to make sure I was starting with a clean slate. I used the 9629 drivers from Nvidia's site. Afterwards, X will not start, and here's the error report I get:

```
/usr/lib/xorg/modules/xgl/libglx.so Cannot open shared object, so such file or dir exists
Fatal Error No GLX Modules loaded
```

When I followed instructions to uninstall everything from automatix, nvidia-glx and the like and go back to regular "nv", I cannot get X to start that way either, I have checked my xorg.conf to ensure it was configured with "nv". I am pretty lost at this point, any other input would be greatly appreciated. ](*,)

---

### Post by J-Rod on 2006-11-22
Well, here's an update. I dug through the forums some more, and discovered Envy. TSELIOT: you sir, are a godsend. I am still salty that it took a script to do this, and I didn't do it manually, but I found that the card I am using with the current drivers (GeForce3 Ti200 + 9629) segfaults for everyone. I used the Envy script unstable to install the 9626 drivers, and they work fine. Now, the only problem I have left is GDM still doesn't load properly. After it crashes from a cold boot, I get the errors about libglx.so not being seen. I can log in from prompt, and then run startx, I get into X fine running the 9626 drivers, and all is well. If anyone can tell me how to fig the xorg.conf from this point, I'd appreciate it. For now I am happy just to have something working, even somewhat borked. :)

---

### Post by tseliot on 2006-11-22
> **J-Rod said:**
> Well, here's an update. I dug through the forums some more, and discovered Envy. TSELIOT: you sir, are a godsend. I am still salty that it took a script to do this, and I didn't do it manually, but I found that the card I am using with the current drivers (GeForce3 Ti200 + 9629) segfaults for everyone. I used the Envy script unstable to install the 9626 drivers, and they work fine. Now, the only problem I have left is GDM still doesn't load properly. After it crashes from a cold boot, I get the errors about libglx.so not being seen. I can log in from prompt, and then run startx, I get into X fine running the 9626 drivers, and all is well. If anyone can tell me how to fig the xorg.conf from this point, I'd appreciate it. For now I am happy just to have something working, even somewhat borked. :)

CAn you post your /var/log/Xorg.0.log ?

---

### Post by J-Rod on 2006-11-22
Sure can.


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux jrodder-desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 22 16:26:36 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "GDM-5411"
(**) |   |-->Device "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3189 card 1106,3189 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b168 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 1282,9102 card 3030,5032 rev 40 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1106,3104 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,3177 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1565,f614 rev 50 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0201 card 1462,8503 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xd7ffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV20 [GeForce3 Ti 200] rev 163, Mem @ 0xd8000000/24, 0xc8000000/27, 0xd0000000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xc7ffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe0041000 - 0xe00410ff (0x100) MX[B]
	[1] -1	0	0xe0040000 - 0xe00400ff (0x100) MX[B]
	[2] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[3] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[4] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[5] -1	0	0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe0041000 - 0xe00410ff (0x100) MX[B]
	[1] -1	0	0xe0040000 - 0xe00400ff (0x100) MX[B]
	[2] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[3] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[4] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[5] -1	0	0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
	[6] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[7] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0041000 - 0xe00410ff (0x100) MX[B]
	[5] -1	0	0xe0040000 - 0xe00400ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[8] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9626
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9626
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9626  Wed Sep 20 16:41:00 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0041000 - 0xe00410ff (0x100) MX[B]
	[5] -1	0	0xe0040000 - 0xe00400ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[8] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe0041000 - 0xe00410ff (0x100) MX[B]
	[5] -1	0	0xe0040000 - 0xe00400ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[8] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[19] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] 0	0	0xd00803b0 - 0xd00803bb (0xc) IS[B]
	[22] 0	0	0xd00803c0 - 0xd00803df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce3 Ti 200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 03.20.00.28.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce3 Ti 200 at PCI:1:0:0:
(--) NVIDIA(0):     Silicon Graphics GDM-5411 (CRT-0)
(--) NVIDIA(0): Silicon Graphics GDM-5411 (CRT-0): 350.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1800x1440"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1920x1440"
(II) NVIDIA(0):     "1856x1392"
(II) NVIDIA(0):     "1792x1344"
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1440
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd007ffff (0x80000) MX[B]
	[1] 0	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] 0	0	0xd8000000 - 0xd8ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe0041000 - 0xe00410ff (0x100) MX[B]
	[8] -1	0	0xe0040000 - 0xe00400ff (0x100) MX[B]
	[9] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[10] -1	0	0xd0000000 - 0xd007ffff (0x80000) MX[B](B)
	[11] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] 0	0	0xd00803b0 - 0xd00803bb (0xc) IS[B]
	[25] 0	0	0xd00803c0 - 0xd00803df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1920x1440"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
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
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1280x960"

---

### Post by J-Rod on 2006-11-27
-=bump=- Anyone?

---

### Post by Mongoose on 2006-11-28
GeForce 3?  Doesn't that need the legacy driver pak?  I have no idea actually, since even my grandmother has newer hardware that I've given her.  No offense.  =)

---

