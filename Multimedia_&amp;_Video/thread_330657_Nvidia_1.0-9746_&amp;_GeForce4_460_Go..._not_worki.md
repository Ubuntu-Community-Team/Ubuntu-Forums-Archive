---
title: "Nvidia 1.0-9746 &amp; GeForce4 460 Go... not working?"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by daniel1988 on 2007-01-03
Driver was intalled following this guide: [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)   & this one [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)
Lupine repository

```
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA(0): The NVIDIA GeForce4 460 Go GPU installed in this system is
(WW) NVIDIA(0):     supported through the NVIDIA 1.0-96xx Legacy drivers.
(WW) NVIDIA(0):     Please visit http://www.nvidia.com/object/unix.html for
(WW) NVIDIA(0):     more information.  The 1.0-9746 NVIDIA driver will ignore
(WW) NVIDIA(0):     this GPU.  Continuing probe... 
(EE) No devices detected.

Fatal server error:
no screens found
```
Whole /var/log/Xorg.0.log [here]("http://paste.ubuntu-nl.org/343/")

Any clue what happens here? :-k  Is this a bug or Nvidia proprietary drivers from 97xx series doesn't support GF4 GPU series? If this the second is the case, how to add to Synaptic >=9629 <97xx driver?

Cheers,
Daniel

---

### Post by tseliot on 2007-01-03
Your card is not supported by the latest nvidia driver (and the 97xx series in general).

Try envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Envy will select the driver for your card (96xx) and install it for you

---

### Post by daniel1988 on 2007-01-04
I tried, but as long as cs.archive.ubuntu.com/ubuntu is inactive, I can't finish the instalation. DNS translates that into 147.91.8.38, but it can't acces that IP (maybe the problem resides in my ISP's DNS server....)

Thanks for the replay

--Daniel

---

### Post by daniel1988 on 2007-01-04
The installation process of nvidia drivers successfully finished (nice script :) ) 96.31 is currently installed. There is one issue: after booting the system, when GDM loads, there is only white screen like [this]("http://img443.imageshack.us/img443/5905/nvidiaew6.jpg") < link to the image showing how it looks like.

The only way to kill this nag screen is to press ctrl+alt+f1, log in there, sudo rm /tmp/.X0-lock and then startx < after this, nvidia logo is shown, gnome session starts and everyting goes fine: ```
$ glxinfo | grep direct
direct rendering: Yes

```
New /var/log/Xorg.0.log.old [here]("http://paste.ubuntu-nl.org/507/") & /etc/X11/xorg.conf [here]("http://paste.ubuntu-nl.org/509/").

Any idea how to solve this?

--Daniel

P.S. I tried to *sudo /etc/init.d/gdm stop*... after executing startx, the white screen is shown and there is no way to remove it.

