---
title: "Java in Natty with Intel driver, x errors?"
date: 2011-05-18
forum: Multimedia Software
---

### Post by jivana on 2011-05-18
I am trying to run a Java simulation in a browser (same in FF and Chromium) using Sun Java and have no conflicting Java components installed. It is running very slowly (about .5 FPS, not sure how to measure it exactly) in Natty while it was fine in Maverick. While I had to work my way through the Intel driver workarounds as for every distro upgrade to get any graphics working, something seems to be different in Natty and I cannot figure it out this time.
At first the Java app did not run at all and displayed this error in the Java Console:
```

Default Display could not be created! Using Software Renderer.
org.lwjgl.LWJGLException: X Error - disp: 0x9968840 serial: 148 error: BadGC (invalid GC parameter) request_code: 60 minor_code: 0
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:276)
	at org.lwjgl.opengl.LinuxKeyboard.nSetDetectableKeyRepeat(Native Method)
	at org.lwjgl.opengl.LinuxKeyboard.setDetectableKeyRepeat(LinuxKeyboard.java:152)
	at org.lwjgl.opengl.LinuxKeyboard.destroy(LinuxKeyboard.java:163)
	at org.lwjgl.opengl.LinuxDisplay.destroyKeyboard(LinuxDisplay.java:1054)
	at org.lwjgl.input.Keyboard.destroy(Keyboard.java:349)
	at org.lwjgl.opengl.Display.destroyWindow(Display.java:357)
	at org.lwjgl.opengl.Display.access$300(Display.java:67)
	at org.lwjgl.opengl.Display$3.destroy(Display.java:146)
	at org.lwjgl.opengl.Display.create(Display.java:864)
	at org.lwjgl.opengl.Display.create(Display.java:785)
	at org.lwjgl.opengl.Display.create(Display.java:766)
	at P.D.A(Unknown Source)
	at engine.D.C(Unknown Source)
	at M.B.H(Unknown Source)
	at engine.B$_A.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:662)
(null:-1): java.lang.NullPointerException
	at org.lwjgl.opengl.GL11.glGetString(GL11.java:1771)
	at R.A.D.<init>(Unknown Source)
	at R.A.B.E(Unknown Source)
	at M.B.H(Unknown Source)
	at engine.B$_A.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:662)

Exception in thread "CoronaGameThread" java.lang.NullPointerException
	at org.lwjgl.opengl.GL11.glGenTextures(GL11.java:1372)
	at I.D.Ó(Unknown Source)
	at I.D.N(Unknown Source)
	at F.A.G.E(Unknown Source)
	at F.A.G.B(Unknown Source)
	at I.E.<init>(Unknown Source)
	at engine.H.G(Unknown Source)
	at M.B.H(Unknown Source)
	at engine.B$_A.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:662)

```

So to run it, I switched from **libgl1-mesa-glx** to **libgl1-mesa-swx11**, but it's too slow to even watch.
However, my video and graphics performance is better than ever, although the computer is defaulting to Ubuntu Classic, which I've always used, anyway.

Hardware: Dell Dell 510m with an Intel 855GM integrated graphics card

xorg.conf file (largely the result of Intel graphics workarounds):
```

Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
Option          "AccelMethod"   "UXA"
        VideoRam        130560
EndSection

```

