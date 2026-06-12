---
title: "X Crashing (Google Chrome?)"
date: 2011-02-22
forum: Multimedia Software
---

### Post by Sam Lars on 2011-02-22
I'm using Ubuntu 10.10 64-bit with Intel GM965 graphics.
I've been having X crash every few days. It's always been while I'm doing things in Chrome (dev channel, currently 11.0.672.2). Either X just suddenly restarts, or the screens slowly pixelizes white and then X restarts. I can't find any info in the system logs or the X log before the crash.
None of Chrome's graphics flags (GPU Accelerated Canvas 2D, Composited render layer borders, GPU Accelerated Compositing) are enabled.
Any ideas for tracking down what's causing this? Things will work fine for a day or two and then without warning while doing something in Chrome, X will restart.

---

### Post by primlinOS on 2011-04-24
Same issue here.  X is crashing.  I switched over to chrome because I was getting a similar problem using firefox, from flash I think (crashing X).  Reported that bug via apport.  This one is "unsupported with apport."  I have:

Title: chromium-browser crashed with SIGABRT
UnreportableReason: The program crashed on an assertion failure, but the message could not be retrieved. Apport does not support reporting these crashes.
XsessionErrors:
 (gnome-power-manager:1943): Gtk-WARNING **: A floating object was finalized. This means that someone
 (polkit-gnome-authentication-agent-1:1973): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
 (gnome-panel:1974): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen2/screen' was not being monitored by GConfClient 0x1b17520
 (gnome-panel:1974): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen2/screen' was not being monitored by GConfClient 0x1b17520
 (gnome-panel:1974): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x1b17520
 (gnome-panel:1974): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x1b17520
 (nautilus:1976): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
 (nautilus:1976): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
 (nautilus:1976): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
 (nautilus:1976): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
 (nautilus:1976): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
 

Very annoying crash, since it kills X, and restarting w/ sudo etc/init.gdm start doesn't work without running sudo etc/init.gdm stop first ... loses all your work.

---

### Post by mandarke on 2011-05-06
i'm getting something similar whenever i have chrome and mplayer/totem/youtube running. as i close chrome the screen goes black for a few seconds then i am presented with the login screen.

looking at my logs at the time of the event i get this:

May  7 04:53:50 acer8730 kernel: [19981.809962] ACPI Warning for \_SB_.PCI0.PEGP.VGA_.MXMI: Excess arguments - needs 1, found 2 (20100428/nspredef-319)
May  7 04:53:50 acer8730 kernel: [19981.810041] ACPI Warning for \_SB_.PCI0.PEGP.VGA_.MXMS: Excess arguments - needs 1, found 2 (20100428/nspredef-319)

my system specs are: intel t6400 @ 2GHz, 4GB ram, nvidia 9300m gs (driver ver 260.19.06) on an acer 8730g.

---

### Post by kortas on 2011-05-08
have the same problem with google-chrome and ubuntu 10.10 (intel graphics)

---

### Post by peterx14 on 2011-05-08
I've been seeing the odd X crash (kicks me back to the login screen) over the last 2 or 3 weeks. After re-logging in, my /var/log/Xorg.0.log.old file contains:

```

[  2266.734] 
Backtrace:
[  2266.750] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[  2266.750] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[  2266.750] 2: /lib/libpthread.so.0 (0x7f8a682ba000+0xfb40) [0x7f8a682c9b40]
[  2266.750] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f8a62c32000+0x3a3a7c) [0x7f8a62fd5a7c]
[  2266.750] 4: /usr/bin/X (FreeClientResources+0xef) [0x44adef]
[  2266.750] 5: /usr/bin/X (CloseDownClient+0x5c) [0x43b2ac]
[  2266.750] 6: /usr/bin/X (0x400000+0x3fa46) [0x43fa46]
[  2266.750] 7: /usr/bin/X (0x400000+0x2187b) [0x42187b]
[  2266.750] 8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f8a67225d8e]
[  2266.750] 9: /usr/bin/X (0x400000+0x21409) [0x421409]
[  2266.750] Segmentation fault at address (nil)
[  2266.750] 
Caught signal 11 (Segmentation fault). Server aborting
[  2266.750] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[  2266.750] Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

This is running Ubuntu 10.10 64bit on a Core i5-750 with nVidia GeForce 9800GT 512MB graphics card.

Every crash (I've probably had about 6 or 7 now) has been when I've just done something with Chrome -- usually just closed it. Chrome has been updated at least once during these problems, but I'm currently running Google Chrome 11.0.696.65

Not sure how/where this should be filed?

---

### Post by quazi on 2011-05-14
> **peterx14 said:**
> I've been seeing the odd X crash (kicks me back to the login screen) over the last 2 or 3 weeks. After re-logging in, my /var/log/Xorg.0.log.old file contains:

```