Edit: not sure, but this could be usefull: *diff -U6 /var/log/Xorg.0.log.old /var/log/Xorg.0.log*
```
--- /var/log/Xorg.0.log.old	2007-01-05 16:02:50.000000000 +0100
+++ /var/log/Xorg.0.log	2007-01-05 16:03:05.000000000 +0100
@@ -8,13 +8,13 @@
 	Before reporting problems, check http://wiki.x.org
 	to make sure that you have the latest version.
 Module Loader present
 Markers: (--) probed, (**) from config file, (==) default setting,
 	(++) from command line, (!!) notice, (II) informational,
 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
-(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  5 15:56:29 2007
+(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  5 16:03:04 2007
 (==) Using config file: "/etc/X11/xorg.conf"
 (==) ServerLayout "Default Layout"
 (**) |-->Screen "Default Screen" (0)
 (**) |   |-->Monitor "Generic Monitor"
 (**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 460 Go]"
 (**) |-->Input Device "Generic Keyboard"
@@ -69,13 +69,13 @@
 (II) Loading font Bitmap
 (II) LoadModule: "pcidata"
 (II) Loading /usr/lib/xorg/modules/libpcidata.so
 (II) Module pcidata: vendor="X.Org Foundation"
 	compiled for 7.1.1, module version = 1.0.0
 	ABI class: X.Org Video Driver, version 1.0
-(++) using VT number 7
+(--) using VT number 9
 
 (II) PCI: PCI scan (all values are in hex)
 (II) PCI: 00:00:0: chip 8086,1a30 card 1179,0001 rev 04 class 06,00,00 hdr 00
 (II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 04 class 06,04,00 hdr 01
 (II) PCI: 00:1d:0: chip 8086,2482 card 1179,0001 rev 02 class 0c,03,00 hdr 00
 (II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 42 class 06,04,00 hdr 01
@@ -407,31 +407,28 @@
 (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
 (**) NVIDIA(0): Option "ExactModeTimingsDVI" "TRUE"
 (**) NVIDIA(0): Option "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
 (**) NVIDIA(0): Enabling RENDER acceleration
 (WW) NVIDIA(0): Unrecognized ModeValidation token "NoEdidDFPMaxSizeCheck";
 (WW) NVIDIA(0):     ignoring.
-(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
 (II) NVIDIA(0): NVIDIA GPU GeForce4 460 Go at PCI:1:0:0 (GPU-0)
 (--) NVIDIA(0): Memory: 32768 kBytes
 (--) NVIDIA(0): VideoBIOS: 04.17.00.59.d3
 (II) NVIDIA(0): Detected AGP rate: 4X
 (--) NVIDIA(0): Interlaced video modes are supported on this GPU
 (--) NVIDIA(0): Connected display device(s) on GeForce4 460 Go at PCI:1:0:0:
-(--) NVIDIA(0):     CRT-0
 (--) NVIDIA(0):     TOSHIBA Internal Panel (DFP-0)
-(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
 (--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): 224.0 MHz maximum pixel clock
 (--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): Internal Dual Link LVDS
-(II) NVIDIA(0): Assigned Display Device: CRT-0
+(II) NVIDIA(0): Mode Validation Overrides for TOSHIBA Internal Panel (DFP-0):
+(II) NVIDIA(0):     NoVesaModes
+(II) NVIDIA(0): Assigned Display Device: DFP-0
 (II) NVIDIA(0): Validated modes:
 (II) NVIDIA(0):     "1024x768"
 (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
-(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
-(WW) NVIDIA(0):     from CRT-0's EDID.
-(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
+(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
 (--) Depth 24 pixmap format is 32 bpp
 (II) do I need RAC?  No, I don't.
 (II) resource ranges after preInit:
 	[0] 0	0	0xd7f80000 - 0xd7ffffff (0x80000) MX[B]
 	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
 	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
@@ -589,8 +586,6 @@
 	No such file or directory.
 Error opening /dev/wacom : No such file or directory
 (II) Configured Mouse: ps2EnableDataReporting: succeeded
 Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
 Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
 Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
-AUDIT: Fri Jan  5 16:02:50 2007: 3925 X: client 4 rejected from local host
-  Auth name: MIT-MAGIC-COOKIE-1 ID: -1

```

---

### Post by daniel1988 on 2007-01-05
bump (really need to get this to work properly)

---

### Post by tseliot on 2007-01-05
can you post the content of your /etc/X11/xorg.conf ?

---

### Post by daniel1988 on 2007-01-05
I've already posted (take a look at post #4) ;)
[http://paste.ubuntu-nl.org/509/](http://paste.ubuntu-nl.org/509/)

---

### Post by tseliot on 2007-01-05
Did you try without these lines? 
```
    Option         "ExactModeTimingsDVI" "TRUE"
    Option         "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
```

---

### Post by daniel1988 on 2007-01-05
> **tseliot said:**
> Did you try without these lines? 
```
    Option         "ExactModeTimingsDVI" "TRUE"
    Option         "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
```

Sure... same thing

---

### Post by tseliot on 2007-01-05
You might try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by daniel1988 on 2007-01-05
> **tseliot said:**
> You might try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)
I'll try. [Edit]Done:  [http://www.nvnews.net/vbulletin/showthread.php?p=1120035#post1120035](http://www.nvnews.net/vbulletin/showthread.php?p=1120035#post1120035) [/Edit]

Acording to this: [http://albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION](http://albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION) (Problems section)
7) If you own a GeForce4 420/440 Go or a GeForce4 MX 440 you should follow these steps:
I've tried all 4 combinations, no success :mad: 

Could this be a GDM misconfiguration/bug? I'm using newest version available in ubuntu repos (2.16.1-0ubuntu4.1). After killing GDM, nvidia driver works as expected.


--Daniel

---

### Post by daniel1988 on 2007-01-06
Problem solved: [http://www.nvnews.net/vbulletin/showthread.php?p=1121320&posted=1#post1121320](http://www.nvnews.net/vbulletin/showthread.php?p=1121320&posted=1#post1121320)

Thank you for pointing me in the right way

--Daniel

---

### Post by albertlash on 2008-01-30
I too got the GeForce 460 working with the NVIDIA 9631 driver. It was a serious pain to compile and install, but it works now. The FPS is not great at 300 FPS (with CPU assistance turned off) but it powers 1680x1050 widescreen! :-)

---