The only thing going wrong now I can think of (being an experienced muck-around-er with Ubuntu, but not knowing too much in particular) is that the X configuration is not 100%. Xorg.0.log shows lots of error messages of the kind 
```

[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

```.
Here Xorg.0.log without running the java app - it still shows the errors:
```
[    19.767] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    19.767] X Protocol Version 11, Revision 0
[    19.767] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    19.767] Current Operating System: Linux xxxxx-laptop 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686
[    19.767] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-9-generic root=UUID=e3fd410e-3b1b-499c-a7a8-c2b011034839 ro quiet splash vt.handoff=7
[    19.768] Build Date: 19 April 2011  03:33:17PM
[    19.768] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    19.768] Current version of pixman: 0.20.2
[    19.768] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.768] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.768] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 19 07:54:45 2011
[    19.768] (==) Using config file: "/etc/X11/xorg.conf"
[    19.768] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.768] (==) No Layout section.  Using the first Screen section.
[    19.768] (**) |-->Screen "Configured Screen Device" (0)
[    19.768] (**) |   |-->Monitor "<default monitor>"
[    19.769] (**) |   |-->Device "Configured Video Device"
[    19.769] (==) No monitor specified for screen "Configured Screen Device".
	Using a default monitor configuration.
[    19.769] (==) Automatically adding devices
[    19.769] (==) Automatically enabling devices
[    19.876] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.876] 	Entry deleted from font path.
[    19.924] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    19.924] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.924] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.924] (II) Loader magic: 0x81ffde0
[    19.924] (II) Module ABI versions:
[    19.924] 	X.Org ANSI C Emulation: 0.4
[    19.924] 	X.Org Video Driver: 10.0
[    19.924] 	X.Org XInput driver : 12.3
[    19.924] 	X.Org Server Extension : 5.0
[    19.925] (--) PCI:*(0:0:2:0) 8086:3582:1028:0164 rev 2, Mem @ 0xf0000000/134217728, 0xfaf80000/524288, I/O @ 0x0000c000/8
[    19.925] (--) PCI: (0:0:2:1) 8086:3582:1028:0164 rev 2, Mem @ 0xe8000000/134217728, 0xfaf00000/524288
[    19.926] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.926] (II) LoadModule: "extmod"
[    19.962] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.962] (II) Module extmod: vendor="X.Org Foundation"
[    19.963] 	compiled for 1.10.1, module version = 1.0.0
[    19.963] 	Module class: X.Org Server Extension
[    19.963] 	ABI class: X.Org Server Extension, version 5.0
[    19.963] (II) Loading extension MIT-SCREEN-SAVER
[    19.963] (II) Loading extension XFree86-VidModeExtension
[    19.963] (II) Loading extension XFree86-DGA
[    19.963] (II) Loading extension DPMS
[    19.963] (II) Loading extension XVideo
[    19.963] (II) Loading extension XVideo-MotionCompensation
[    19.963] (II) Loading extension X-Resource
[    19.963] (II) LoadModule: "dbe"
[    19.963] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.963] (II) Module dbe: vendor="X.Org Foundation"
[    19.963] 	compiled for 1.10.1, module version = 1.0.0
[    19.963] 	Module class: X.Org Server Extension
[    19.963] 	ABI class: X.Org Server Extension, version 5.0
[    19.963] (II) Loading extension DOUBLE-BUFFER
[    19.963] (II) LoadModule: "glx"
[    19.963] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.963] (II) Module glx: vendor="X.Org Foundation"
[    19.963] 	compiled for 1.10.1, module version = 1.0.0
[    19.963] 	ABI class: X.Org Server Extension, version 5.0
[    19.963] (==) AIGLX enabled
[    19.963] (II) Loading extension GLX
[    19.963] (II) LoadModule: "record"
[    19.964] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.964] (II) Module record: vendor="X.Org Foundation"
[    19.964] 	compiled for 1.10.1, module version = 1.13.0
[    19.964] 	Module class: X.Org Server Extension
[    19.964] 	ABI class: X.Org Server Extension, version 5.0
[    19.964] (II) Loading extension RECORD
[    19.964] (II) LoadModule: "dri"
[    19.964] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.964] (II) Module dri: vendor="X.Org Foundation"
[    19.964] 	compiled for 1.10.1, module version = 1.0.0
[    19.964] 	ABI class: X.Org Server Extension, version 5.0
[    19.964] (II) Loading extension XFree86-DRI
[    19.964] (II) LoadModule: "dri2"
[    19.964] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.964] (II) Module dri2: vendor="X.Org Foundation"
[    19.964] 	compiled for 1.10.1, module version = 1.2.0
[    19.964] 	ABI class: X.Org Server Extension, version 5.0
[    19.965] (II) Loading extension DRI2
[    19.965] (==) Matched vesa as autoconfigured driver 0
[    19.965] (==) Matched fbdev as autoconfigured driver 1
[    19.965] (==) Assigned the driver to the xf86ConfigLayout
[    19.965] (II) LoadModule: "vesa"
[    19.994] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.004] (II) Module vesa: vendor="X.Org Foundation"
[    20.004] 	compiled for 1.10.0, module version = 2.3.0
[    20.004] 	Module class: X.Org Video Driver
[    20.005] 	ABI class: X.Org Video Driver, version 10.0
[    20.005] (II) LoadModule: "fbdev"
[    20.005] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.007] (II) Module fbdev: vendor="X.Org Foundation"
[    20.007] 	compiled for 1.10.0, module version = 0.4.2
[    20.007] 	ABI class: X.Org Video Driver, version 10.0
[    20.007] (II) VESA: driver for VESA chipsets: vesa
[    20.007] (II) FBDEV: driver for framebuffer: fbdev
[    20.007] (++) using VT number 7

[    20.007] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    20.007] (WW) Falling back to old probe method for vesa
[    20.007] (II) Loading sub module "fbdevhw"
[    20.007] (II) LoadModule: "fbdevhw"
[    20.007] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.015] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.015] 	compiled for 1.10.1, module version = 0.0.2
[    20.015] 	ABI class: X.Org Video Driver, version 10.0
[    20.015] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.015] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.015] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    20.015] (II) FBDEV(0): using default device
[    20.015] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Configured Screen Device" for depth/fbbpp 24/32
[    20.015] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    20.015] (==) FBDEV(0): RGB weight 888
[    20.015] (==) FBDEV(0): Default visual is TrueColor
[    20.015] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.015] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    20.015] (II) FBDEV(0): checking modes against framebuffer device...
[    20.015] (II) FBDEV(0): checking modes against monitor...
[    20.015] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    20.015] (**) FBDEV(0):  Built-in mode "current"
[    20.015] (==) FBDEV(0): DPI set to (96, 96)
[    20.016] (II) Loading sub module "fb"
[    20.016] (II) LoadModule: "fb"
[    20.016] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.031] (II) Module fb: vendor="X.Org Foundation"
[    20.031] 	compiled for 1.10.1, module version = 1.0.0
[    20.031] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.031] (**) FBDEV(0): using shadow framebuffer
[    20.031] (II) Loading sub module "shadow"
[    20.031] (II) LoadModule: "shadow"
[    20.031] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    20.032] (II) Module shadow: vendor="X.Org Foundation"
[    20.032] 	compiled for 1.10.1, module version = 1.1.0
[    20.032] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.032] (==) Depth 24 pixmap format is 32 bpp
[    20.380] (==) FBDEV(0): Backing store disabled
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (==) FBDEV(0): DPMS enabled
[    20.385] (==) RandR enabled
[    20.385] (II) Initializing built-in extension Generic Event Extension
[    20.385] (II) Initializing built-in extension SHAPE
[    20.385] (II) Initializing built-in extension MIT-SHM
[    20.385] (II) Initializing built-in extension XInputExtension
[    20.385] (II) Initializing built-in extension XTEST
[    20.385] (II) Initializing built-in extension BIG-REQUESTS
[    20.385] (II) Initializing built-in extension SYNC
[    20.385] (II) Initializing built-in extension XKEYBOARD
[    20.385] (II) Initializing built-in extension XC-MISC
[    20.385] (II) Initializing built-in extension SECURITY
[    20.385] (II) Initializing built-in extension XINERAMA
[    20.385] (II) Initializing built-in extension XFIXES
[    20.385] (II) Initializing built-in extension RENDER
[    20.385] (II) Initializing built-in extension RANDR
[    20.385] (II) Initializing built-in extension COMPOSITE
[    20.385] (II) Initializing built-in extension DAMAGE
[    20.385] (II) Initializing built-in extension GESTURE
[    20.402] (II) AIGLX: Screen 0 is not DRI2 capable
[    20.402] (II) AIGLX: Screen 0 is not DRI capable
[    20.402] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    20.587] (II) AIGLX: Loaded and initialized swrast
[    20.587] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    20.792] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.812] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    20.812] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.812] (II) LoadModule: "evdev"
[    20.813] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.861] (II) Module evdev: vendor="X.Org Foundation"
[    20.861] 	compiled for 1.10.0.902, module version = 2.6.0
[    20.861] 	Module class: X.Org XInput Driver
[    20.861] 	ABI class: X.Org XInput driver, version 12.3
[    20.861] (II) Using input driver 'evdev' for 'Video Bus'
[    20.861] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.861] (**) Video Bus: always reports core events
[    20.861] (**) Video Bus: Device: "/dev/input/event4"
[    20.862] (--) Video Bus: Found keys
[    20.862] (II) Video Bus: Configuring as keyboard
[    20.862] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input4/event4"
[    20.862] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    20.862] (**) Option "xkb_rules" "evdev"
[    20.862] (**) Option "xkb_model" "pc105"
[    20.862] (**) Option "xkb_layout" "gb"
[    20.866] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    20.880] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.880] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.880] (II) Using input driver 'evdev' for 'Power Button'
[    20.880] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.880] (**) Power Button: always reports core events
[    20.880] (**) Power Button: Device: "/dev/input/event1"
[    20.881] (--) Power Button: Found keys
[    20.881] (II) Power Button: Configuring as keyboard
[    20.881] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    20.881] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.881] (**) Option "xkb_rules" "evdev"
[    20.881] (**) Option "xkb_model" "pc105"
[    20.881] (**) Option "xkb_layout" "gb"
[    20.881] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    20.881] (II) No input driver/identifier specified (ignoring)
[    20.882] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    20.882] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.882] (II) Using input driver 'evdev' for 'Sleep Button'
[    20.882] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.882] (**) Sleep Button: always reports core events
[    20.882] (**) Sleep Button: Device: "/dev/input/event2"
[    20.882] (--) Sleep Button: Found keys
[    20.882] (II) Sleep Button: Configuring as keyboard
[    20.882] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    20.882] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    20.882] (**) Option "xkb_rules" "evdev"
[    20.882] (**) Option "xkb_model" "pc105"
[    20.882] (**) Option "xkb_layout" "gb"
[    20.890] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    20.890] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.890] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.890] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.890] (**) AT Translated Set 2 keyboard: always reports core events
[    20.890] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    20.890] (--) AT Translated Set 2 keyboard: Found keys
[    20.890] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    20.890] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    20.890] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    20.890] (**) Option "xkb_rules" "evdev"
[    20.891] (**) Option "xkb_model" "pc105"
[    20.891] (**) Option "xkb_layout" "gb"
[    20.891] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event5)
[    20.891] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    20.891] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    20.891] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.891] (**) PS/2 Mouse: always reports core events
[    20.891] (**) PS/2 Mouse: Device: "/dev/input/event5"
[    20.891] (--) PS/2 Mouse: Found 3 mouse buttons
[    20.891] (--) PS/2 Mouse: Found relative axes
[    20.891] (--) PS/2 Mouse: Found x and y relative axes
[    20.892] (II) PS/2 Mouse: Configuring as mouse
[    20.892] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    20.892] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.892] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    20.892] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    20.892] (II) PS/2 Mouse: initialized for relative axes.
[    20.892] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    20.892] (**) PS/2 Mouse: (accel) acceleration profile 0
[    20.892] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    20.892] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    20.892] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[    20.892] (II) No input driver/identifier specified (ignoring)
[    20.893] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event6)
[    20.893] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    20.893] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    20.893] (II) LoadModule: "synaptics"
[    20.893] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.908] (II) Module synaptics: vendor="X.Org Foundation"
[    20.908] 	compiled for 1.10.0.902, module version = 1.3.99
[    20.908] 	Module class: X.Org XInput Driver
[    20.908] 	ABI class: X.Org XInput driver, version 12.3
[    20.908] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    20.908] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    20.908] (**) Option "Device" "/dev/input/event6"
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    20.908] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    20.908] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    20.909] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    20.909] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    20.909] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    20.909] (II) No input driver/identifier specified (ignoring)
```

