---
title: "FGLRX for 9.04 and ATI Radeon HD 3200 GPU"
date: 2009-04-23
forum: Multimedia Software
---

### Post by trivialpackets on 2009-04-23
Anyone know if there's any way to get this going yet?

---

### Post by BubuXP on 2009-04-23
From this thread:
[http://ubuntuforums.org/showthread.php?t=1133844](http://ubuntuforums.org/showthread.php?t=1133844)


I have same GPU as your and all is working fine in Jaunty with fglrx.


How I resolved:

Reinstalled a clean copy of Jaunty.
After applying updates, I opened Synaptic and removed all xserver-xorg-* useless packages (related to other VGA). Here's the list:
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-intel
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-voodoo

After, I installed the xorg-driver-fglrx package and all dependencies, via Synaptic.
Next step, opened a terminal and typed:
sudo aticonfig --initial -f
Finally, I crossed my fingers and reboot. And I'm still here

Compiz works fine and also Google Earth 5 from Medibuntu repository runs smooth (but with compiz or minimal effects enabled the earth start to flash and is unusuable).

---

### Post by trivialpackets on 2009-04-23
Thanks, I'll be giving this a try.  Currently running Ubuntu in a virtualbox on my vista install, but may be reversing that if all goes well!  Actually, that's not true...I would probably be going to XP in a VB or maybe even Windows 7 Beta.

I don't care so much about the compiz, but the improved rendering over the radeon drivers is what I'm looking for.

---

### Post by trivialpackets on 2009-04-23
Here goes nothing!

---

### Post by trivialpackets on 2009-04-23
Worked like a charm!  Thanks!

---

### Post by pyrokamileon on 2009-04-25
I installed 9.04 today and when I was done with everything I tried installing the new ati drivers.  of course they didn't work and I figured I'd try what was suggested on this forum but now my system won't load the login screen correctly (and even if I try logging in blindly nothing happens) so seeing as how I don't know enough about linux or the root command line to get anywhere I figure I might try again after reinstalling 9.04.  but since everything worked fine b4 installing the ati drivers I'm not even sure if I'll do that...

---

### Post by Darent on 2009-04-25
Hi, pyrokamileon. I have exactly the same problem. fglrx doesn't work with jaunty and my radeon x1300(and some other radeon's), so if you install it, you can't acces the x server (the login screen is black)

You can try this:

