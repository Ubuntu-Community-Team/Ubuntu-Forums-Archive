---
title: "Kind of a Unique Nvidia problem"
date: 2011-09-08
forum: Multimedia Software
---

### Post by gregorthebigmac on 2011-09-08
So right off the bat, I'm guessing most people reading this will think "why would you do that?" But this is the setup I have, and the problems it's causing. I've been doing research, but can't find anything that addresses my problem specifically, so if there's a write-up on this already, feel free to just drop a link and say "come back if this doesn't solve it."

When I first installed 10.04, I had only one graphics card, and 2 monitors, running twinview. The card is a GeForce 9800 GTX+ ([[COLOR="Blue"]_Specs_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130339"))

But then I got a third monitor, and bought a new card so I can run all 3 simultaneously. The new card is a GeForce 430 GT ([[COLOR="Blue"]_Specs_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130579")). Since the 430 has twice as much RAM, I made that one my primary, and made the 9800 my secondary. Windows 7 had no problem with this (I'm dual-booting win7 and Ubuntu). But Ubuntu won't even boot with this setup.

I managed to get it to boot in failsafe low graphics mode, so right now I got one monitor running on the 430 GT at 1280x1024. My first thought was I had installed the drivers for the 9800 GTX+ before I swapped the cards, so I should probably uninstall those drivers, reboot, and reinstall the drivers for the new card. Tried, and still no go. Right before the login screen would normally come up, and I get the blinking _ in my top-left, it stops blinking, and just freezes. Since I don't keep much on the hard drive that Ubuntu is installed on, I tried erasing and reinstalling Ubuntu 10.04. Still didn't help. So now, I'm at a loss. Thanks in advance.

---

### Post by BicyclerBoy on 2011-09-08
The GT430 is most likely not supported by the nvidia-current driver version in 10.04.

You can check the nvidia linux driver readme documentation..Appendix A.
275.xxx.x does support GT430
I think you need to add a launchpad ppa to get a later driver.
xorg-edgers ppa
x-swat team ppa

post your /var/log/Xorg.0.log file to help debug..

Dual video cards can have problems with 32 bit setups due to available memory in the boot phase.

---

### Post by gregorthebigmac on 2011-09-09
That makes sense. I have been pretty lucky with hardware, as far as linux distros are concerned. This is the first time I've owned a video card that was *not* supported by linux.

Also, I know my profile says 11.04, but I'm actually running 10.04 64-bit. When I try to edit my personal data, it says I can't do it until I make 50 posts, but anyway, here's my log:


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux grayghost 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-28-generic root=UUID=445d0089-d728-4c07-907c-1bb9c421cdef ro quiet splash
Build Date: 10 December 2010  05:52:57PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  9 05:06:27 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
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
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:3:0:0) 10de:0de1:3842:1430 nVidia Corporation rev 161, Mem @ 0xf6000000/16777216, 0xc8000000/134217728, 0xc6000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/524288
(--) PCI: (0:4:0:0) 10de:0613:3842:c879 nVidia Corporation G92 [GeForce 9800 GTX+] rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 03@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Sep 09 05:06:27 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 09 05:06:27 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 09 05:06:27 NVIDIA(0):     enabled.
(EE) Sep 09 05:06:31 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:3:0:0. 
(EE) Sep 09 05:06:31 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Sep 09 05:06:31 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Sep 09 05:06:31 NVIDIA(0):     README for additional information.
(EE) Sep 09 05:06:31 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by BicyclerBoy on 2011-09-09
You appear to be running nvidia 195.xx.xx
That is not recognizing the GT430. (very good HTPC card)
There is a lot of old cruft in the xorg.conf file..(probably harmless).

Try the xorg-edgers launchpad ppa..that should get you 260 - 275 & later Xorg packages.
Backup your old xorg.conf & then run:
nvidia-xconfig

Note: GT430 is the perfect HTPC based on performance/power efficiency...it is not a gaming openGL card.

---

### Post by gregorthebigmac on 2011-09-10
> **BicyclerBoy said:**
> Note: GT430 is the perfect HTPC based on performance/power efficiency...it is not a gaming openGL card.

Is this true for all OS's, or just Linux-based?

---

### Post by LowSky on 2011-09-10
> **gregorthebigmac said:**
> Is this true for all OS's, or just Linux-based?

You can game with any card but performance will take a hit.

For decent gaming a Nvidia GTX 460 or better would be recommended these days. And the 460 is nearly a year old. Lets be fair gaming in Linux isn't really that great so any gaming you do wont need even your 9800. OpenGL is no where as good as DirectX for gaming in most cases.

To be fair my GTX460 only gets used to decode video when I'm using Linux.

---

### Post by gregorthebigmac on 2011-09-10
Interesting. I've been using my GT 430 for Portal 2, and I've been running it at 1920x1080 with everything almost maxed out (I think I was using 8xAA, and everything else was cranked), and the only time the game bogs down is if I'm in a big room with lots of objects in it. Granted, that's the only game I've played since buying the card (I only got it a couple weeks ago), but so far, it's been treating me pretty well.

---

### Post by BicyclerBoy on 2011-09-10
That shows how good the cheap bottom end cards can be..

The distinction between the HTPC & gaming cards has changed because now all the new models have the purevideo bitstream processor.
The GT200 family were feature set C
The GTX200 family were only set A. 
The 9800 & 9600 were all set A
The 9400 were all feature set B (as were 8200 9200)
So the slower members of the families were superior for HTPC for PQ, noise & power efficiency.
Only the too slow GT520 has set D.
The GPU only need to be fast enough to run the post decode filters (scale, sharpen denoise, de-interlace) in the shaders & the GT520 isn't.

Linux nVidia X server. AFAIK, disclaimer to follow..
If the 9800 card was the primary GPU/monitor then all openGL computation runs on this GPU. The 430 was {just} a output renderer.
You can tell the X sever to use a specific card or both I think, but the cards need to be similar or same model.
It is explained in the driver readme but not very clearly or in one section.
I have never had the opportunity to put this theory into practise tho'.

---

### Post by gregorthebigmac on 2011-09-12
Good to know.

I haven't updated my drivers yet (just been a super busy week), but a new development on my situation just now happened. While I was on my win7 partition, Windows randomly decided to reboot while I went outside to have a smoke. When I came back, Ubuntu had loaded by default, and normally, it would freeze while trying to start X. But I guess it wasn't actually frozen, it was simply taking forever to get X started. When I came back inside, roughly 10 minutes later, I was at the login screen on my main monitor from the 9800GTX+, but the GT430 has a frozen image of the Ubuntu splash screen stuck on it, and Ubuntu refuses to acknowledge any video besides one of the monitors on the GT430, and when I click System>Preferences>Monitors it says "Could not get screen information: RANDR extension is not present."

---

### Post by BicyclerBoy on 2011-09-12
The nVidia driver readme is a good source of info..but you need to read the whole thing.
Chapter 25.
Multi-card GPU processing requires using SLI mode & a video bridge in most cases..
Identical cards recommended.
Has some really bad side-effects like: can only have monitors connected to primary, no twinview.
(SLI)mosaic is a solution BUT only works with professional quadro cards. 
So you probably better with one good card with multiple outputs.
Appendix A.
Is the list of supported h/w.

The gnome System>Preferences>Monitors tools is completely unusable/useless when using the nVidia X server.
You have to use nvidia-settings.

---

### Post by gregorthebigmac on 2011-11-28
Sorry to revive an old thread, but I wanted to follow up on the results of my situation, in case anyone else runs into a similar problem. I didn't have much chance to work on this until this past weekend, and I finally got my system to a point where it's not perfect, but I can live with it for now. Here is what I tried, and what the result was:

1. Tried installing Ubuntu 11.10. This worked, but not with the best results. Unity would only run in 2d, and it was kind of laggy (which blew me away, considering I'm running an i7 930 with 8gb of ram, and two video cards with 1.5 gb of ram between the two of them). Not to mention, it would only recognize one monitor (the main one on the 430 GT). I couldn't even get it to acknowledge I had a second GPU.

2. Installed 11.04, with similar results.

3. Tried going back to 10.10, which gave me the same issue I was fighting in the beginning.

4. Tried a new approach by installing 10.04, installing all updates through synaptic, then upgrading to 10.10 through synaptic, with all 10.10 updates. *Then* I tried installing the updated drivers through the usual System>Administration>Additional Drivers program. This allows me to use all 3 monitors simultaneously, but they must be divided into two separate X Servers. My main monitor on the 430 GT is one X Server, and the other two monitors on the 9800 GTX+ are running twinview on a single X Server. Not the ideal setup I would have liked, but it will suffice.

**tl;dr** BicyclerBoy was right. They won't run on a single X Server using twinview or xinerama, but they will work if you divide up the X Servers according to which GPU your monitors are on. It may not be the sweet setup you had going on another OS, but it will do. Thanks to everyone for your help and suggestions :)

---