Here it is after running the Java app, with more errors:
```

[    19.767] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    19.767] X Protocol Version 11, Revision 0
[    19.767] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    19.767] Current Operating System: Linux stefan-laptop 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:25:15 UTC 2011 i686
[    19.767] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-9-generic root=UUID=e3fd410e-3b1b-499c-a7a8-c2b011034839 ro quiet splash vt.handoff=7
[    19.768] Build Date: 19 April 2011  03:33:17PM
[    19.768] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    19.768] Current version of pixman: 0.20.2
[    19.768] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.768] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.768] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May 19 07:54:45 2011
[    19.768] (==) Using config file: "/etc/X11/xorg.conf"
[    19.768] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.768] (==) No Layout section.  Using the first Screen section.
[    19.768] (**) |-->Screen "Configured Screen Device" (0)
[    19.768] (**) |   |-->Monitor "<default monitor>"
[    19.769] (**) |   |-->Device "Configured Video Device"
[    19.769] (==) No monitor specified for screen "Configured Screen Device".
	Using a default monitor configuration.
[    19.769] (==) Automatically adding devices
[    19.769] (==) Automatically enabling devices
[    19.876] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.876] 	Entry deleted from font path.
[    19.924] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    19.924] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.924] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.924] (II) Loader magic: 0x81ffde0
[    19.924] (II) Module ABI versions:
[    19.924] 	X.Org ANSI C Emulation: 0.4
[    19.924] 	X.Org Video Driver: 10.0
[    19.924] 	X.Org XInput driver : 12.3
[    19.924] 	X.Org Server Extension : 5.0
[    19.925] (--) PCI:*(0:0:2:0) 8086:3582:1028:0164 rev 2, Mem @ 0xf0000000/134217728, 0xfaf80000/524288, I/O @ 0x0000c000/8
[    19.925] (--) PCI: (0:0:2:1) 8086:3582:1028:0164 rev 2, Mem @ 0xe8000000/134217728, 0xfaf00000/524288
[    19.926] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.926] (II) LoadModule: "extmod"
[    19.962] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.962] (II) Module extmod: vendor="X.Org Foundation"
[    19.963] 	compiled for 1.10.1, module version = 1.0.0
[    19.963] 	Module class: X.Org Server Extension
[    19.963] 	ABI class: X.Org Server Extension, version 5.0
[    19.963] (II) Loading extension MIT-SCREEN-SAVER
[    19.963] (II) Loading extension XFree86-VidModeExtension
[    19.963] (II) Loading extension XFree86-DGA
[    19.963] (II) Loading extension DPMS
[    19.963] (II) Loading extension XVideo
[    19.963] (II) Loading extension XVideo-MotionCompensation
[    19.963] (II) Loading extension X-Resource
[    19.963] (II) LoadModule: "dbe"
[    19.963] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.963] (II) Module dbe: vendor="X.Org Foundation"
[    19.963] 	compiled for 1.10.1, module version = 1.0.0
[    19.963] 	Module class: X.Org Server Extension
[    19.963] 	ABI class: X.Org Server Extension, version 5.0
[    19.963] (II) Loading extension DOUBLE-BUFFER
[    19.963] (II) LoadModule: "glx"
[    19.963] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.963] (II) Module glx: vendor="X.Org Foundation"
[    19.963] 	compiled for 1.10.1, module version = 1.0.0
[    19.963] 	ABI class: X.Org Server Extension, version 5.0
[    19.963] (==) AIGLX enabled
[    19.963] (II) Loading extension GLX
[    19.963] (II) LoadModule: "record"
[    19.964] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.964] (II) Module record: vendor="X.Org Foundation"
[    19.964] 	compiled for 1.10.1, module version = 1.13.0
[    19.964] 	Module class: X.Org Server Extension
[    19.964] 	ABI class: X.Org Server Extension, version 5.0
[    19.964] (II) Loading extension RECORD
[    19.964] (II) LoadModule: "dri"
[    19.964] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.964] (II) Module dri: vendor="X.Org Foundation"
[    19.964] 	compiled for 1.10.1, module version = 1.0.0
[    19.964] 	ABI class: X.Org Server Extension, version 5.0
[    19.964] (II) Loading extension XFree86-DRI
[    19.964] (II) LoadModule: "dri2"
[    19.964] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.964] (II) Module dri2: vendor="X.Org Foundation"
[    19.964] 	compiled for 1.10.1, module version = 1.2.0
[    19.964] 	ABI class: X.Org Server Extension, version 5.0
[    19.965] (II) Loading extension DRI2
[    19.965] (==) Matched vesa as autoconfigured driver 0
[    19.965] (==) Matched fbdev as autoconfigured driver 1
[    19.965] (==) Assigned the driver to the xf86ConfigLayout
[    19.965] (II) LoadModule: "vesa"
[    19.994] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.004] (II) Module vesa: vendor="X.Org Foundation"
[    20.004] 	compiled for 1.10.0, module version = 2.3.0
[    20.004] 	Module class: X.Org Video Driver
[    20.005] 	ABI class: X.Org Video Driver, version 10.0
[    20.005] (II) LoadModule: "fbdev"
[    20.005] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.007] (II) Module fbdev: vendor="X.Org Foundation"
[    20.007] 	compiled for 1.10.0, module version = 0.4.2
[    20.007] 	ABI class: X.Org Video Driver, version 10.0
[    20.007] (II) VESA: driver for VESA chipsets: vesa
[    20.007] (II) FBDEV: driver for framebuffer: fbdev
[    20.007] (++) using VT number 7

[    20.007] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    20.007] (WW) Falling back to old probe method for vesa
[    20.007] (II) Loading sub module "fbdevhw"
[    20.007] (II) LoadModule: "fbdevhw"
[    20.007] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.015] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.015] 	compiled for 1.10.1, module version = 0.0.2
[    20.015] 	ABI class: X.Org Video Driver, version 10.0
[    20.015] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.015] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.015] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    20.015] (II) FBDEV(0): using default device
[    20.015] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Configured Screen Device" for depth/fbbpp 24/32
[    20.015] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    20.015] (==) FBDEV(0): RGB weight 888
[    20.015] (==) FBDEV(0): Default visual is TrueColor
[    20.015] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.015] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    20.015] (II) FBDEV(0): checking modes against framebuffer device...
[    20.015] (II) FBDEV(0): checking modes against monitor...
[    20.015] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    20.015] (**) FBDEV(0):  Built-in mode "current"
[    20.015] (==) FBDEV(0): DPI set to (96, 96)
[    20.016] (II) Loading sub module "fb"
[    20.016] (II) LoadModule: "fb"
[    20.016] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.031] (II) Module fb: vendor="X.Org Foundation"
[    20.031] 	compiled for 1.10.1, module version = 1.0.0
[    20.031] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.031] (**) FBDEV(0): using shadow framebuffer
[    20.031] (II) Loading sub module "shadow"
[    20.031] (II) LoadModule: "shadow"
[    20.031] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    20.032] (II) Module shadow: vendor="X.Org Foundation"
[    20.032] 	compiled for 1.10.1, module version = 1.1.0
[    20.032] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.032] (==) Depth 24 pixmap format is 32 bpp
[    20.380] (==) FBDEV(0): Backing store disabled
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.381] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.382] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.383] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.384] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    20.385] (==) FBDEV(0): DPMS enabled
[    20.385] (==) RandR enabled
[    20.385] (II) Initializing built-in extension Generic Event Extension
[    20.385] (II) Initializing built-in extension SHAPE
[    20.385] (II) Initializing built-in extension MIT-SHM
[    20.385] (II) Initializing built-in extension XInputExtension
[    20.385] (II) Initializing built-in extension XTEST
[    20.385] (II) Initializing built-in extension BIG-REQUESTS
[    20.385] (II) Initializing built-in extension SYNC
[    20.385] (II) Initializing built-in extension XKEYBOARD
[    20.385] (II) Initializing built-in extension XC-MISC
[    20.385] (II) Initializing built-in extension SECURITY
[    20.385] (II) Initializing built-in extension XINERAMA
[    20.385] (II) Initializing built-in extension XFIXES
[    20.385] (II) Initializing built-in extension RENDER
[    20.385] (II) Initializing built-in extension RANDR
[    20.385] (II) Initializing built-in extension COMPOSITE
[    20.385] (II) Initializing built-in extension DAMAGE
[    20.385] (II) Initializing built-in extension GESTURE
[    20.402] (II) AIGLX: Screen 0 is not DRI2 capable
[    20.402] (II) AIGLX: Screen 0 is not DRI capable
[    20.402] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    20.587] (II) AIGLX: Loaded and initialized swrast
[    20.587] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    20.792] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.812] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    20.812] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.812] (II) LoadModule: "evdev"
[    20.813] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.861] (II) Module evdev: vendor="X.Org Foundation"
[    20.861] 	compiled for 1.10.0.902, module version = 2.6.0
[    20.861] 	Module class: X.Org XInput Driver
[    20.861] 	ABI class: X.Org XInput driver, version 12.3
[    20.861] (II) Using input driver 'evdev' for 'Video Bus'
[    20.861] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.861] (**) Video Bus: always reports core events
[    20.861] (**) Video Bus: Device: "/dev/input/event4"
[    20.862] (--) Video Bus: Found keys
[    20.862] (II) Video Bus: Configuring as keyboard
[    20.862] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input4/event4"
[    20.862] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    20.862] (**) Option "xkb_rules" "evdev"
[    20.862] (**) Option "xkb_model" "pc105"
[    20.862] (**) Option "xkb_layout" "gb"
[    20.866] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    20.880] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    20.880] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.880] (II) Using input driver 'evdev' for 'Power Button'
[    20.880] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.880] (**) Power Button: always reports core events
[    20.880] (**) Power Button: Device: "/dev/input/event1"
[    20.881] (--) Power Button: Found keys
[    20.881] (II) Power Button: Configuring as keyboard
[    20.881] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    20.881] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.881] (**) Option "xkb_rules" "evdev"
[    20.881] (**) Option "xkb_model" "pc105"
[    20.881] (**) Option "xkb_layout" "gb"
[    20.881] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    20.881] (II) No input driver/identifier specified (ignoring)
[    20.882] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    20.882] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.882] (II) Using input driver 'evdev' for 'Sleep Button'
[    20.882] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.882] (**) Sleep Button: always reports core events
[    20.882] (**) Sleep Button: Device: "/dev/input/event2"
[    20.882] (--) Sleep Button: Found keys
[    20.882] (II) Sleep Button: Configuring as keyboard
[    20.882] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    20.882] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    20.882] (**) Option "xkb_rules" "evdev"
[    20.882] (**) Option "xkb_model" "pc105"
[    20.882] (**) Option "xkb_layout" "gb"
[    20.890] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    20.890] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.890] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.890] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.890] (**) AT Translated Set 2 keyboard: always reports core events
[    20.890] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    20.890] (--) AT Translated Set 2 keyboard: Found keys
[    20.890] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    20.890] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    20.890] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    20.890] (**) Option "xkb_rules" "evdev"
[    20.891] (**) Option "xkb_model" "pc105"
[    20.891] (**) Option "xkb_layout" "gb"
[    20.891] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event5)
[    20.891] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    20.891] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    20.891] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.891] (**) PS/2 Mouse: always reports core events
[    20.891] (**) PS/2 Mouse: Device: "/dev/input/event5"
[    20.891] (--) PS/2 Mouse: Found 3 mouse buttons
[    20.891] (--) PS/2 Mouse: Found relative axes
[    20.891] (--) PS/2 Mouse: Found x and y relative axes
[    20.892] (II) PS/2 Mouse: Configuring as mouse
[    20.892] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    20.892] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.892] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    20.892] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    20.892] (II) PS/2 Mouse: initialized for relative axes.
[    20.892] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    20.892] (**) PS/2 Mouse: (accel) acceleration profile 0
[    20.892] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    20.892] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    20.892] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse0)
[    20.892] (II) No input driver/identifier specified (ignoring)
[    20.893] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event6)
[    20.893] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    20.893] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    20.893] (II) LoadModule: "synaptics"
[    20.893] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.908] (II) Module synaptics: vendor="X.Org Foundation"
[    20.908] 	compiled for 1.10.0.902, module version = 1.3.99
[    20.908] 	Module class: X.Org XInput Driver
[    20.908] 	ABI class: X.Org XInput driver, version 12.3
[    20.908] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    20.908] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    20.908] (**) Option "Device" "/dev/input/event6"
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    20.908] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    20.908] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    20.908] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    20.908] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    20.909] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    20.909] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    20.909] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse1)
[    20.909] (II) No input driver/identifier specified (ignoring)
[  8956.624] (II) XKB: reuse xkmfile /var/lib/xkb/server-C516A43597F5C19E6D5298016C7B5853052F7589.xkm
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.823] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.824] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.825] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.826] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.827] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.832] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.833] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.834] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.834] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.836] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.837] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.838] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.839] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.844] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.845] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.846] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.847] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.848] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.850] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[ 13177.851] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

```