-Reboot, and in the grub select failsafe mode (the second option, under normal boot).
-It will ask you if you want to continue normal boot. No, select the option "root prompt with network access" (not exactly that name, but you'll found it)

Now you have to unninstall privative ati drivers. You can do this:

sudo apt-get remove xorg-driver-fglrx


If this doesn't work, (maybe your drivers were installed via a binary.run) go to the folder where ati drivers are installed doing
cd /usr/share/ati
and there, do this:

./fglrx-uninstall.sh

(put sudo if doesn't work)

This will unninstall the ati drivers.

Then, you must install the free drivers, doing this:

sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-radeon

After this, you'll get the free drivers. The performance is not perfect, but at least you have a desktop and you can run compiz... 

We'll have to wait to they fix this mess... For now, i have compiz working buth i can't play epsxe emulator xD ******* ati... 

See you

---

### Post by Darent on 2009-04-25
As i said in my post, the only solution i found is to install the free drivers...

Can someone please confirm if the solution of bubuxp

**sudo aticonfig --initial -f**

work in a **Radeon x1300**?

Thank you.

---

### Post by BubuXP on 2009-04-26
no, this won't work with your VGA because it isn't supported anymore by the fglrx drivers in Jaunty (ver. 9.4).

This command needs to configure properly the /etc/X11/xorg.conf file, because the driver installer won't do this.
If you cannot boot anymore, you can try to run the live cd and restore the original xorg.conf file.
My clean xorg.conf file is:


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by khmr33 on 2009-04-26
I got things working finally. Followed your directions but the Synaptic packages are out of date. Installed driver from ATi website manually on top of the Synaptic version.

New version has updated Catalyst gui with the underscan slider that fixes black border on HDTV's ( yay!!! ) but I'm sure I'm screwing something up in my xorg.conf.

I'm still getting tearing on 720p MKV's in SMplayer. I even turned off desk effects to no avail. (actually the performance seemed to be similar with compiz running) 

Tried with both 60Hz and 24Hz desktop refresh rates. I'm using Xv, but there's a selection for Xv 0 AVIVO I tried it doesn't work. SMPlayer reports back that Mplayer is out of date when I pick that option. Went to mPlayer website... they say that the version being used by Synaptic is outdated with little help on how to get a newer version.

Since it's the HD3200 it's supposed to use Textured Video rather than Video Overlay or OpenGL Overlay... is Xv the right choice???

I think I'm supposed to be loading more modules than just glx anyone know for sure?

Here's my xorg.conf


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideo" "on"
	Option	    "Textured2D" "on"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
	Option	    "TexturedVideoSync" "on"
	Option	    "Capabilities" "0x00000800"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

---

### Post by rvm4000 on 2009-04-27
> **khmr33 said:**
> Tried with both 60Hz and 24Hz desktop refresh rates. I'm using Xv, but there's a selection for Xv 0 AVIVO I tried it doesn't work. SMPlayer reports back that Mplayer is out of date when I pick that option. Went to mPlayer website... they say that the version being used by Synaptic is outdated with little help on how to get a newer version.

You can get a newer version of mplayer from this PPA:
[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by mendieta on 2009-04-27
Thanks all for posting your experiences. I had my HD 3200 running just fine with gflrx in 8.10, and the upgrade to Jaunty broke it to a point I can only use the radeon driver (with no 3D accel). I tried all the suggestions here, including khmr33's xorg.conf, I tried other things I saw on the web, and in launchpad's bug reports, and still broken (when trying fglrx). I tried purging packages, I tried the latest catalyst (9.4) from ATI's site, what haven't I!

Despite the common wisdom that one should use NVIDIA in Linux, and having had an NVIDIA card with no issues in my previous box, I just built a new rig around AMD/ATI, in part as a way to say thanks for opening the specs of the graphics card to facilitate open source drivers. But the frustrations I've already had make me think it was a mistake. It ptickes me that you can;t report a bug to the ATI engineers, all you can do (AFAIK) is to fill a "feedback" form. Oh well. 

I think I'll get an NVIDIA PCIe card and get done with this :-(

---

### Post by khmr33 on 2009-04-28
That's the problem, I'm still sure my xorg.conf isn't completely right.

Also, I think we're talking fresh install only here... I would never expect an upgrade to work. So...

1. Fresh Install
2. Delete junk VGA files (per BubuXp)
3. Install old FGLRX. (BubuXp used Synaptic, I used Restricted Driver manager under System -> Admin -> Hardware Drivers)
4. Initialize (sudo aticonfig --initial -f)
5. Reboot (If you are using HDMI to an HDTV your underscan should be effed in the a)
6. Download 9.4 from ATi's website
7. Follow this guide for manual install ([http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide))
8. Initialize (sudo aticonfig --initial -f)
9. Reboot
10. Force use of xorg.conf (sudo aticonfig --input=/etc/X11/xorg.conf --tls=1)
11. Edit xorg.conf (my file is a start, but we need help finalizing it)
12. Reboot

This got everything working until I got greedy and started effing with video playback.

---

### Post by mendieta on 2009-04-28
Thanks kmh33!

Fresh install is not at option, I have mythbuntu-backend installed and it took me a long while to figure out how to set it up. Having said that, all my tests (except for the first hours of frustration) were done on a FRESH install on a usb drive. I am trying to fix it there and copy the steps in the desktop.

I'll give it another shot, thanks a lot for your post. I'll see if it inspires me. I love the community around _X_buntu.

BTW, the 9.4 Catalyst driver is an "early driver" for 9.04. Since they have a release about once a month, I may wait and try for one more release before buying a dedicated card. Oh well.

Cheers, and thank you all for sharing!

---

### Post by mendieta on 2009-04-28
Well, I did try again, this time in the hard drive installation, and same as in the USB drive, no go. I think the driver gets confused when trying to load up (see the x log below). I did all the steps suggested here, tried the fglrx from the repo, and the one in Catalyst 9.4, following all the proper instructions. The one from the repositories didn;t work at all (it couldn't even run aticonfig properly). Something screwed was that the fglrx xserver package doesn't check that you have the kernel headers installed. but I installed them manually.

Oh well. 

```


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux grisell 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 29 00:22:52 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:5:0) ATI Technologies Inc Radeon HD 3200 Graphics rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, 0xfe900000/1048576, I/O @ 0x0000d000/256
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.3
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.3
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.60.3
(II) ATI Proprietary Linux Driver Release Identifier: 8.602                                
(II) ATI Proprietary Linux Driver Build Date: Apr  1 2009 14:59:47
(II) PCS database file /etc/ati/amdpcsdb not found
(II)   Creating PCS database from initial defaults instead
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 5.0
(--) Chipset Supported AMD Graphics Processor (0x9610) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x99d3000
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[34] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[35] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[36] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[37] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[38] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(--) fglrx(0): Chipset: "ATI Radeon HD 3200 Graphics" (Chipset = 0x9610)
(--) fglrx(0): (PciSubVendor = 0x105b, PciSubDevice = 0x0e17)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfeaf0000
(--) fglrx(0): I/O port at 0x0000d000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.79
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS780
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) fglrx(0): Using adapter: 1:5.0.
(--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000001, disabled=0x00000000
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: JWY  Model: 1733  Serial#: 0
(II) fglrx(0): Year: 2003  Week: 40
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.609 redY: 0.352   greenX: 0.303 greenY: 0.550
(II) fglrx(0): blueX: 0.148 blueY: 0.128   whiteX: 0.305 whiteY: 0.342
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0):  
(II) fglrx(0):  
(II) fglrx(0): Monitor name: 
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff002af9331700000000
(II) fglrx(0): 	280d010308221b00ca0b329c5a4d8c26
(II) fglrx(0): 	204e57afcf0081800101010101010101
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300520e1100001e000000fe000a2020
(II) fglrx(0): 	20202020202020202020000000fe000a
(II) fglrx(0): 	202020202020202020202020000000fc
(II) fglrx(0): 	000a2020202020202020202020200048
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Output DFP2 using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output CRT1 using initial mode 1280x1024
(++) fglrx(0): DPI set to (100, 100)
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): QBS disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): [pcie] 1931264 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): AC Adapter is used
(II) fglrx(0): Interrupt handler installed at IRQ 2300.
(II) fglrx(0): Finished Initialize PPLIB!
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[34] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[35] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[36] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[37] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[38] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(WW) fglrx(0): could not detect X server version (query_status=-1)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit for fglrx driver
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 13, (OK)
drmOpenByBusid: drmOpenMinor returns 13
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb76d8000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.60.3
(II) fglrx(0):     Date: Apr  1 2009
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.28-11-server
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01004000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1280) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2000
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 1.4.99.906, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): UVD2 feature is available 
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(==) fglrx(0): Using software cursor
(II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) fglrx(0): atiddxDisplayScreenLoadPalette: numColors: 256
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(II) fglrx(0): Setting screen physical size to 325 x 260
swlDalGetDisplayIndex:ERROR: The number of Active Displays is 0 
swlDalGetDisplayIndex:ERROR: The number of Active Displays is 0 
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0


```

---

### Post by Luiggipro on 2009-04-29
> **BubuXP said:**
> From this thread:
[http://ubuntuforums.org/showthread.php?t=1133844](http://ubuntuforums.org/showthread.php?t=1133844)


I have same GPU as your and all is working fine in Jaunty with fglrx.


How I resolved:

Reinstalled a clean copy of Jaunty.
After applying updates, I opened Synaptic and removed all xserver-xorg-* useless packages (related to other VGA). Here's the list:
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-intel
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-voodoo

After, I installed the xorg-driver-fglrx package and all dependencies, via Synaptic.
Next step, opened a terminal and typed:
sudo aticonfig --initial -f
Finally, I crossed my fingers and reboot. And I'm still here

Compiz works fine and also Google Earth 5 from Medibuntu repository runs smooth (but with compiz or minimal effects enabled the earth start to flash and is unusuable).

why make it so complicate? My moms pc have a HD 3300 igp and I formatted with ubunu jaunty 32 bit, chose my video card and downloaded the drivers in ati website, ran ```
sudo sh ./"driver"
``` installed the driver (the installer has a gui) and then according to the driver manual I had to do this : ```
sudo /usr/bin/aticonfig --initial
``` and rebooted, and everything was working fine, compiz, games, etc. :guitar:

---

### Post by waspbr on 2009-04-29
I have an HD 3300 IGP and I tried your methods, still cannot enable desktop effects.

---

### Post by Luiggipro on 2009-04-29
> I have an HD 3300 IGP and I tried your methods, still cannot enable desktop effects. 

Oh, bad luck. I dont know why it doesnt work for you, maybe you could give me more information so I can help you :)

---

### Post by mendieta on 2009-04-29
> **Luiggipro said:**
> Oh, bad luck. I dont know why it doesnt work for you, maybe you could give me more information so I can help you :)

Luiggi, if you look around on the web and in this forum, different people with the same ATI graphics cards have had different luck. That's why people are trying all sorts of funky stuff. I think what matters is the combination of software/hardware you have, not just the graphics card !

---

### Post by Luiggipro on 2009-04-30
> **mendieta said:**
> Luiggi, if you look around on the web and in this forum, different people with the same ATI graphics cards have had different luck. That's why people are trying all sorts of funky stuff. I think what matters is the combination of software/hardware you have, not just the graphics card !

yeah m8 I know, but I also had problems with older ati cards and nvidia in the past, so I kinda know a lil bit about setting up video cards in ubuntu, and theres always time to help other people right? :P

---

### Post by waspbr on 2009-05-01
essentially the card works, just not well. I have 2 PCs with ati on them , one with a HD 3850 AGP and another one with the IGP HD 3300.

I have tried to install via jockey, envy and manually and neither method has made it possible to enable compiz, honestly I don't miss compiz that much, on top of that I can't even watch videos, the computers slow down to a crawl in fullscreen.  If I wanna watch videos I need to either use my nvidia powered laptop or boot into my windows partition. 

CCC seems to recognise my cards correctly. I am not really sure where the problem lies. 

glxinfo gives:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3300 Graphics
OpenGL version string: 2.1.8591
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_color_buffer_float, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_instanced, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_transpose_matrix, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_buffer, GL_EXT_copy_texture, 
    GL_EXT_draw_buffers2, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_swizzle, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_copy_depth_to_color, 
    GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_WIN_swap_hint, 
    WGL_EXT_swap_control

65 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xae 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon

71 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x43  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0xae  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon
0xae  0 tc  0 128  0    y  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Ncon
0xae  0 tc  0 128  0    .  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Ncon
0xae  0 tc  0 64  0    y  . 16 16 16 16  0 24  0  0  0  0  0  0 0 None
0xae  0 tc  0 64  0    .  . 16 16 16 16  0 24  0  0  0  0  0  0 0 None
0xae  0 tc  0 32  0    y  . 11 11 10  0  0 24  0  0  0  0  0  0 0 None
0xae  0 tc  0 32  0    .  . 11 11 10  0  0 24  0  0  0  0  0  0 0 None

```

lspci gives 

```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics

```


glxgears seems to work well

```
7937 frames in 5.0 seconds = 1587.312 FPS
7996 frames in 5.0 seconds = 1599.090 FPS
7971 frames in 5.0 seconds = 1594.016 FPS
7891 frames in 5.0 seconds = 1578.170 FPS

```


Not sure what I could do here, as far as I can see my options lie at the 9.5 drivers...

---

### Post by mendieta on 2009-05-01
> **waspbr said:**
> 
Not sure what I could do here, as far as I can see my options lie at the 9.5 drivers...

Yes, this is the first time I use ATI, but it seems they release about once a month. It irritates me that there is no way to post a bug for the binary driver, oh well! The opensource radeon works great here for everything but games (meaning, web-browsing, HD content in Hulu, etc)

---

### Post by Worp8d on 2009-05-03
> **BubuXP said:**
> From this thread:
[http://ubuntuforums.org/showthread.php?t=1133844](http://ubuntuforums.org/showthread.php?t=1133844)


I have same GPU as your and all is working fine in Jaunty with fglrx.


How I resolved:

Reinstalled a clean copy of Jaunty.
After applying updates, I opened Synaptic and removed all xserver-xorg-* useless packages (related to other VGA). Here's the list:
xserver-xorg-video-all
xserver-xorg-video-apm
xserver-xorg-video-chips
xserver-xorg-video-cirrus
xserver-xorg-video-intel
xserver-xorg-video-mga
xserver-xorg-video-neomagic
xserver-xorg-video-nv
xserver-xorg-video-openchrome
xserver-xorg-video-rendition
xserver-xorg-video-s3
xserver-xorg-video-s3virge
xserver-xorg-video-savage
xserver-xorg-video-siliconmotion
xserver-xorg-video-sis
xserver-xorg-video-sisusb
xserver-xorg-video-tdfx
xserver-xorg-video-trident
xserver-xorg-video-tseng
xserver-xorg-video-voodoo

After, I installed the xorg-driver-fglrx package and all dependencies, via Synaptic.
Next step, opened a terminal and typed:
sudo aticonfig --initial -f
Finally, I crossed my fingers and reboot. And I'm still here.

I have an ATI Mobility Radeon HD 3200 in an Asus F5 laptop and this method worked perfectly for me.  Thanks!

---

### Post by djchandler on 2009-05-07
Just upgraded to 9.04 this evening. So far so good with a couple of caveats.

Have HD 3200 in 780G chip set on my MB. For now I'm using the fglrx driver. Here is the info output by Catalyst Control Center (amd-cccle) which says I'm running version 010.087.000.001.000000.

Compiz runs but I can't left-click my mouse. This persists from a previous version of the driver. I don't think ATI has any intention of supporting Compiz. Everything works fine until I activate Screen Effects (Compiz).

There's a semi-transparent graphic in the lower right corner of the screen that has the AMD logo and signage that says:
Testing use
    only
Unsupported
  hardware

Apparently the graphic is embedded in the driver. Can't get it with a screenshot.

This is a mother board with an AMD 780G chipset, SB700. It's new, but the chipset has been available for about a year. So I guess that means AMD doesn't support their own hardware. I've been a loyal AMD customer for years. Something needs to change or I won't be the next time I go CPU and motherboard shopping.

I'm going to open synaptic and try rolling back the driver. I may go for installing the ATI driver downloaded from their site otherwise.

Stay tuned.

PS That was my bios version number up there. Sorry about that, but I obviously had hold of something I shouldn't have tried to use. But that's what got downloaded during the Jaunty upgrade. I blame my error on too much going on at once. My daughter's in labor, getting ready to deliver her second child and my fifth grandchild. This is what I'm doing to calm myself. HA-HA!

---

### Post by djchandler on 2009-05-07
I'm back. Here's the latest.

I am now running:

2D Driver - 8.60.3
CCC      - 2.6
OpenGL      - 2.1.8591

They know Compiz does not work with their driver. It's a known issue, and they don't seem inclined to resolve it. If this is a deal breaker for you, either get a different brand video card or find another OS. Right now ATI only claims to support Red Hat, Suze and Ubuntu.

I downloaded ati-driver-installer-9-4-x86.x86_64.run and ran it from the cli using sudo. It actually works, but you need to restart X before it is configurable. Luckily my previous settings were intact, so all I had to do was re-start the X server.

You can drill down to your specific  [ATI Catalyst&#8482; Proprietary Display Driver]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English") and get instructions from ATI.
[]("http://support.amd.com/us/gpudownload/Pages/index.aspx")
The following is a quote from the end of the instructions:
> Known Issues

The following section provides a brief description of known issues associated with the latest version of ATI CatalystTM Linux software suite. These issues include:


[LIST]
[*]Resuming from sleep the display connected to add-on card remains off in some dual-head mode configurations
[*]System may stop functioning while trying to start a third X-session on some ASICs System may become unresponsive when toggling between virtual terminals in multi-head configuration with application running
[*]Catalyst Control Center: The primary display is not identified when using the Identify Displays button
[*]Error may occur while setting the TV geometry
[*]The display might not scale appropriately for each resolution/refresh rate change through amdcccle
[*]Starting X with a second hotplugged display may cause segmentation fault
[*]Game corruption might be observed in full screen when 2 monitors are connected and RandR 1.2 is enabled
[*]Video playback may exhibit corruption when desktop effects are enabled and Composite is not explicitly disabled
[*]TV screen corruption may be visible while starting the X-server on some ASICs
[*][SUSE11] The display might not turn off while disabling the output
[*][Ubuntu 8.10] Startx may fail with no monitor connected and RandR1.2 enabled
[*][Ubuntu 8.10] System may become inoperative when starting X on surround view system
[/LIST]
Since there is no mention of Ubuntu 9.04, we can assume they are behind somewhat. It wouldn't be surprising that they are way more concerned about getting ready for the Windows 7 launch.

On issue #8  (video playback) I think they mean Compiz instead of Composite. Their programmers don't seem too experienced when it comes to Compiz or it may be just a language problem.

Good luck all. As for me, I'm sticking with the fglrx driver. As long as I don't use Compiz, it works. This isn't my first problem with Compiz. I just moved of a box with older Nvidia graphics and chipset. It wasn't perfect either. So hang in there everybody.

:)

---

### Post by *uu on 2009-06-09
Doh!

Yesterday I had a freshly installed and updated Jaunty up and running, using the HD 3200 with the fglrx driver and with Compiz activated. Then I installed a lot of programs and packages, and suddenly I couldn't log to GDM anymore after a reboot. I got stuck at the black screen with some garbled colored pixels at the top. Sometimes I could access the virtual terminals (CTRL+ALT+F1), sometimes I couldn't. And often when I tried, Ubuntu froze completely so I couldn't even connect via SSH from another computer to at least reboot without brute force reset button.

I spent all night and day trying to figure out what went wrong, de- and reinstalling, activating and deactivating fglrx dozens of times from the repos and from the latest ATI package, following the hints and tips from this thread and in other forums, trying the Guides from the UbuntuWiki and what not, but always failing and going back to the 'radeon' driver, which was the only way to at least get into GNOME.

Now I finally found the cause of this error: Somehow I accidentally installed the package 'linux-image-2.6.28-11-server' and some related headers and image packages, and as this was the first one in the Startup Manager (Grub config GUI), I set the 'kernel 2.6.28-11-server' as the default operating system. I guess I was a little too tired when I did that, :oops: but I didn't notice that one was named *-generic and the other one *-server. Well, long story short, I booted into the server version all the time without noticing, and apparently there's no way to get the fglrx drivers working with it. I just noticed my mistake in Synaptic's history, removed the *-server image, booted into the *-generic image after re-activating fglrx and voilà, I got my working Ubuntu back. #-o Compiz is again working like a charm, as it did before my accident. The only annoying thing left is that weird screen flickering when running a video or even only a browser in fullscreen mode -- but that is a problem for another day, I guess.

So, in case you're as well struggling with this friggin' black screen with the purple-ish pixel patterns at the top, you might wanna check if maybe you also found it a wise idea to install the *-server image and boot into it. I for one will from now on look a little closer before "upgrading" to a new kernel image and when setting up all my proggies in a fresh system. :p

Hope this might save someone some pointless struggle.

Regards and good night.
*uu

---

### Post by Alka-Seltzer PLUS on 2009-06-10
Hola !

I am also not sure if I have the drivers installed :O
Everithing works out of the box but....
take a look to my xorg.conf:

> 
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1680x1050" "1400x1050" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
this is my glxgear output with compiz disabled:

> 
4703 frames in 5.0 seconds = 940.232 FPS
5013 frames in 5.0 seconds = 1002.540 FPS
4745 frames in 5.0 seconds = 948.996 FPS
4513 frames in 5.0 seconds = 902.599 FPS
4793 frames in 5.0 seconds = 957.965 FPS
5849 frames in 5.0 seconds = 1169.742 FPS
7426 frames in 5.0 seconds = 1485.172 FPS
7796 frames in 5.0 seconds = 1558.947 FPS
7904 frames in 5.0 seconds = 1580.707 FPS
8144 frames in 5.0 seconds = 1627.759 FPS
8389 frames in 5.0 seconds = 1677.754 FPS
with compiz enabled:

> 
502 frames in 5.0 seconds = 100.335 FPS
565 frames in 5.0 seconds = 112.965 FPS
623 frames in 5.0 seconds = 124.532 FPS
624 frames in 5.0 seconds = 124.786 FPS
565 frames in 5.0 seconds = 112.762 FPS
571 frames in 5.0 seconds = 114.036 FPS
415 frames in 5.0 seconds = 82.911 FPS
213 frames in 5.0 seconds = 42.484 FPS
338 frames in 5.0 seconds = 67.553 FPS
431 frames in 5.0 seconds = 86.144 FPS
350 frames in 5.0 seconds = 69.881 FPS
and the output of lspci:

> 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
I installed the driver from ati's site, but I have not enabled propietary from System->Administration->Hardware Drivers : shall I ? Is this ****** driver installed properly or not ????? I have all the xorg.* packages installed yet ...

---

### Post by twosticks on 2009-06-11
So I have a slightly different problem than I've seen discussed anywhere (and I've been searching for awhile.) I have an AMD 780G chipset w/ HD 3200 embedded video and was working in intrepid. I upgraded to jaunty and installed the newest version of ati's driver from their site. (Actually, I've done it a few times with the same results, more or less. My last attempt followed this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually").) 

So anyway technically the driver is working. I'm writing this message using the upgraded system. I get 1200+ fps from glxgears. BUT, there's this random, weird, corruption of the screen that comes and goes. When it's light, there are some half dozen or so lines of pixels with the first 100-300 pixels are black, and shifted across the screen halfway or so. At it's worst, and it's seemingly random when this happens, nearly the whole display will do this and is almost completely unusable at that point. It's hard to explain and I"m not sure what to call the problem in order to search efficiently for a workaround/fix. I'm attaching a picture too since it's probably easier to see it:

[http://brightstatic.com/wp-content/uploads/2009/06/2009-06-10-201541.jpg]("http://brightstatic.com/wp-content/uploads/2009/06/2009-06-10-201541.jpg")

Since this is a media center pc I also have tv card, lirc, and other misc drivers loaded, and I started wondering if they were conflicting with something. I tried unloading them but it didn't seem to have any effect. I'm not running Compiz. I'm not even running Gnome, just XFCE. I've tried as many HD3200-specific settings I can find online but nothing seems to make a difference. Here's my xorg.conf:

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

```

---

### Post by oliver.greg@gmail.com on 2009-06-11
I too am new to ATI's crap linux support..  I have no need to have games or any of the "fancy" compiz eyecandy, but I have been reliant on a few things that rely on compositing to be enabled..

I was seeing all of the fullscreen slowdowns, and minimize/maximize issues as posted here..

I ended up using 9.5 ATI driver, disabling compiz and running the metacity compositor..  This immediately cleared up all of my issues and my composite apps run just fine now..

Using aticongig, I can also get dual head, etc working even though the catalyst interface does not enable them until after aticonfig turns it on...

-Greg

---

### Post by oliver.greg@gmail.com on 2009-06-15
OK - after a week or so of fiddling and researching, I have finally come up with a stable working composited desktop with ATIs crap linux driver..  I just upgraded to 9.6, but it was working fine with 9.5..

Here are the few simple steps I did...

Install the ATI driver, and:

rm /etc/ati/amdpcsdb
aticonfig --initial=dual-head --overlay-type=Xv
aticonfig --tv-format-type=NTSC-M

--reboot for new kernel module--

aticonfig --set-pcs-str="DDX,EnableRandr12,FALSE"
aticonfig --dtop=horizontal

logout/in

It has been running stable since with Metacity compositing off and compiz in full..  I have it working on 2.6.28-11 (for MythTV) and the current jaunty kernel - x86_64 BTW...

-Greg

---

### Post by krackersk on 2009-06-20
Anybody had issues with the screen constantly shaking? This only happens when I'm using HDMI, with analog input it works fine.

I'm using linux mint (based on Ubuntu 9.04) and ATI Radeon HD 3200. I initially had black screen issues when loading up but installed Catalyst 9.6 and that fixed that but left me with a shakey screen.

---

### Post by raymondvillain on 2009-06-26
Built a machine from a gigabyte mobo with AMD phenom II quad core and built in Radeon 3200 graphics.

Installed Jaunty 64 bit from live CD.

Downloaded ATI's 9.6 drivers and installed them per AMD/ATI instructions.

Things work pretty well for me.  I don't use games or fancy graphics, so I don't need much.  But I would like to fool around with compiz and desktop effects.

Can't seem to get compiz running.  The only choice I have in desktop effects is "none".

I know compiz is installed, if I go to synaptics and search for it all the boxes are indicating its presence.

Any suggestions?

P. S.  I did not have simple-cssm and some other stuff installed.  Now it works fine.

---

### Post by Joshw91 on 2009-07-27
> **oliver.greg@gmail.com said:**
> OK - after a week or so of fiddling and researching, I have finally come up with a stable working composited desktop with ATIs crap linux driver..  I just upgraded to 9.6, but it was working fine with 9.5..

Here are the few simple steps I did...

Install the ATI driver, and:

rm /etc/ati/amdpcsdb
aticonfig --initial=dual-head --overlay-type=Xv
aticonfig --tv-format-type=NTSC-M

--reboot for new kernel module--

aticonfig --set-pcs-str="DDX,EnableRandr12,FALSE"
aticonfig --dtop=horizontal

logout/in

It has been running stable since with Metacity compositing off and compiz in full..  I have it working on 2.6.28-11 (for MythTV) and the current jaunty kernel - x86_64 BTW...

-Greg
Wow, that worked like a charm, it's a miracle! I can use blender, enable my screensaver, etc., all with compiz enabled... except for a few glitches I noticed... my gfx card is the radeon hd 3200. But I'm very glad it's working better now!

---

### Post by *uu on 2009-07-27
[quote=Joshw91]except for a few glitches I noticed...[/quote]
The major glitches that I still face regularly, when Compiz is activated:

1. Video in fullscreen flickers when Totem Movie Player shows or fades out the fullscreen controls. Same when I do a photo presentation in fullscreen mode (using GNOME standard eog): the screen flickers like mad when controls fade in at the top of the screen or when switching to another picture, and sometimes even for no apparent reason. Oh, yeah, and most GL screensavers show the same annoying flickering, when Compiz is on, but then it flickers permanently. All in all, video and screensaver performance is rather slow with Compiz activated.

2. Flash video (like YouTube and similars) will not work in fullscreen mode. When trying, the screen flashes once, but the video remains running inside its flash frame on the web page.

3. Whenever Compiz has been running for a while (sometimes it takes hours, sometimes only minutes), it seems to sort of freeze suddenly, meaning that the screen suddenly appears to not get refreshed anymore. It flashes once and looks empty or partially empty, sometimes some of the previously opened windows are still visible, but not at the position on the screen where they were before. Then I can still see the mouse cursor change when hovering e.g. over the edge of a window underneath (changes to resize arrow) or over a text box (changes to the I symbol), but the window is actually displayed at another position and will visible there even after I closed or minimized the window -- assuming that I found the close or minimize button by blindly clicking where I expect them to be. Sometimes even only a part of the screen is affected by this at first, only to later on affect the whole screen. The only way to get to see the actual current state of the screen is to switch back and forth between another virtual console and CTRL+ALT+F7. 
To get around this mess, I have to disable Compiz (with the Compiz Icon and the switching between terminals mentioned above, or by opening a new terminal via a shortcut and blindly typing "metacity --refresh &"). And I cannot switch Compiz back on afterwards without a complete system restart. If I would, it would only get back to the frozen-like empty screen. Restarting only X doesn't resolve it, either. Somehow especially this glitch feels like some sort of a graphics buffer overflow. 

4. In driver version 9.5 videos would often but sporadically completely freeze the screen, when switching to fullscreen or back to windowed video, or sometimes even when the movie is just running. In those cases both the mouse and the keyboard remained completely unresponsive. I could sometimes connect via SSH to the machine and restart X. If SSH didn't succeed, I could only press the power button and hope everything would at least shut down gracefully. Or the reset button in the worst cases.
Not sure if this was fixed with version 9.6 or 9.7, or maybe with some setting in my xorg.conf that I added since than. I haven't really dared to provoke such a crash anymore, I always turn of Compiz to watch movies now, which really sucks.

Does anyone experience the same with the onboard HD 3200? And did anyone find a solution? 9.7 didn't change anything for me, neither did 9.6 and 9.5 before. Before every upgrade I completely removed the old driver versions as suggested by ATI. This has really become annoying after a while, I'd like Compiz to finally work and I'm a short step away from getting myself a working NVidia device (any suggestions here? ;)).

Here's my xorg.conf, in case someone knows some voodoo. :P
```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Option      "UseFBDev" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "UseFastTLS" "1"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

Regards and good night.
*uu

---

### Post by Joshw91 on 2009-07-28
> ***uu said:**
> The major glitches that I still face regularly, when Compiz is activated:
Yes, I still have those exact same problems. My previous post was a false alarm, because I had forgot that blender worked in windowed mode before anyway.. And so I noticed that many opengl and video applications have still NOT been working correctly. I usually just use windows when I want to use those applications, because I hate having to disable compiz and reconfigure everything again when I reenable it... I'm not sure how you would replace an onboard graphics chip on a laptop, but that's what I would do if I could. 
I once had problems with a (really) old ati card that now seems to work just fine with compiz out of the box in jaunty jackelope. Hopefully the driver gets fixed in the near future!

---

### Post by *uu on 2009-07-28
> **Joshw91 said:**
> Hopefully the driver gets fixed in the near future!
I just sent a mail to ATI support with a link to this thread and the explanations above. Let's see if that does anything good...

---

### Post by LostinSpacetime on 2009-08-05
> ***uu said:**
> 
1. Video in fullscreen flickers when Totem Movie Player shows or fades out the fullscreen controls. Same when I do a photo presentation in fullscreen mode (using GNOME standard eog): the screen flickers like mad when controls fade in at the top of the screen or when switching to another picture, and sometimes even for no apparent reason. Oh, yeah, and most GL screensavers show the same annoying flickering, when Compiz is on, but then it flickers permanently. All in all, video and screensaver performance is rather slow with Compiz activated.
*uu

U can get rid of the flickering by deactivating "unredirect fullscreen windows" in the general part of Compiz configuration manager.

---

### Post by Joshw91 on 2009-08-05
> **LostinSpacetime said:**
> U can get rid of the flickering by deactivating "unredirect fullscreen windows" in the general part of Compiz configuration manager.
it didn't help

---

### Post by xzero1 on 2009-08-05
I have the hd 3300IGP, fairly close to yours. The original stock Jaunty driver gave me big problems which all went away after installing 9.6 and doing a little tweaking. I don't use or have a sideband memory option, if that has any relevance. Also note that accelerated video (-xv) only works fullscreen. Additional info is here: [http://ubuntuforums.org/showthread.php?t=1224509](http://ubuntuforums.org/showthread.php?t=1224509)

---

### Post by LostinSpacetime on 2009-08-06
> **Joshw91 said:**
> it didn't help

I have exactly the same hardware (HD3200) and same OS (Ubuntu 9.04). It would be weird if it would work for me and not for you. The latest driver (Catalyst 9.7) fixed some XV issues for me. Maybe you give it a try. Good luck! :)

---

### Post by *uu on 2009-08-06
> **LostinSpacetime said:**
> U can get rid of the flickering by deactivating "unredirect fullscreen windows" in the general part of Compiz configuration manager.

Thank you, LostinSpacetime, very much for this hint. For me, this did, indeed, help to get rid of the flickering in some applications. Videos (totem) and picture presentations in fullscreen (eog) apparently do now work without flickering when Compiz is activated. Even flash video in fullscreen did work in a test I just did. :) Though, video in general seems to take a lot of CPU and sometimes lags a little when there's a lot of "motion" in the video in fullscreen mode. I suspect that with Compiz activated, I can still forget about watching HD quality videos. My system did already struggle hard without Compiz when fullscreen rendering such a film. Didn't test that now, though, as I don't currently have an HD vid at hand.

Strange, though: The GL screensavers are now rendered flawlessly in fullscreen preview mode, but at least some of them (e.g. "Skyrocket"; I only tested a few for now) still flicker once they get started for real when the machine is idle. I have to deactivate Compiz to have them work fine...

> **LostinSpacetime said:**
> I have exactly the same hardware (HD3200) and same OS (Ubuntu 9.04). It would be weird if it would work for me and not for you.

I suspect that the driver doesn't work all the same on the different architectures the HD 3200 is integrated with. So here are my system specs, for comparison:
- HD 3200 integrated on ASUS M3A78 PRO mainboard with AMD X4 9650 processor
- Graphics RAM 128MB of 4GB shared memory (currently, but I had same issues with up to 512MB, didn't notice any differences, neither for the better nor worse)
- Ubuntu 9.04 x86_64 with linux kernel 2.6.28-14
- ATI Catalyst version 9.7 (I think -- apparently it was not changed or overwritten by the kernel update two day ago)
- Screen resolution 2048 x 1152 @ 60 Hz

Now I hope that those screen-buffer-like issues mentioned above will get fixed sometime soon, as this is a major pain in the behind... :D

BTW: So far no reply to my email to ATI/AMD, except that it has been forwarded to AMD's linux dev team.

Regards,
*uu

---

### Post by xzero1 on 2009-08-06
> I suspect that the driver doesn't work all the same on the different architectures the HD 3200 is integrated with.I tend to agree with this as the actual motherboard implementations may differ a bit, still there are many xorg options which could make a difference. One thing you might try is to post your xorg log. Maybe by comparing this to a 'normal' log someone may spot something interesting.

---

### Post by LostinSpacetime on 2009-08-07
[QUOTE=*uu]Thank you, LostinSpacetime, very much for this hint. For me, this did, indeed, help to get rid of the flickering in some applications. Videos (totem) and picture presentations in fullscreen (eog) apparently do now work without flickering when Compiz is activated. Even flash video in fullscreen did work in a test I just did. :)[/QUOTE]

Glad I could help. :D Actually I had the same problem until yesterday on my laptop and after reading your post I got the idea (don't ask why) that it might be fixed by that.

[QUOTE=*uu]
- ATI Catalyst version 9.7 (I think -- apparently it was not changed or overwritten by the kernel update two day ago)[/QUOTE]

If you installed the driver via the built packages, then you don't have to bother about kernel updates, since it has Dynamic Kernel Module Support (DKMS).

---

### Post by markbuntu on 2009-08-07
Yes, these days a new kernel will build the fglrx kernel modules automagically if you only have one version nstalled. If the kernel detects more than one kernel modules version it will not build them. This is why it is so important to remove old drivers before installing new ones.

---

### Post by boarder428 on 2010-01-17
Great post, worked for me aswell except I did'nt take the time to remove all the other "useless drivers"

---