[  2266.734] 
Backtrace:
[  2266.750] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[  2266.750] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[  2266.750] 2: /lib/libpthread.so.0 (0x7f8a682ba000+0xfb40) [0x7f8a682c9b40]
[  2266.750] 3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f8a62c32000+0x3a3a7c) [0x7f8a62fd5a7c]
[  2266.750] 4: /usr/bin/X (FreeClientResources+0xef) [0x44adef]
[  2266.750] 5: /usr/bin/X (CloseDownClient+0x5c) [0x43b2ac]
[  2266.750] 6: /usr/bin/X (0x400000+0x3fa46) [0x43fa46]
[  2266.750] 7: /usr/bin/X (0x400000+0x2187b) [0x42187b]
[  2266.750] 8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f8a67225d8e]
[  2266.750] 9: /usr/bin/X (0x400000+0x21409) [0x421409]
[  2266.750] Segmentation fault at address (nil)
[  2266.750] 
Caught signal 11 (Segmentation fault). Server aborting
[  2266.750] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[  2266.750] Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

This is running Ubuntu 10.10 64bit on a Core i5-750 with nVidia GeForce 9800GT 512MB graphics card.

Every crash (I've probably had about 6 or 7 now) has been when I've just done something with Chrome -- usually just closed it. Chrome has been updated at least once during these problems, but I'm currently running Google Chrome 11.0.696.65

Not sure how/where this should be filed?


Same hardware, same problem.

---

### Post by peterx14 on 2011-05-16
As a work around, I had been starting Chrome and just making sure I always leave one Chrome window minimised since I only seem to get crashes when I close the last Chrome window.

That seems to work, the only down side being that if I click on a hyper-link somewhere and there's no other Chrome windows, it'll restore the minimised window and use that... I found this particularly annoying because I'd usually keep my minimised Chrome instance on a separate screen! So what I needed was a way to keep Chrome running but prevent it from being used to open links... and happily, this is possible by running it as an "app"... e.g. without any address bar or navigation buttons.

So, I've now added an extra Chrome launcher on my panel with the command:
```
google-chrome --app="http://localhost/"
```

When I first log in, I click this launcher and then minimise that Chrome window.

Obviously this isn't ideal, but does seem to prevent the crashes. Hopefully there will be a proper fix some time... but it's odd that more people aren't being affected!

---

### Post by morodrigues on 2011-05-17
Same problem with me.

Using Ubuntu 10.10 on Dell Lattitude D820 with a NVidia graphics adapter.

Google Chrome version is 11.0.696.68.

Problem also occurs when closing Google Chrome.

The problem started some weeks ago (2011.04.28) after an Ubuntu update on Xserver-xorg-video-savage, nautilus, google-chrome and others.

---

### Post by coldnebo on 2011-05-18
Sounds like I'm having the same problem. Everything is fine, then I close the last google-chrome window and the X server spontaneously restarts.

I initially thought that this was because of the WebGL exploits reported earlier (see [http://www.contextis.co.uk/resources/blog/webgl/]("http://www.contextis.co.uk/resources/blog/webgl/"))

But even when using --disable-webgl, the problem still exists.

Note, I am using Compiz and Emerald.

```

$ uname -a
Linux lkyrala-ibex-64 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

$ lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

$ sudo lspci -v
01:00.0 VGA compatible controller: nVidia Corporation G84 [Quadro FX 370] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: nVidia Corporation Device 0491
	Physical Slot: 2
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 1100 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nouveau, nvidiafb

$ glxinfo|grep -i nvidia
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL version string: 3.3.0 NVIDIA 260.19.06
OpenGL shading language version string: 3.30 NVIDIA via Cg compiler

$ compiz --version
compiz 0.8.6


```


/var/log/gdm/0.log.1 shows:

```

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux lkyrala-ibex-64 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64
Kernel command line: root=UUID=3ce4cb05-7db5-4a80-9e2b-53131443f531 ro quiet splash 
Build Date: 09 January 2011  12:14:27PM
xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 13 10:08:06 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(--) PCI:*(0:1:0:0) 10de:040a:10de:0491 rev 161, Mem @ 0xf2000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x00001100/128
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA GLX Module  260.19.06  Mon Sep 13 04:54:41 PDT 2010
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.2.0
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA dlloader X Driver  260.19.06  Mon Sep 13 04:31:43 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(--) using VT number 8

(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 1.0.0
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU Quadro FX 370 (G84GL) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.6a.00.10
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on Quadro FX 370 at PCI:1:0:0
(--) NVIDIA(0):     HP LP2465 (DFP-1)
(--) NVIDIA(0): HP LP2465 (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): HP LP2465 (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) NVIDIA(0): DPI set to (93, 92); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
(WW) NVIDIA(0):     UBB.
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(==) NVIDIA(0): DPMS enabled
(II) NVIDIA(0): [DRI2] Setup complete
(==) RandR enabled
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.9.0, module version = 2.3.2
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/udev: Adding input device CHICONY USB NetVista Full Width Keyboard (/dev/input/event2)
(**) CHICONY USB NetVista Full Width Keyboard: Applying InputClass "evdev keyboard catchall"
(**) CHICONY USB NetVista Full Width Keyboard: always reports core events
(**) CHICONY USB NetVista Full Width Keyboard: Device: "/dev/input/event2"
(II) CHICONY USB NetVista Full Width Keyboard: Found keys
(II) CHICONY USB NetVista Full Width Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "CHICONY USB NetVista Full Width Keyboard" (type: KEYBOARD)
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
(**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Found relative axes
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event4)
(**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) HP WMI hotkeys: always reports core events
(**) HP WMI hotkeys: Device: "/dev/input/event4"
(II) HP WMI hotkeys: Found keys
(II) HP WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
(II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
2: /lib/libpthread.so.0 (0x7f40efaef000+0xfb40) [0x7f40efafeb40]
3: /usr/lib/xorg/extra-modules/nvidia_drv.so (0x7f40ea467000+0x3a3a7c) [0x7f40ea80aa7c]
4: /usr/bin/X (FreeClientResources+0xef) [0x44adef]
5: /usr/bin/X (CloseDownClient+0x5c) [0x43b2ac]
6: /usr/bin/X (0x400000+0x3fa46) [0x43fa46]
7: /usr/bin/X (0x400000+0x2187b) [0x42187b]
8: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f40eea5ad8e]
9: /usr/bin/X (0x400000+0x21409) [0x421409]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) Power Button: Close
(II) Power Button: Close
(II) CHICONY USB NetVista Full Width Keyboard: Close
(II) Logitech USB Optical Mouse: Close
(II) HP WMI hotkeys: Close
 ddxSigGiveUp: Closing log

```

---

### Post by coldnebo on 2011-05-19
hey guys, I just read up on the making of nouveau (opensource nvidia driver) standard in Ubuntu 10.04.  One of the articles I read said that the nvidia provided drivers are still available in case you want OpenGL support for games, etc.

It's very confusing though.  On the one hand, I don't remember having these spontaneous crashes in 10.04.  On the other, the boards are now full of complaints about compiz and 3d games not working together, which seems similar to my prob of webgl and compiz not playing nice together.

I may try the nvidia drivers (270.41.06), but there's a lot of work:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/installdriver.html)
[http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/commonproblems.html#nouveau](http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/commonproblems.html#nouveau)

Yikes.  Has anyone else tried this or noticed problems afterwards?

Thanks!

---

### Post by Sam Lars on 2011-05-19
I have an FX5200 that I've used the Nvidia driver with before. I found that it wasn't too bad to set up and it worked quite well. I would guess that Nvidia's drivers would be better than the open source one... Nouveau is relatively new.
I haven't had the Chrome problems for a while now. I'm still using the dev channel, 13.0.767.1, and I'm on 11.04 now. I enabled the 2D compositing flag, but it says it's not supported...
I have been having an issue that when I'm using Gthumb and I right click on something and choose to open with Gimp, after I've done that a few times, eventually that crashes X.

---

### Post by coldnebo on 2011-05-24
Ok, this is crashing waaaay too much. Bye Google Chrome, back to Firefox.

---

### Post by quazi on 2011-06-18
> **coldnebo said:**
> Ok, this is crashing waaaay too much. Bye Google Chrome, back to Firefox.

It is unbelievable to me that this hasn't been fixed yet. This is a huge problem.

---

### Post by Yellow Pasque on 2011-06-18
> **quazi said:**
> It is unbelievable to me that this hasn't been fixed yet. This is a huge problem.
How is it going to get fixed without a bug report? ;)

---

### Post by quazi on 2011-06-23
Point taken, the only bug report I found was filed with google (who dismissed it as a Ubuntu problem).

Anyway, installing the newest Nvidia driver seemed to fix the issue with me.

---

### Post by peterx14 on 2011-06-23
FWIW I've not had a crash in a few weeks now and I've not changed anything -- just applied the updates as they come, so I assumed Chrome was fixed!

---

### Post by kavoura on 2011-12-16
I have been having the same problem for some time now. I close Chrome and then X crashes and I am back at the login screen, which also shows me as logged in still.

I am using Ubuntu 10.10 64-bit, and have updated Chrome several times and with each new update, either it will crash when closing Chrome or it will not, seems to be fairly random.

I recall going to a page to report this bug at the time it happened first, and others were having the same problem. Several months on and the problem has not been fixed.

Surely there must be a solution to this?

I would just use Firefox, but there is one website in particular I need to use which does not work properly in Firefox but works okay in Chrome, so I need Chrome for a few things like that.

---