Here some of my configuration:
lshw:
```
H/W path           Device      Class          Description
=========================================================
                               system         Portable Computer
/0                             bus            0H1908
/0/0                           memory         64KiB BIOS
/0/400                         processor      Intel(R) Pentium(R) M processor 1.
/0/400/700                     memory         8KiB L1 cache
/0/400/701                     memory         2MiB L2 cache
/0/1000                        memory         2GiB System Memory
/0/1000/0                      memory         1GiB DIMM DDR Synchronous 333 MHz 
/0/1000/1                      memory         1GiB DIMM DDR Synchronous 333 MHz 
/0/100                         bridge         82852/82855 GM/GME/PM/GMV Processo
/0/100/0.1                     generic        82852/82855 GM/GME/PM/GMV Processo
/0/100/0.3                     generic        82852/82855 GM/GME/PM/GMV Processo
/0/100/2                       display        82852/855GM Integrated Graphics De
/0/100/2.1                     display        82852/855GM Integrated Graphics De
/0/100/1d                      bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.1                    bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.2                    bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1d.7                    bus            82801DB/DBM (ICH4/ICH4-M) USB2 EHC
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1e/1                    bridge         PCI4510 PC card Cardbus Controller
/0/100/1e/1.1                  bus            PCI4510 IEEE-1394 Controller
/0/100/1e/3        eth1        network        PRO/Wireless LAN 2100 3B Mini PCI 
/0/100/1e/8        eth0        network        82801DB PRO/100 VE (MOB) Ethernet 
/0/100/1f                      bridge         82801DBM (ICH4-M) LPC Interface Br
/0/100/1f.1        scsi0       storage        82801DBM (ICH4-M) IDE Controller
/0/100/1f.1/0      /dev/sda    disk           60GB FUJITSU MHT2060A
/0/100/1f.1/0/1    /dev/sda1   volume         53GiB EXT4 volume
/0/100/1f.1/0/2    /dev/sda2   volume         2384MiB Extended partition
/0/100/1f.1/0/2/5  /dev/sda5   volume         2384MiB Linux swap / Solaris parti
/0/100/1f.1/1      /dev/cdrom  disk           DVD+RW DW-R56A
/0/100/1f.5                    multimedia     82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-
/0/100/1f.6                    communication  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-

```

lsmod:
```

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
lib80211_crypt_ccmp    12785  2 
snd_intel8x0           33213  1 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
i915                  450944  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ipw2100                77368  0 
pcmcia                 39671  0 
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
libipw                 46641  1 ipw2100
lib80211               14570  2 lib80211_crypt_ccmp,libipw
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 ipw2100,libipw
ppdev                  12849  0 
joydev                 17322  0 
binfmt_misc            13213  1 
yenta_socket           27230  0 
drm                   180037  2 i915,drm_kms_helper
dell_laptop            13515  0 
pcmcia_rsrc            18292  1 yenta_socket
dcdbas                 14054  1 dell_laptop
parport_pc             32111  1 
snd                    55295  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
soundcore              12600  1 snd
shpchp                 32345  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
e100                   40108  0 
crc_itu_t              12627  1 firewire_core

```

lspci:
```

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

```

Any help at all is much appreciated. If you need anything else, please let me know.

---

### Post by jivana on 2011-05-19
Fixed it myself after all:
Added **Driver ¨intel¨** back into **Xorg.conf**.
On startup, got black screen.
Checked Xorg.0.log to notice that the intel module cannot be found.
Installed package **xserver-xorg-video-inte**l - not sure why it was not installed in the first place.
No more black screen on startup.
Then switched back from **libgl1-mesa-swx11** to **libgl1-mesa-glx** and the computer is pumping, best performance ever.

:guitar:

---

