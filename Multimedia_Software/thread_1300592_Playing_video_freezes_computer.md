---
title: "Playing video freezes computer"
date: 2009-10-25
forum: Multimedia Software
---

### Post by mask13 on 2009-10-25
Ok, I am fairly new to Linux, about 8 hours to be exact. So far I'm picking up on things pretty well, but I have tried to play video I copied from my external hard drive, and it freezes the computer. I tried the formats .avi, .mp4, and .mkv but they all freeze and I have to reboot. I tried all of those formats with mplayer and VLC. Please tell me there's a fairly simple way to fix this, dare I consider going back to... Vista... I am running Ubuntu 8.04 on a Lenovo Y430 laptop with 3 gigs of ram. Any help I can get would be most appreciated. (And please keep it detailed, I've never done anything like this before.)


:guitar:Rock on.

---

### Post by MasterProg on 2009-10-25
Does Totem (default player, can be found in Applications -> Sound & Video -> Movie Player) freeze up?

---

### Post by laceration on 2009-10-25
It is probably because when you first install Ubuntu it does not install "non-free" codecs that would enable you to play these files.

This will help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mask13 on 2009-10-25
MasterProg, I forgot Totem. Yes, it also froze.

laceration, I don't have time to work right now, but I'll be sure to get back on how it works for me.

Thanks both of you.

---

### Post by mask13 on 2009-10-26
> **laceration said:**
> It is probably because when you first install Ubuntu it does not install "non-free" codecs that would enable you to play these files.

This will help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


I did everything that would apply to me on that page, now VLC turns my background blue and green, plays about 5 seconds of audio, then completely freezes the entire computer. mplayer turns blue where the video should be and freezes the entire computer. Totem did freeze everything, but now it freezes everything but the mouse.

 When I had Windows Vista (It sucked!) I never had things like this happen. Anything else anyone can think of to help me?

---

### Post by Lavahead on 2009-10-26
I am experiencing the exact same problem on a Toshiba Satellite notebook running Hardy. I posted the problem a few weeks ago in this same forum.

So far, I have not been able to locate the source of the problem. I reviewed the system logs after three [alt][sysreq]REISUB reboots last night from continual movie player freezes. The kernel and x.org did not report any abnormalities, so I assume that Gnome is the culprit. The freezing also occurs whether Compiz is on or off, and all movie players (Mplayer, Totem, VLC) are affected.

---

### Post by mask13 on 2009-10-26
> **Lavahead said:**
> I am experiencing the exact same problem on a Toshiba Satellite notebook running Hardy. I posted the problem a few weeks ago in this same forum.

So far, I have not been able to locate the source of the problem. I reviewed the system logs after three [alt][sysreq]REISUB reboots last night from continual movie player freezes. The kernel and x.org did not report any abnormalities, so I assume that Gnome is the culprit. The freezing also occurs whether Compiz is on or off, and all movie players (Mplayer, Totem, VLC) are affected.

Since I'm new to this (and I probably sound like an idiot for asking) but is there a way that I could replace GNOME with something else and see what happens? Or is there even anything else to replace GNOME with?

---

### Post by Lavahead on 2009-10-27
I believe that both KDE (used in Kubuntu) and Xfce (used in Xubuntu) desktops can be installed via Synaptic Package Manager. Once installed, then the alternative destop will be available under "Options" in the log-in screen.

I thought of installing Xfce to see whether the freezing problem would be solved. However, in the end, it might just be best to wait for the 10.04 LTS release in April 2010. I'll post any new developments if they come up.

---

### Post by mask13 on 2009-10-27
> **Lavahead said:**
> I believe that both KDE (used in Kubuntu) and Xfce (used in Xubuntu) desktops can be installed via Synaptic Package Manager. Once installed, then the alternative destop will be available under "Options" in the log-in screen.

I thought of installing Xfce to see whether the freezing problem would be solved. However, in the end, it might just be best to wait for the 10.04 LTS release in April 2010. I'll post any new developments if they come up.

I think I'll try it, just to see. I'll keep you updated if it works.

I couldn't find it in the Package Manager, but I found this. sudo aptitude update && sudo aptitude install xubuntu-desktop

It's going right now, so I will more than likely post back again in just a few.

---

### Post by mask13 on 2009-10-27
Well, that didn't go well. I did the same test as before, using a variety of formats in a variety of players. For each one, the same thing as before would happen with the addition of the screen going black. Well, I guess I'm going to go try KDE now and see what happens. Wish me luck somebody.

Well, I get the same thing with KDE as with GNOME. I guess I'll start looking up some newer releases and try them to see what happens. Thanks for the help everyone.

---

### Post by laceration on 2009-10-27
```
I am experiencing the exact same problem on a Toshiba Satellite notebook running Hardy.
```
I have an old, underpowered Toshiba Satellite notebook originally with Hardy, now running Karmic, with Xbuntu.  I never attempted Compiz for it.  It has never had problems with video.  That being said, if your machines satisfy basic hardware requirements, I don't think this problem would be caused by your choice of Desktop environment.

Sorry I am not expert enough to help you more, but it stands to reason that perhaps you should do some searching here on your video adapters and drivers.

Just like with the codecs, because of licensing issues, sometimes Unbuntu will not install better working propriety drivers.

---

### Post by Lavahead on 2009-10-28
I am not sure what mask13 has for a video card, but my Toshiba Satellite is using the basic Intel 94x series video processor which is well supported by the generic driver in Linux. So, that should not be an issue. I say "should not" becuae I don't really know.

From mask13's recent experience with installing dfferent desktops and not solving the problem, then neither the window manager (Metacity or Compiz) or the desktop environment (Gnome, KDE, Xfce) are the culprits. From what I can ascertain, the [ctrl][alt][Fn] are detected by X.org  and [alt][sysreq]REISUB is detected by the kernel. During the freeze, only the latter combination works, so the real problem may be X.org itself. I will recheck the logs.

Incidentally, the flash player in Firefox works just fine, which is even more puzzling.

---

### Post by laceration on 2009-10-28
My Toshiba has Ati video.  From what I've picked up by noticing various forum titles, Intel video can be very problematic, but I don't know any details of 94x series.  I'd start looking there.  Most likely problems of Xorg is the video isn't configured correctly, anyways.

---

### Post by Lavahead on 2009-10-29
Yes, I stand corrected.Apparently, the Intel driver has been a problem. However, it seems that the implementation on Hardy was pretty good. I also noticed that, starting with Hardy, the *xorg.conf* file is completely generic. However, upon checking the x.org log, the configuration was done correctly including enabling hardware acceleration and mapping out the correct size of video RAM.

Viewing the *Xsession-errors* file, though, was another story. Lots of different errors, but everything seems to work fine. Sadly, after a freeze and reboot, the *Xsession-errors* file is replaced with no archive of the old one.

Fortunately, I have found that mplayer can generate a log file using the command:

```
mplayer -v video_filename > mplayer.log 2>&1
```

So, I will run mplayer using that command to see what happens when the freeze occurs. I'll post the results, if there is anything new.

---

### Post by mask13 on 2009-10-29
I found a code for the terminal that was supposed to tell me about my video card. I don't know what most of this means, but this is what I got. I hope this helps you to help me.

 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

The last few posts have completely lost me... I did notice the vendor:Intel Corporation. Do Intel video cards not work with Linux? Should I go back to Windows just because that's what this was made for?

---

### Post by mask13 on 2009-10-29
I just came up with a thought... Since I never had problems when I was running Vista, could I set up VLC or some other media player in Wine (I've never actually used Wine, but I've read a little about it)? Could that allow me to play my videos?

---

### Post by laceration on 2009-10-29
> **mask13 said:**
> I just came up with a thought... Since I never had problems when I was running Vista, could I set up VLC or some other media player in Wine (I've never actually used Wine, but I've read a little about it)? Could that allow me to play my videos?
That seems like the Rube Goldberg solution to me
[http://en.wikipedia.org/wiki/Rube_goldberg](http://en.wikipedia.org/wiki/Rube_goldberg)

You guys gotta be looking on these forums for Intel video adapters help.

---

### Post by Lavahead on 2009-10-30
I have been slowly but surely going through the threads about X.org and Intel video drivers. There has been little about Hardy so far, though. And, I agree with laceration that using Wine to run a video player is a "Rube Goldberg" solution (although I had pondered the idea myself).

The System Log Viewer allows you to view the X.org log which provides all the information about the video driver and what got loaded. Here's mine (other stuff edited out):

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Monastery 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 29 18:01:27 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7


(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xd0200000/19, 0xc0000000/28, 0xd0300000/18, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xd0280000/19
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
(II) Active PCI resource ranges:
	[0] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[1] -1	0	0xd0103800 - 0xd01038ff (0x100) MX[B]
	[2] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[3] -1	0	0xd0104000 - 0xd0107fff (0x4000) MX[B]
	[4] -1	0	0xd0103000 - 0xd01037ff (0x800) MX[B]
	[5] -1	0	0x88000000 - 0x8800ffff (0x10000) MX[B]
	[6] -1	0	0xd0544000 - 0xd05443ff (0x400) MX[B]
	[7] -1	0	0xd0340000 - 0xd0343fff (0x4000) MX[B]
	[8] -1	0	0xd0280000 - 0xd02fffff (0x80000) MX[B](B)
	[9] -1	0	0xd0300000 - 0xd033ffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd0200000 - 0xd027ffff (0x80000) MX[B](B)
	[12] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[13] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[1] -1	0	0xd0103800 - 0xd01038ff (0x100) MX[B]
	[2] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[3] -1	0	0xd0104000 - 0xd0107fff (0x4000) MX[B]
	[4] -1	0	0xd0103000 - 0xd01037ff (0x800) MX[B]
	[5] -1	0	0x88000000 - 0x8800ffff (0x10000) MX[B]
	[6] -1	0	0xd0544000 - 0xd05443ff (0x400) MX[B]
	[7] -1	0	0xd0340000 - 0xd0343fff (0x4000) MX[B]
	[8] -1	0	0xd0280000 - 0xd02fffff (0x80000) MX[B](B)
	[9] -1	0	0xd0300000 - 0xd033ffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd0200000 - 0xd027ffff (0x80000) MX[B](B)
	[12] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[13] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
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
	[4] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[5] -1	0	0xd0103800 - 0xd01038ff (0x100) MX[B]
	[6] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[7] -1	0	0xd0104000 - 0xd0107fff (0x4000) MX[B]
	[8] -1	0	0xd0103000 - 0xd01037ff (0x800) MX[B]
	[9] -1	0	0x88000000 - 0x8800ffff (0x10000) MX[B]
	[10] -1	0	0xd0544000 - 0xd05443ff (0x400) MX[B]
	[11] -1	0	0xd0340000 - 0xd0343fff (0x4000) MX[B]
	[12] -1	0	0xd0280000 - 0xd02fffff (0x80000) MX[B](B)
	[13] -1	0	0xd0300000 - 0xd033ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0200000 - 0xd027ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0


(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[5] -1	0	0xd0103800 - 0xd01038ff (0x100) MX[B]
	[6] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[7] -1	0	0xd0104000 - 0xd0107fff (0x4000) MX[B]
	[8] -1	0	0xd0103000 - 0xd01037ff (0x800) MX[B]
	[9] -1	0	0x88000000 - 0x8800ffff (0x10000) MX[B]
	[10] -1	0	0xd0544000 - 0xd05443ff (0x400) MX[B]
	[11] -1	0	0xd0340000 - 0xd0343fff (0x4000) MX[B]
	[12] -1	0	0xd0280000 - 0xd02fffff (0x80000) MX[B](B)
	[13] -1	0	0xd0300000 - 0xd033ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0200000 - 0xd027ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[5] -1	0	0xd0103800 - 0xd01038ff (0x100) MX[B]
	[6] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[7] -1	0	0xd0104000 - 0xd0107fff (0x4000) MX[B]
	[8] -1	0	0xd0103000 - 0xd01037ff (0x800) MX[B]
	[9] -1	0	0x88000000 - 0x8800ffff (0x10000) MX[B]
	[10] -1	0	0xd0544000 - 0xd05443ff (0x400) MX[B]
	[11] -1	0	0xd0340000 - 0xd0343fff (0x4000) MX[B]
	[12] -1	0	0xd0280000 - 0xd02fffff (0x80000) MX[B](B)
	[13] -1	0	0xd0300000 - 0xd033ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xd0200000 - 0xd027ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xD0200000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): found backlight control method /sys/class/backlight/acpi_video0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Output TV has no monitor section
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output TV disconnected
(II) intel(0): Output LVDS using initial mode 1440x900
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x10000000 to 0x000c0000
(WW) intel(0): Register 0x68010 (TV_CSC_Y) changed from 0x00000000 to 0x0332012d
(WW) intel(0): Register 0x68014 (TV_CSC_Y2) changed from 0x00000000 to 0x07d30104
(WW) intel(0): Register 0x68018 (TV_CSC_U) changed from 0x00000000 to 0x0733052d
(WW) intel(0): Register 0x6801c (TV_CSC_U2) changed from 0x00000000 to 0x05c70200
(WW) intel(0): Register 0x68020 (TV_CSC_V) changed from 0x00000000 to 0x0340030c
(WW) intel(0): Register 0x68024 (TV_CSC_V2) changed from 0x00000000 to 0x06d00200
(WW) intel(0): Register 0x68028 (TV_CLR_KNOBS) changed from 0x00000000 to 0x00606000
(WW) intel(0): Register 0x6802c (TV_CLR_LEVEL) changed from 0x00000000 to 0x010b00e1
(WW) intel(0): Register 0x68030 (TV_H_CTL_1) changed from 0x00000000 to 0x00400359
(WW) intel(0): Register 0x68034 (TV_H_CTL_2) changed from 0x00000000 to 0x80480022
(WW) intel(0): Register 0x68038 (TV_H_CTL_3) changed from 0x00000000 to 0x007c0344
(WW) intel(0): Register 0x6803c (TV_V_CTL_1) changed from 0x00000000 to 0x00f01415
(WW) intel(0): Register 0x68040 (TV_V_CTL_2) changed from 0x00000000 to 0x00060607
(WW) intel(0): Register 0x68044 (TV_V_CTL_3) changed from 0x00000000 to 0x80120001
(WW) intel(0): Register 0x68048 (TV_V_CTL_4) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x6804c (TV_V_CTL_5) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68050 (TV_V_CTL_6) changed from 0x00000000 to 0x000900f0
(WW) intel(0): Register 0x68054 (TV_V_CTL_7) changed from 0x00000000 to 0x000a00f0
(WW) intel(0): Register 0x68060 (TV_SC_CTL_1) changed from 0x00000000 to 0xc1710088
(WW) intel(0): Register 0x68064 (TV_SC_CTL_2) changed from 0x00000000 to 0x4e2d1dc8
(WW) intel(0): Register 0x68070 (TV_WIN_POS) changed from 0x00000000 to 0x00360024
(WW) intel(0): Register 0x68074 (TV_WIN_SIZE) changed from 0x00000000 to 0x02640198
(WW) intel(0): Register 0x68080 (TV_FILTER_CTL_1) changed from 0x00000000 to 0x800010bb
(WW) intel(0): Register 0x68084 (TV_FILTER_CTL_2) changed from 0x00000000 to 0x00028283
(WW) intel(0): Register 0x68088 (TV_FILTER_CTL_3) changed from 0x00000000 to 0x00014141
(WW) intel(0): Register 0x68100 (TV_H_LUMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x681ec (TV_H_LUMA_59) changed from 0x00000000 to 0x0000b060
(WW) intel(0): Register 0x68200 (TV_H_CHROMA_0) changed from 0x00000000 to 0xb1403000
(WW) intel(0): Register 0x682ec (TV_H_CHROMA_59) changed from 0x00000000 to 0x0000b060
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0300000 - 0xd033ffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xd0200000 - 0xd027ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd0102000 - 0xd0102fff (0x1000) MX[B]
	[8] -1	0	0xd0103800 - 0xd01038ff (0x100) MX[B]
	[9] -1	0	0xd0101000 - 0xd0101fff (0x1000) MX[B]
	[10] -1	0	0xd0104000 - 0xd0107fff (0x4000) MX[B]
	[11] -1	0	0xd0103000 - 0xd01037ff (0x800) MX[B]
	[12] -1	0	0x88000000 - 0x8800ffff (0x10000) MX[B]
	[13] -1	0	0xd0544000 - 0xd05443ff (0x400) MX[B]
	[14] -1	0	0xd0340000 - 0xd0343fff (0x4000) MX[B]
	[15] -1	0	0xd0280000 - 0xd02fffff (0x80000) MX[B](B)
	[16] -1	0	0xd0300000 - 0xd033ffff (0x40000) MX[B](B)
	[17] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xd0200000 - 0xd027ffff (0x80000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] 0	0	0x00001800 - 0x00001807 (0x8) IS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[26] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[27] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[33] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[34] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[35] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[36] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488960 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1955836 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1472 -> 2048).
(II) intel(0): [drm] Registers = 0xd0200000
(II) intel(0): [drm] ring buffer = 0xc0000000
(II) intel(0): [drm] mapped front buffer at 0xc1000000, handle = 0xc1000000
(II) intel(0): [drm] mapped back buffer at 0xc5000000, handle = 0xc5000000
(II) intel(0): [drm] mapped depth buffer at 0xc6000000, handle = 0xc6000000
(II) intel(0): [drm] mapped classic textures at 0xc7000000, handle = 0xc7000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 35389440 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x06000000 (pgoffset 24576)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x07000000 (pgoffset 28672)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x0061ffff: compressed frame buffer (6144 kB, 0x000000007f820000 physical
)
(II) intel(0): 0x00620000-0x00620fff: compressed ll buffer (4 kB, 0x000000007fe20000 physical
)
(II) intel(0): 0x00621000-0x0062afff: HW cursors (40 kB, 0x000000007fe21000 physical
)
(II) intel(0): 0x0062b000-0x00632fff: logical 3D context (32 kB)
(II) intel(0): 0x00633000-0x00633fff: overlay registers (4 kB, 0x000000007fe33000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (11520 kB) X tiled
(II) intel(0): 0x02000000-0x041bffff: exa offscreen (34560 kB)
(II) intel(0): 0x05000000-0x05ffffff: back buffer (11520 kB) X tiled
(II) intel(0): 0x06000000-0x06ffffff: depth buffer (11520 kB) X tiled
(II) intel(0): 0x07000000-0x08ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc enabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0):   Output TV is connected to pipe none
(II) intel(0): [drm] dma control initialized, using IRQ 17
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 367 x 230
Atom 4, CARD32 4, unsigned long 4

(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 901 904 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 901 904 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 901 904 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 901 904 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 901 904 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
SetClientVersion: 0 9
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1440x900"x0.0   96.21  1440 1504 1536 1760  900 901 904 912 -hsync -vsync (54.7 kHz)
(II) intel(0): EDID vendor "LPL", prod id 41217
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc enabled on plane a
(II) intel(0): fbc disabled on plane a
```
From what I can tell, the automatic configuration is correct.

I have been running Mplayer using the option to log (from CLI) in order to capture the errors causing the freeze. However, so far Mplayer has decided to run just fine. I'll keep trying.

---

### Post by mask13 on 2009-11-02
Well, I just tried playing music for the first time also. Mp3 and m4a both do the same thing as the video.

---

### Post by Lavahead on 2009-11-03
After a few days of running gmplayer (mplayer w/ GUI) through the command line, I finally got it to freeze the desktop. Here's the log for when mplayer works fine:

```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1440x900 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
Adding filename Test.mpg && pathname /home/monk/Desktop
get_path('codecs.conf') -> '/home/monk/.mplayer/codecs.conf'
Reading /home/monk/.mplayer/codecs.conf: Can't open '/home/monk/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder
CommandLine: '-v' '/home/monk/Desktop/Test.mpg'
init_freetype
get_path('font/font.desc') -> '/home/monk/.mplayer/font/font.desc'
font: can't open file: /home/monk/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/monk/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/monk/.mplayer/input.conf'
Can't open input config file /home/monk/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
vo: X11 truecolor visual 0x23, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x24, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x25, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x26, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x27, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x28, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x29, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x57, depth 32, R:FF0000 G:FF00 B:FF
get_path('skins') -> '/home/monk/.mplayer/skins'
get_path('Skin') -> '/home/monk/.mplayer/Skin'
SKIN dir 1: '/home/monk/.mplayer/skins'
SKIN dir 1 (obsolete): '/home/monk/.mplayer/Skin'
SKIN dir 2: '/usr/share/mplayer/skins'
SKIN dir 2 (obsolete): '/usr/share/mplayer/Skin'
vo: X11 truecolor visual 0x23, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x24, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x25, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x26, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x27, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x28, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x29, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x57, depth 32, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x23, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x24, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x25, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x26, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x27, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x28, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x29, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x2a, depth 24, R:FF0000 G:FF00 B:FF
vo: X11 truecolor visual 0x57, depth 32, R:FF0000 G:FF00 B:FF
get_path('subfont.ttf') -> '/home/monk/.mplayer/subfont.ttf'
Unicode font: 4861 glyphs.
get_path('Test.mpg.conf') -> '/home/monk/.mplayer/Test.mpg.conf'
get_path('subfont.ttf') -> '/home/monk/.mplayer/subfont.ttf'
Unicode font: 4861 glyphs.

Playing /home/monk/Desktop/Test.mpg.
get_path('sub/') -> '/home/monk/.mplayer/sub/'
[file] File size is 2798096 bytes
STREAM: [file] /home/monk/Desktop/Test.mpg
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: MPEG PS format
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename /home/monk/Desktop/Test.mpg ext: .mpg
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
header block 1 size: 0
AVS: avs_check_file - attempting to open file /home/monk/Desktop/Test.mpg
AVS: File is too big, aborting...
Checking for PVA
Checking for MPEG-TS...
TRIED UP TO POSITION 68536, FOUND 47, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=0 size=553648376
LMLM4 Stream Format not found
system stream synced at 0xB (11)!
==> Found video stream: 0
==> Found audio stream: 0
MPEG-PS file format detected.
Searching for sequence header... OK!
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1150.0 kbps (143.8 kbyte/s)
[V] filefmt:2  fourcc:0x10000001  size:352x288  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/monk/.mplayer/sub/'
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x0101fe).
[xv common] Maximum source image dimensions: 1920x1088
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
dec_audio: Allocating 4096 bytes for input buffer.
dec_audio: Allocating 9216 + 65536 = 74752 bytes for output buffer.
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter volnorm 
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO Config (352x288->376x288,flags=0,'MPlayer',0x32315659)
VO: [xv] 352x288 => 376x288 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 84 for hw scaling
[xv] dx: 0 dy: 0 dw: 376 dh: 288
*** [vo] Allocating mp_image_t, 352x288x12bpp YUV planar, 152064 bytes
[xv] dx: 549 dy: 444 dw: 376 dh: 288
A:   0.3 V:   0.0 A-V:  0.309 ct:  0.000   1/  1 ??% ??% ??,?% 0 0              
*** [vo] Allocating mp_image_t, 352x288x12bpp YUV planar, 152064 bytes
A:   0.3 V:   0.3 A-V:  0.002 ct:  0.000   2/  2 ??% ??% ??,?% 0 0              
get_path('subfont.ttf') -> '/home/monk/.mplayer/subfont.ttf'
Unicode font: 4861 glyphs.
A:   0.5 V:   0.4 A-V:  0.110 ct:  0.004   3/  3 ??% ??% ??,?% 0 0              
*** [vo] Allocating mp_image_t, 352x288x12bpp YUV planar, 152064 bytes
A:   0.5 V:   0.4 A-V:  0.094 ct:  0.008   4/  4 ??% ??% ??,?% 0 0              
A:   0.5 V:   0.5 A-V:  0.073 ct:  0.012   5/  5 ??% ??% ??,?% 0 0              
A:   0.6 V:   0.5 A-V:  0.047 ct:  0.016   6/  6 ??% ??% ??,?% 0 0              
A:   0.6 V:   0.5 A-V:  0.043 ct:  0.020   7/  7 ??% ??% ??,?% 0 0              
A:   0.6 V:   0.6 A-V:  0.036 ct:  0.024   8/  8 ??% ??% ??,?% 0 0              
A:   0.7 V:   0.6 A-V:  0.033 ct:  0.027   9/  9 ??% ??% ??,?% 0 0              
A:   0.7 V:   0.7 A-V:  0.028 ct:  0.030  10/ 10 ??% ??% ??,?% 0 0              
A:   0.7 V:   0.7 A-V:  0.025 ct:  0.032  11/ 11 ??% ??% ??,?% 0 0              
A:   0.8 V:   0.7 A-V:  0.021 ct:  0.034  12/ 12 ??% ??% ??,?% 0 0              
A:   0.8 V:   0.8 A-V:  0.019 ct:  0.036  13/ 13 ??% ??% ??,?% 0 0              
A:   0.8 V:   0.8 A-V:  0.014 ct:  0.038  14/ 14  4% 20%  2.7% 0 0              
A:   0.9 V:   0.9 A-V:  0.012 ct:  0.039  15/ 15  4% 19%  2.6% 0 0              
A:   0.9 V:   0.9 A-V:  0.008 ct:  0.040  16/ 16  4% 18%  2.6% 0 0              
A:   1.0 V:   0.9 A-V:  0.008 ct:  0.040  17/ 17  3% 17%  2.5% 0 0              
A:   1.0 V:   1.0 A-V:  0.003 ct:  0.041  18/ 18  3% 16%  2.4% 0 0              
A:   1.0 V:   1.0 A-V:  0.003 ct:  0.041  19/ 19  3% 15%  2.3% 0 0              
A:   1.1 V:   1.1 A-V:  0.001 ct:  0.041  20/ 20  3% 14%  2.3% 0 0              
A:   1.1 V:   1.1 A-V:  0.023 ct:  0.043  21/ 21  3% 14%  2.2% 0 0              
A:   1.2 V:   1.1 A-V:  0.021 ct:  0.046  22/ 22  3% 13%  2.1% 0 0              
A:   1.2 V:   1.2 A-V:  0.019 ct:  0.047  23/ 23  3% 12%  2.1% 0 0              
A:   1.2 V:   1.2 A-V:  0.014 ct:  0.049  24/ 24  3% 12%  2.0% 0 0              
A:   1.3 V:   1.3 A-V:  0.013 ct:  0.050  25/ 25  3% 11%  2.0% 0 0              
A:   1.3 V:   1.3 A-V:  0.007 ct:  0.051  26/ 26  2% 11%  2.0% 0 0              
A:   1.4 V:   1.3 A-V:  0.008 ct:  0.051  27/ 27  2% 11%  2.0% 0 0              
A:   1.4 V:   1.4 A-V:  0.006 ct:  0.052  28/ 28  2% 10%  1.9% 0 0              
A:   1.4 V:   1.4 A-V:  0.003 ct:  0.052  29/ 29  2% 10%  1.9% 0 0              
A:   1.5 V:   1.5 A-V: -0.000 ct:  0.052  30/ 30  2% 10%  1.9% 0 0              
A:   1.5 V:   1.5 A-V: -0.002 ct:  0.052  31/ 31  2%  9%  1.9% 0 0              
A:   1.5 V:   1.5 A-V:  0.000 ct:  0.052  32/ 32  2%  9%  1.9% 0 0              
A:   1.6 V:   1.6 A-V: -0.001 ct:  0.052  33/ 33  2%  9%  1.9% 0 0              
A:   1.6 V:   1.6 A-V: -0.001 ct:  0.052  34/ 34  2%  8%  1.9% 0 0              
A:   1.7 V:   1.7 A-V: -0.006 ct:  0.051  35/ 35  2%  8%  1.9% 0 0              
A:   1.7 V:   1.7 A-V: -0.007 ct:  0.050  36/ 36  2%  8%  1.9% 0 0              
A:   1.7 V:   1.7 A-V: -0.007 ct:  0.050  37/ 37  2%  8%  1.9% 0 0              
A:   1.8 V:   1.8 A-V: -0.006 ct:  0.049  38/ 38  2%  8%  1.9% 0 0              
A:   1.8 V:   1.8 A-V:  0.018 ct:  0.051  39/ 39  2%  7%  1.9% 0 0              
A:   1.9 V:   1.9 A-V:  0.012 ct:  0.052  40/ 40  2%  7%  1.9% 0 0              
A:   1.9 V:   1.9 A-V:  0.011 ct:  0.053  41/ 41  2%  7%  1.8% 0 0              
A:   2.0 V:   1.9 A-V:  0.007 ct:  0.054  42/ 42  2%  7%  1.8% 0 0              
A:   2.0 V:   2.0 A-V:  0.006 ct:  0.055  43/ 43  2%  7%  1.8% 0 0              
A:   2.0 V:   2.0 A-V:  0.006 ct:  0.055  44/ 44  2%  7%  1.8% 0 0              
A:   2.1 V:   2.1 A-V:  0.002 ct:  0.055  45/ 45  2%  7%  1.8% 0 0              
A:   2.1 V:   2.1 A-V: -0.002 ct:  0.055  46/ 46  2%  6%  1.8% 0 0              
A:   2.1 V:   2.1 A-V: -0.001 ct:  0.055  47/ 47  2%  6%  1.8% 0 0              
A:   2.2 V:   2.2 A-V:  0.001 ct:  0.055  48/ 48  2%  6%  1.8% 0 0              
A:   2.2 V:   2.2 A-V: -0.004 ct:  0.055  49/ 49  2%  6%  1.8% 0 0              
A:   2.3 V:   2.3 A-V: -0.004 ct:  0.054  50/ 50  2%  6%  1.8% 0 0              
A:   2.3 V:   2.3 A-V: -0.008 ct:  0.054  51/ 51  2%  6%  1.8% 0 0              
A:   2.3 V:   2.3 A-V: -0.005 ct:  0.053  52/ 52  2%  6%  1.8% 0 0              
A:   2.4 V:   2.4 A-V: -0.008 ct:  0.052  53/ 53  2%  6%  1.8% 0 0              
A:   2.4 V:   2.4 A-V: -0.007 ct:  0.051  54/ 54  2%  6%  1.8% 0 0              
A:   2.5 V:   2.5 A-V: -0.009 ct:  0.051  55/ 55  2%  5%  1.8% 0 0              
A:   2.5 V:   2.5 A-V:  0.016 ct:  0.052  56/ 56  2%  5%  1.9% 0 0              
A:   2.6 V:   2.5 A-V:  0.013 ct:  0.053  57/ 57  2%  5%  1.8% 0 0              
A:   2.6 V:   2.6 A-V:  0.012 ct:  0.055  58/ 58  2%  5%  1.8% 0 0              
A:   2.6 V:   2.6 A-V:  0.008 ct:  0.055  59/ 59  2%  5%  1.8% 0 0              
A:   2.7 V:   2.7 A-V:  0.007 ct:  0.056  60/ 60  2%  5%  1.8% 0 0              
A:   2.7 V:   2.7 A-V:  0.003 ct:  0.056  61/ 61  2%  5%  1.8% 0 0              
A:   2.7 V:   2.7 A-V:  0.003 ct:  0.057  62/ 62  2%  5%  1.8% 0 0              
A:   2.8 V:   2.8 A-V: -0.001 ct:  0.056  63/ 63  2%  5%  1.8% 0 0              
A:   2.8 V:   2.8 A-V: -0.000 ct:  0.056  64/ 64  2%  5%  1.8% 0 0              
A:   2.9 V:   2.9 A-V: -0.003 ct:  0.056  65/ 65  2%  5%  1.8% 0 0              
A:   2.9 V:   2.9 A-V: -0.004 ct:  0.056  66/ 66  2%  5%  1.8% 0 0              
A:   2.9 V:   2.9 A-V: -0.003 ct:  0.055  67/ 67  2%  5%  1.8% 0 0              
A:   3.0 V:   3.0 A-V: -0.005 ct:  0.055  68/ 68  2%  5%  1.9% 0 0              
A:   3.0 V:   3.0 A-V: -0.007 ct:  0.054  69/ 69  2%  4%  1.9% 0 0              
A:   3.1 V:   3.1 A-V: -0.007 ct:  0.053  70/ 70  2%  4%  1.8% 0 0              
A:   3.1 V:   3.1 A-V: -0.006 ct:  0.053  71/ 71  2%  4%  1.8% 0 0              
A:   3.1 V:   3.1 A-V: -0.009 ct:  0.052  72/ 72  2%  4%  1.9% 0 0              
A:   3.2 V:   3.2 A-V: -0.011 ct:  0.051  73/ 73  2%  4%  1.9% 0 0              
A:   3.2 V:   3.2 A-V: -0.010 ct:  0.050  74/ 74  2%  4%  1.9% 0 0              
A:   3.3 V:   3.3 A-V:  0.014 ct:  0.051  75/ 75  2%  4%  1.9% 0 0              
A:   3.3 V:   3.3 A-V:  0.012 ct:  0.052  76/ 76  2%  4%  1.9% 0 0              
A:   3.4 V:   3.3 A-V:  0.009 ct:  0.053  77/ 77  2%  4%  1.9% 0 0              
A:   3.4 V:   3.4 A-V:  0.008 ct:  0.054  78/ 78  2%  4%  1.9% 0 0              
A:   3.4 V:   3.4 A-V:  0.004 ct:  0.054  79/ 79  2%  4%  1.9% 0 0              
A:   3.5 V:   3.5 A-V:  0.004 ct:  0.055  80/ 80  2%  4%  1.9% 0 0              
A:   3.5 V:   3.5 A-V:  0.002 ct:  0.055  81/ 81  2%  4%  1.9% 0 0              
A:   3.5 V:   3.5 A-V: -0.000 ct:  0.055  82/ 82  2%  4%  1.9% 0 0              
A:   3.6 V:   3.6 A-V:  0.000 ct:  0.055  83/ 83  2%  4%  1.8% 0 0              
A:   3.6 V:   3.6 A-V: -0.006 ct:  0.054  84/ 84  2%  4%  1.9% 0 0              
A:   3.7 V:   3.7 A-V: -0.005 ct:  0.054  85/ 85  2%  4%  1.9% 0 0              
A:   3.7 V:   3.7 A-V: -0.003 ct:  0.054  86/ 86  2%  4%  1.9% 0 0              
A:   3.7 V:   3.7 A-V: -0.005 ct:  0.053  87/ 87  2%  4%  1.9% 0 0              
A:   3.8 V:   3.8 A-V: -0.007 ct:  0.052  88/ 88  2%  4%  1.9% 0 0              
A:   3.8 V:   3.8 A-V: -0.012 ct:  0.051  89/ 89  2%  4%  1.9% 0 0              
A:   3.9 V:   3.9 A-V: -0.008 ct:  0.050  90/ 90  2%  4%  1.9% 0 0              
A:   3.9 V:   3.9 A-V:  0.018 ct:  0.052  91/ 91  2%  4%  1.9% 0 0              
A:   4.0 V:   3.9 A-V:  0.011 ct:  0.053  92/ 92  2%  3%  1.9% 0 0              
A:   4.1 V:   4.0 A-V:  0.132 ct:  0.054  93/ 93  2%  3%  2.0% 1 0              
A:   4.1 V:   4.0 A-V:  0.095 ct:  0.054  94/ 94  2%  3%  2.0% 1 0              
A:   4.1 V:   4.1 A-V:  0.056 ct:  0.054  95/ 95  2%  3%  1.9% 1 0              
A:   4.1 V:   4.1 A-V:  0.018 ct:  0.054  96/ 96  2%  3%  1.9% 1 0              
A:   4.1 V:   4.1 A-V:  0.002 ct:  0.055  97/ 97  2%  3%  1.9% 1 0              
A:   4.2 V:   4.2 A-V:  0.002 ct:  0.055  98/ 98  2%  3%  1.9% 1 0              
A:   4.2 V:   4.2 A-V:  0.000 ct:  0.055  99/ 99  2%  3%  1.9% 1 0              
A:   4.3 V:   4.3 A-V: -0.001 ct:  0.055 100/100  2%  3%  1.9% 1 0              
A:   4.3 V:   4.3 A-V:  0.001 ct:  0.055 101/101  2%  3%  1.9% 1 0              
A:   4.3 V:   4.3 A-V: -0.004 ct:  0.054 102/102  2%  3%  1.9% 1 0              
A:   4.4 V:   4.4 A-V: -0.004 ct:  0.054 103/103  2%  3%  1.9% 1 0              
A:   4.4 V:   4.4 A-V: -0.008 ct:  0.053 104/104  2%  3%  1.9% 1 0              
A:   4.5 V:   4.5 A-V: -0.006 ct:  0.053 105/105  2%  3%  1.9% 1 0              
A:   4.5 V:   4.5 A-V: -0.007 ct:  0.052 106/106  2%  3%  1.9% 1 0              
A:   4.5 V:   4.5 A-V: -0.007 ct:  0.051 107/107  2%  3%  1.9% 1 0              
A:   4.6 V:   4.6 A-V: -0.010 ct:  0.050 108/108  2%  3%  1.9% 1 0              
A:   4.6 V:   4.6 A-V: -0.009 ct:  0.049 109/109  2%  3%  1.9% 1 0              
A:   4.7 V:   4.7 A-V:  0.015 ct:  0.051 110/110  2%  3%  1.9% 1 0              
A:   4.7 V:   4.7 A-V:  0.014 ct:  0.052 111/111  2%  3%  1.9% 1 0              
A:   4.8 V:   4.7 A-V:  0.009 ct:  0.053 112/112  2%  3%  1.9% 1 0              
A:   4.8 V:   4.8 A-V:  0.008 ct:  0.054 113/113  2%  3%  1.9% 1 0              
A:   4.8 V:   4.8 A-V:  0.005 ct:  0.055 114/114  2%  3%  1.9% 1 0              
A:   4.9 V:   4.9 A-V:  0.004 ct:  0.055 115/115  2%  3%  1.9% 1 0              
A:   4.9 V:   4.9 A-V:  0.001 ct:  0.055 116/116  2%  3%  1.9% 1 0              
A:   4.9 V:   4.9 A-V: -0.000 ct:  0.055 117/117  2%  3%  1.9% 1 0              
A:   5.0 V:   5.0 A-V: -0.002 ct:  0.055 118/118  2%  3%  1.9% 1 0              
A:   5.0 V:   5.0 A-V: -0.002 ct:  0.055 119/119  2%  3%  1.9% 1 0              
A:   5.1 V:   5.1 A-V: -0.005 ct:  0.054 120/120  2%  3%  1.9% 1 0              
A:   5.1 V:   5.1 A-V: -0.005 ct:  0.054 121/121  2%  3%  1.9% 1 0              
A:   5.1 V:   5.1 A-V: -0.007 ct:  0.053 122/122  2%  3%  1.9% 1 0              
A:   5.2 V:   5.2 A-V: -0.006 ct:  0.052 123/123  2%  3%  1.9% 1 0              
A:   5.2 V:   5.2 A-V: -0.008 ct:  0.052 124/124  2%  3%  1.9% 1 0              
A:   5.3 V:   5.3 A-V: -0.008 ct:  0.051 125/125  2%  3%  1.9% 1 0              
A:   5.3 V:   5.3 A-V: -0.010 ct:  0.050 126/126  2%  3%  1.9% 1 0              
A:   5.3 V:   5.3 A-V: -0.010 ct:  0.049 127/127  2%  3%  1.9% 1 0              
A:   5.4 V:   5.4 A-V:  0.015 ct:  0.050 128/128  2%  3%  1.9% 1 0              
A:   5.4 V:   5.4 A-V:  0.012 ct:  0.051 129/129  2%  3%  1.9% 1 0              
A:   5.5 V:   5.5 A-V:  0.009 ct:  0.052 130/130  2%  3%  1.9% 1 0              
A:   5.5 V:   5.5 A-V:  0.008 ct:  0.053 131/131  2%  3%  1.9% 1 0              
A:   5.5 V:   5.5 A-V:  0.003 ct:  0.053 132/132  2%  3%  1.9% 1 0              
A:   5.6 V:   5.6 A-V:  0.004 ct:  0.054 133/133  2%  3%  1.9% 1 0              
A:   5.6 V:   5.6 A-V:  0.001 ct:  0.054 134/134  2%  3%  1.9% 1 0              
A:   5.7 V:   5.7 A-V:  0.001 ct:  0.054 135/135  2%  3%  1.9% 1 0              
A:   5.7 V:   5.7 A-V: -0.002 ct:  0.054 136/136  2%  3%  1.9% 1 0              
A:   5.7 V:   5.7 A-V: -0.001 ct:  0.054 137/137  2%  3%  1.9% 1 0              
A:   5.8 V:   5.8 A-V: -0.002 ct:  0.053 138/138  2%  2%  1.9% 1 0              
A:   5.8 V:   5.8 A-V: -0.004 ct:  0.053 139/139  2%  2%  1.9% 1 0              
A:   5.9 V:   5.9 A-V: -0.004 ct:  0.053 140/140  2%  2%  1.9% 1 0              
A:   5.9 V:   5.9 A-V: -0.007 ct:  0.052 141/141  2%  2%  1.9% 1 0              
A:   5.9 V:   5.9 A-V: -0.010 ct:  0.051 142/142  2%  2%  1.9% 1 0              
A:   6.0 V:   6.0 A-V: -0.008 ct:  0.050 143/143  2%  2%  1.9% 1 0              
A:   6.0 V:   6.0 A-V:  0.016 ct:  0.052 144/144  2%  2%  1.9% 1 0              
A:   6.1 V:   6.1 A-V:  0.014 ct:  0.053 145/145  2%  2%  1.9% 1 0              
A:   6.1 V:   6.1 A-V:  0.010 ct:  0.054 146/146  2%  2%  1.9% 1 0              
A:   6.2 V:   6.1 A-V:  0.007 ct:  0.055 147/147  2%  2%  1.9% 1 0              
A:   6.2 V:   6.2 A-V:  0.008 ct:  0.055 148/148  2%  2%  1.9% 1 0              
A:   6.2 V:   6.2 A-V:  0.005 ct:  0.056 149/149  2%  2%  1.9% 1 0              
A:   6.3 V:   6.3 A-V:  0.001 ct:  0.056 150/150  2%  2%  1.9% 1 0              
A:   6.3 V:   6.3 A-V:  0.001 ct:  0.056 151/151  2%  2%  1.9% 1 0              
A:   6.3 V:   6.3 A-V: -0.003 ct:  0.056 152/152  2%  2%  1.9% 1 0              
A:   6.4 V:   6.4 A-V: -0.002 ct:  0.056 153/153  2%  2%  1.9% 1 0              
A:   6.4 V:   6.4 A-V: -0.002 ct:  0.055 154/154  2%  2%  1.9% 1 0              
A:   6.5 V:   6.5 A-V: -0.005 ct:  0.055 155/155  2%  2%  1.9% 1 0              
A:   6.5 V:   6.5 A-V: -0.004 ct:  0.054 156/156  2%  2%  1.9% 1 0              
A:   6.5 V:   6.5 A-V: -0.007 ct:  0.054 157/157  2%  2%  1.9% 1 0              
A:   6.6 V:   6.6 A-V: -0.009 ct:  0.053 158/158  2%  2%  1.9% 1 0              
A:   6.6 V:   6.6 A-V: -0.008 ct:  0.052 159/159  2%  2%  1.9% 1 0              
A:   6.7 V:   6.7 A-V: -0.008 ct:  0.051 160/160  2%  2%  1.9% 1 0              
A:   6.7 V:   6.7 A-V: -0.010 ct:  0.050 161/161  2%  2%  1.9% 1 0              
A:   6.7 V:   6.7 A-V: -0.011 ct:  0.049 162/162  2%  2%  1.9% 1 0              
A:   6.8 V:   6.8 A-V:  0.015 ct:  0.051 163/163  2%  2%  1.9% 1 0              
A:   6.8 V:   6.8 A-V:  0.016 ct:  0.052 164/164  2%  2%  1.9% 1 0              
A:   6.9 V:   6.9 A-V:  0.009 ct:  0.053 165/165  2%  2%  1.9% 1 0              
A:   6.9 V:   6.9 A-V:  0.008 ct:  0.054 166/166  2%  2%  1.9% 1 0              
A:   6.9 V:   6.9 A-V:  0.003 ct:  0.054 167/167  2%  2%  1.9% 1 0              
A:   7.0 V:   7.0 A-V:  0.004 ct:  0.055 168/168  2%  2%  1.9% 1 0              
A:   7.0 V:   7.0 A-V:  0.003 ct:  0.055 169/169  2%  2%  1.9% 1 0              
A:   7.1 V:   7.1 A-V: -0.003 ct:  0.055 170/170  2%  2%  1.9% 1 0              
A:   7.1 V:   7.1 A-V: -0.002 ct:  0.055 171/171  2%  2%  1.9% 1 0              
A:   7.1 V:   7.1 A-V: -0.003 ct:  0.054 172/172  2%  2%  1.9% 1 0              
A:   7.2 V:   7.2 A-V: -0.005 ct:  0.054 173/173  2%  2%  1.9% 1 0              
A:   7.2 V:   7.2 A-V: -0.003 ct:  0.053 174/174  2%  2%  1.9% 1 0              
A:   7.3 V:   7.3 A-V: -0.007 ct:  0.053 175/175  2%  2%  1.9% 1 0              
A:   7.3 V:   7.3 A-V: -0.006 ct:  0.052 176/176  2%  2%  1.9% 1 0              
A:   7.3 V:   7.3 A-V: -0.010 ct:  0.051 177/177  2%  2%  1.9% 1 0              
A:   7.4 V:   7.4 A-V: -0.008 ct:  0.050 178/178  2%  2%  1.9% 1 0              
A:   7.4 V:   7.4 A-V:  0.016 ct:  0.052 179/179  2%  2%  1.9% 1 0              
A:   7.5 V:   7.5 A-V:  0.015 ct:  0.053 180/180  2%  2%  1.9% 1 0              
A:   7.5 V:   7.5 A-V:  0.010 ct:  0.054 181/181  2%  2%  1.9% 1 0              
A:   7.6 V:   7.5 A-V:  0.008 ct:  0.055 182/182  2%  2%  1.9% 1 0              
A:   7.6 V:   7.6 A-V:  0.005 ct:  0.056 183/183  2%  2%  1.9% 1 0              
A:   7.6 V:   7.6 A-V:  0.005 ct:  0.056 184/184  2%  2%  1.9% 1 0              
A:   7.7 V:   7.7 A-V:  0.002 ct:  0.056 185/185  2%  2%  1.9% 1 0              
A:   7.7 V:   7.7 A-V:  0.001 ct:  0.056 186/186  2%  2%  1.9% 1 0              
A:   7.7 V:   7.7 A-V: -0.002 ct:  0.056 187/187  2%  2%  1.9% 1 0              
A:   7.8 V:   7.8 A-V: -0.002 ct:  0.056 188/188  2%  2%  1.9% 1 0              
A:   7.8 V:   7.8 A-V: -0.005 ct:  0.056 189/189  2%  2%  1.9% 1 0              
A:   7.9 V:   7.9 A-V: -0.004 ct:  0.055 190/190  2%  2%  1.9% 1 0              
A:   7.9 V:   7.9 A-V: -0.004 ct:  0.055 191/191  2%  2%  1.9% 1 0              
A:   7.9 V:   7.9 A-V: -0.007 ct:  0.054 192/192  2%  2%  1.9% 1 0              
A:   8.0 V:   8.0 A-V: -0.009 ct:  0.053 193/193  2%  2%  1.9% 1 0              
A:   8.0 V:   8.0 A-V: -0.008 ct:  0.052 194/194  2%  2%  1.9% 1 0              
A:   8.1 V:   8.1 A-V: -0.010 ct:  0.051 195/195  2%  2%  1.9% 1 0              
A:   8.1 V:   8.1 A-V: -0.009 ct:  0.050 196/196  2%  2%  1.9% 1 0              
A:   8.2 V:   8.1 A-V:  0.015 ct:  0.052 197/197  2%  2%  1.9% 1 0              
A:   8.2 V:   8.2 A-V:  0.013 ct:  0.053 198/198  2%  2%  1.9% 1 0              
A:   8.2 V:   8.2 A-V:  0.009 ct:  0.054 199/199  2%  2%  1.9% 1 0              
A:   8.3 V:   8.3 A-V:  0.008 ct:  0.055 200/200  2%  2%  1.9% 1 0              
A:   8.3 V:   8.3 A-V:  0.004 ct:  0.055 201/201  2%  2%  1.9% 1 0              
A:   8.3 V:   8.3 A-V:  0.002 ct:  0.056 202/202  2%  2%  1.9% 1 0              
A:   8.4 V:   8.4 A-V:  0.001 ct:  0.056 203/203  2%  2%  1.9% 1 0              
A:   8.4 V:   8.4 A-V:  0.001 ct:  0.056 204/204  2%  2%  1.9% 1 0              
A:   8.5 V:   8.5 A-V: -0.001 ct:  0.056 205/205  2%  2%  1.9% 1 0              
A:   8.5 V:   8.5 A-V: -0.002 ct:  0.055 206/206  2%  2%  1.9% 1 0              
A:   8.5 V:   8.5 A-V: -0.002 ct:  0.055 207/207  2%  2%  1.9% 1 0              
A:   8.6 V:   8.6 A-V: -0.005 ct:  0.055 208/208  2%  2%  1.9% 1 0              
A:   8.6 V:   8.6 A-V: -0.004 ct:  0.054 209/209  2%  2%  1.9% 1 0              
A:   8.7 V:   8.7 A-V: -0.007 ct:  0.054 210/210  2%  2%  1.9% 1 0              
A:   8.7 V:   8.7 A-V: -0.006 ct:  0.053 211/211  2%  2%  1.9% 1 0              
A:   8.7 V:   8.7 A-V: -0.008 ct:  0.052 212/212  2%  2%  1.9% 1 0              
A:   8.8 V:   8.8 A-V: -0.011 ct:  0.051 213/213  2%  2%  1.9% 1 0              
A:   8.8 V:   8.8 A-V: -0.010 ct:  0.050 214/214  2%  2%  1.9% 1 0              
A:   8.9 V:   8.9 A-V: -0.010 ct:  0.049 215/215  2%  2%  1.9% 1 0              
A:   8.9 V:   8.9 A-V:  0.015 ct:  0.050 216/216  2%  2%  1.9% 1 0              
A:   9.0 V:   8.9 A-V:  0.011 ct:  0.052 217/217  2%  2%  1.9% 1 0              
A:   9.0 V:   9.0 A-V:  0.009 ct:  0.053 218/218  2%  2%  1.9% 1 0              
A:   9.0 V:   9.0 A-V:  0.006 ct:  0.053 219/219  2%  2%  1.9% 1 0              
A:   9.1 V:   9.1 A-V:  0.005 ct:  0.054 220/220  2%  2%  1.8% 1 0              
A:   9.1 V:   9.1 A-V:  0.001 ct:  0.054 221/221  2%  2%  1.8% 1 0              
A:   9.1 V:   9.1 A-V:  0.003 ct:  0.054 222/222  2%  2%  1.8% 1 0              
A:   9.2 V:   9.2 A-V: -0.002 ct:  0.054 223/223  2%  2%  1.8% 1 0              
A:   9.2 V:   9.2 A-V: -0.002 ct:  0.054 224/224  2%  2%  1.8% 1 0              
A:   9.3 V:   9.3 A-V: -0.002 ct:  0.054 225/225  2%  2%  1.8% 1 0              
A:   9.3 V:   9.3 A-V: -0.004 ct:  0.053 226/226  2%  2%  1.8% 1 0              
A:   9.3 V:   9.3 A-V: -0.006 ct:  0.053 227/227  2%  2%  1.8% 1 0              
A:   9.4 V:   9.4 A-V: -0.006 ct:  0.052 228/228  2%  2%  1.8% 1 0              
A:   9.4 V:   9.4 A-V: -0.006 ct:  0.051 229/229  2%  2%  1.8% 1 0              
A:   9.5 V:   9.5 A-V: -0.005 ct:  0.051 230/230  2%  2%  1.8% 1 0              
A:   9.5 V:   9.5 A-V:  0.016 ct:  0.052 231/231  2%  2%  1.8% 1 0              
A:   9.6 V:   9.5 A-V:  0.014 ct:  0.054 232/232  2%  2%  1.8% 1 0              
A:   9.6 V:   9.6 A-V:  0.012 ct:  0.055 233/233  2%  2%  1.8% 1 0              
A:   9.6 V:   9.6 A-V:  0.008 ct:  0.056 234/234  2%  2%  1.8% 1 0              
A:   9.7 V:   9.7 A-V:  0.007 ct:  0.056 235/235  2%  2%  1.8% 1 0              
A:   9.7 V:   9.7 A-V:  0.004 ct:  0.057 236/236  2%  2%  1.8% 1 0              
A:   9.7 V:   9.7 A-V:  0.003 ct:  0.057 237/237  2%  2%  1.8% 1 0              
A:   9.8 V:   9.8 A-V: -0.002 ct:  0.057 238/238  2%  2%  1.8% 1 0              
A:   9.8 V:   9.8 A-V:  0.000 ct:  0.057 239/239  2%  2%  1.8% 1 0              
A:   9.9 V:   9.9 A-V: -0.002 ct:  0.057 240/240  2%  2%  1.8% 1 0              
A:   9.9 V:   9.9 A-V: -0.003 ct:  0.056 241/241  2%  2%  1.8% 1 0              
A:   9.9 V:   9.9 A-V: -0.005 ct:  0.056 242/242  2%  2%  1.8% 1 0              
A:  10.0 V:  10.0 A-V: -0.005 ct:  0.055 243/243  2%  2%  1.8% 1 0              
A:  10.0 V:  10.0 A-V: -0.004 ct:  0.055 244/244  2%  2%  1.8% 1 0              
A:  10.1 V:  10.1 A-V: -0.007 ct:  0.054 245/245  2%  2%  1.8% 1 0              
A:  10.1 V:  10.1 A-V: -0.006 ct:  0.054 246/246  2%  2%  1.8% 1 0              
A:  10.1 V:  10.1 A-V: -0.009 ct:  0.053 247/247  2%  2%  1.8% 1 0              
A:  10.2 V:  10.2 A-V: -0.012 ct:  0.052 248/248  2%  2%  1.8% 1 0              
A:  10.2 V:  10.2 A-V: -0.010 ct:  0.051 249/249  2%  2%  1.8% 1 0              
A:  10.3 V:  10.3 A-V:  0.015 ct:  0.052 250/250  2%  2%  1.8% 1 0              
A:  10.3 V:  10.3 A-V:  0.013 ct:  0.053 251/251  2%  2%  1.8% 1 0              
A:  10.4 V:  10.3 A-V:  0.009 ct:  0.054 252/252  2%  2%  1.8% 1 0              
A:  10.4 V:  10.4 A-V:  0.008 ct:  0.055 253/253  2%  2%  1.8% 1 0              
A:  10.4 V:  10.4 A-V:  0.004 ct:  0.055 254/254  2%  2%  1.8% 1 0              
A:  10.5 V:  10.5 A-V:  0.004 ct:  0.056 255/255  2%  2%  1.8% 1 0              
A:  10.5 V:  10.5 A-V:  0.000 ct:  0.056 256/256  2%  2%  1.8% 1 0              
A:  10.5 V:  10.5 A-V:  0.000 ct:  0.056 257/257  2%  2%  1.8% 1 0              
A:  10.6 V:  10.6 A-V: -0.004 ct:  0.055 258/258  2%  2%  1.8% 1 0              
A:  10.6 V:  10.6 A-V: -0.002 ct:  0.055 259/259  2%  2%  1.8% 1 0              
A:  10.7 V:  10.7 A-V: -0.005 ct:  0.055 260/260  2%  2%  1.8% 1 0              
A:  10.7 V:  10.7 A-V: -0.005 ct:  0.054 261/261  2%  2%  1.8% 1 0              
A:  10.7 V:  10.7 A-V: -0.004 ct:  0.054 262/262  2%  2%  1.8% 1 0              
A:  10.8 V:  10.8 A-V: -0.007 ct:  0.053 263/263  2%  2%  1.8% 1 0              
A:  10.8 V:  10.8 A-V: -0.006 ct:  0.053 264/264  2%  2%  1.8% 1 0              
A:  10.9 V:  10.9 A-V: -0.011 ct:  0.051 265/265  2%  2%  1.8% 1 0              
A:  10.9 V:  10.9 A-V: -0.008 ct:  0.051 266/266  2%  2%  1.8% 1 0              
A:  10.9 V:  10.9 A-V: -0.008 ct:  0.050 267/267  2%  2%  1.8% 1 0              
A:  11.0 V:  11.0 A-V:  0.014 ct:  0.051 268/268  2%  2%  1.8% 1 0              
A:  11.0 V:  11.0 A-V:  0.013 ct:  0.053 269/269  2%  2%  1.8% 1 0              
A:  11.1 V:  11.1 A-V:  0.007 ct:  0.053 270/270  2%  2%  1.8% 1 0              
A:  11.1 V:  11.1 A-V:  0.008 ct:  0.054 271/271  2%  2%  1.8% 1 0              
A:  11.2 V:  11.1 A-V:  0.007 ct:  0.055 272/272  2%  2%  1.8% 1 0              
A:  11.2 V:  11.2 A-V:  0.003 ct:  0.055 273/273  2%  2%  1.8% 1 0              
A:  11.2 V:  11.2 A-V:  0.003 ct:  0.055 274/274  2%  2%  1.8% 1 0              
A:  11.3 V:  11.3 A-V: -0.000 ct:  0.055 275/275  2%  2%  1.8% 1 0              
A:  11.3 V:  11.3 A-V: -0.003 ct:  0.055 276/276  2%  2%  1.8% 1 0              
A:  11.3 V:  11.3 A-V: -0.003 ct:  0.055 277/277  2%  2%  1.8% 1 0              
A:  11.4 V:  11.4 A-V: -0.003 ct:  0.054 278/278  2%  2%  1.8% 1 0              
A:  11.4 V:  11.4 A-V: -0.006 ct:  0.054 279/279  2%  2%  1.8% 1 0              
A:  11.5 V:  11.5 A-V: -0.005 ct:  0.053 280/280  2%  2%  1.8% 1 0              
A:  11.5 V:  11.5 A-V: -0.007 ct:  0.052 281/281  2%  2%  1.8% 1 0              
A:  11.5 V:  11.5 A-V: -0.007 ct:  0.052 282/282  2%  2%  1.8% 1 0              
A:  11.6 V:  11.6 A-V: -0.009 ct:  0.051 283/283  2%  2%  1.8% 1 0              
A:  11.6 V:  11.6 A-V:  0.015 ct:  0.052 284/284  2%  2%  1.8% 1 0              
A:  11.7 V:  11.7 A-V:  0.015 ct:  0.054 285/285  2%  2%  1.8% 1 0              
A:  11.7 V:  11.7 A-V:  0.012 ct:  0.055 286/286  2%  2%  1.8% 1 0              
A:  11.8 V:  11.7 A-V:  0.008 ct:  0.056 287/287  2%  2%  1.8% 1 0              
A:  11.8 V:  11.8 A-V:  0.006 ct:  0.056 288/288  2%  2%  1.8% 1 0              
A:  11.8 V:  11.8 A-V:  0.003 ct:  0.057 289/289  2%  2%  1.8% 1 0              
A:  11.9 V:  11.9 A-V:  0.001 ct:  0.057 290/290  2%  2%  1.8% 1 0              
A:  11.9 V:  11.9 A-V: -0.000 ct:  0.057 291/291  2%  2%  1.8% 1 0              
A:  11.9 V:  11.9 A-V: -0.000 ct:  0.057 292/292  2%  2%  1.8% 1 0              
A:  12.0 V:  12.0 A-V: -0.001 ct:  0.057 293/293  2%  1%  1.8% 1 0              
A:  12.0 V:  12.0 A-V: -0.003 ct:  0.056 294/294  2%  1%  1.8% 1 0              
A:  12.1 V:  12.1 A-V: -0.008 ct:  0.056 295/295  2%  1%  1.8% 1 0              
A:  12.1 V:  12.1 A-V: -0.005 ct:  0.055 296/296  2%  1%  1.8% 1 0              
A:  12.1 V:  12.1 A-V: -0.007 ct:  0.054 297/297  2%  1%  1.8% 1 0              
A:  12.2 V:  12.2 A-V: -0.006 ct:  0.054 298/298  2%  1%  1.8% 1 0              
A:  12.2 V:  12.2 A-V: -0.006 ct:  0.053 299/299  2%  1%  1.8% 1 0              
A:  12.3 V:  12.3 A-V: -0.007 ct:  0.052 300/300  2%  1%  1.8% 1 0              
A:  12.3 V:  12.3 A-V: -0.011 ct:  0.051 301/301  2%  1%  1.8% 1 0              
A:  12.3 V:  12.3 A-V: -0.010 ct:  0.050 302/302  2%  1%  1.8% 1 0              
A:  12.4 V:  12.4 A-V:  0.012 ct:  0.052 303/303  2%  1%  1.8% 1 0              
A:  12.4 V:  12.4 A-V:  0.013 ct:  0.053 304/304  2%  1%  1.8% 1 0              
A:  12.5 V:  12.5 A-V:  0.010 ct:  0.054 305/305  2%  1%  1.8% 1 0              
A:  12.5 V:  12.5 A-V:  0.008 ct:  0.055 306/306  2%  1%  1.8% 1 0              
A:  12.5 V:  12.5 A-V:  0.004 ct:  0.055 307/307  2%  1%  1.8% 1 0              
A:  12.6 V:  12.6 A-V:  0.004 ct:  0.055 308/308  2%  1%  1.8% 1 0              
A:  12.6 V:  12.6 A-V:  0.000 ct:  0.055 309/309  2%  1%  1.8% 1 0              
A:  12.7 V:  12.7 A-V:  0.000 ct:  0.056 310/310  2%  1%  1.8% 1 0              
A:  12.7 V:  12.7 A-V: -0.003 ct:  0.055 311/311  2%  1%  1.8% 1 0              
A:  12.7 V:  12.7 A-V: -0.003 ct:  0.055 312/312  2%  1%  1.8% 1 0              
A:  12.8 V:  12.8 A-V: -0.002 ct:  0.055 313/313  2%  1%  1.8% 1 0              
A:  12.8 V:  12.8 A-V: -0.005 ct:  0.054 314/314  2%  1%  1.8% 1 0              
A:  12.9 V:  12.9 A-V: -0.005 ct:  0.054 315/315  2%  1%  1.8% 1 0              
A:  12.9 V:  12.9 A-V: -0.008 ct:  0.053 316/316  2%  1%  1.8% 1 0              
A:  12.9 V:  12.9 A-V: -0.009 ct:  0.052 317/317  2%  1%  1.8% 1 0              
A:  13.0 V:  13.0 A-V: -0.007 ct:  0.051 318/318  2%  1%  1.8% 1 0              
A:  13.0 V:  13.0 A-V: -0.011 ct:  0.050 319/319  2%  1%  1.8% 1 0              
A:  13.1 V:  13.1 A-V: -0.010 ct:  0.049 320/320  2%  1%  1.8% 1 0              
A:  13.1 V:  13.1 A-V:  0.014 ct:  0.051 321/321  2%  1%  1.8% 1 0              
A:  13.2 V:  13.1 A-V:  0.013 ct:  0.052 322/322  2%  1%  1.8% 1 0              
A:  13.2 V:  13.2 A-V:  0.012 ct:  0.053 323/323  2%  1%  1.8% 1 0              
A:  13.2 V:  13.2 A-V:  0.007 ct:  0.054 324/324  2%  1%  1.8% 1 0              
A:  13.3 V:  13.3 A-V:  0.004 ct:  0.054 325/325  2%  1%  1.8% 1 0              
A:  13.3 V:  13.3 A-V:  0.001 ct:  0.054 326/326  2%  1%  1.8% 1 0              
A:  13.3 V:  13.3 A-V:  0.000 ct:  0.054 327/327  2%  1%  1.8% 1 0              
A:  13.4 V:  13.4 A-V:  0.001 ct:  0.054 328/328  2%  1%  1.8% 1 0              
A:  13.4 V:  13.4 A-V: -0.003 ct:  0.054 329/329  2%  1%  1.8% 1 0              
A:  13.5 V:  13.5 A-V: -0.003 ct:  0.054 330/330  2%  1%  1.8% 1 0              
A:  13.5 V:  13.5 A-V: -0.003 ct:  0.054 331/331  2%  1%  1.8% 1 0              
A:  13.5 V:  13.5 A-V: -0.005 ct:  0.053 332/332  2%  1%  1.8% 1 0              
A:  13.6 V:  13.6 A-V: -0.002 ct:  0.053 333/333  2%  1%  1.8% 1 0              
A:  13.6 V:  13.6 A-V: -0.007 ct:  0.052 334/334  2%  1%  1.8% 1 0              
A:  13.7 V:  13.7 A-V: -0.007 ct:  0.051 335/335  2%  1%  1.8% 1 0              
A:  13.7 V:  13.7 A-V: -0.012 ct:  0.050 336/336  2%  1%  1.8% 1 0              
A:  13.7 V:  13.7 A-V: -0.008 ct:  0.049 337/337  2%  1%  1.8% 1 0              
A:  13.8 V:  13.8 A-V:  0.017 ct:  0.051 338/338  2%  1%  1.8% 1 0              
A:  13.8 V:  13.8 A-V:  0.014 ct:  0.053 339/339  2%  1%  1.8% 1 0              
A:  13.9 V:  13.9 A-V:  0.010 ct:  0.054 340/340  2%  1%  1.8% 1 0              
A:  13.9 V:  13.9 A-V:  0.011 ct:  0.055 341/341  2%  1%  1.8% 1 0              
A:  13.9 V:  13.9 A-V:  0.005 ct:  0.055 342/342  2%  1%  1.8% 1 0              
A:  14.0 V:  14.0 A-V:  0.001 ct:  0.055 343/343  2%  1%  1.8% 1 0              
A:  14.0 V:  14.0 A-V:  0.001 ct:  0.055 344/344  2%  1%  1.8% 1 0              
A:  14.1 V:  14.1 A-V: -0.002 ct:  0.055 345/345  2%  1%  1.8% 1 0              
A:  14.1 V:  14.1 A-V: -0.002 ct:  0.055 346/346  2%  1%  1.8% 1 0              
A:  14.1 V:  14.1 A-V: -0.002 ct:  0.055 347/347  2%  1%  1.8% 1 0              
A:  14.2 V:  14.2 A-V: -0.004 ct:  0.054 348/348  2%  1%  1.8% 1 0              
A:  14.2 V:  14.2 A-V: -0.004 ct:  0.054 349/349  2%  1%  1.8% 1 0              
A:  14.3 V:  14.3 A-V: -0.007 ct:  0.053 350/350  2%  1%  1.8% 1 0              
A:  14.3 V:  14.3 A-V: -0.006 ct:  0.053 351/351  2%  1%  1.8% 1 0              
A:  14.3 V:  14.3 A-V: -0.008 ct:  0.052 352/352  2%  1%  1.8% 1 0              
A:  14.4 V:  14.4 A-V: -0.008 ct:  0.051 353/353  2%  1%  1.9% 1 0              
A:  14.4 V:  14.4 A-V: -0.010 ct:  0.050 354/354  2%  1%  1.9% 1 0              
A:  14.5 V:  14.5 A-V: -0.009 ct:  0.049 355/355  2%  1%  1.8% 1 0              
A:  14.5 V:  14.5 A-V:  0.015 ct:  0.051 356/356  2%  1%  1.8% 1 0              
A:  14.6 V:  14.5 A-V:  0.011 ct:  0.052 357/357  2%  1%  1.9% 1 0              
A:  14.6 V:  14.6 A-V:  0.010 ct:  0.053 358/358  2%  1%  1.8% 1 0              
A:  14.6 V:  14.6 A-V:  0.009 ct:  0.054 359/359  2%  1%  1.9% 1 0              
A:  14.7 V:  14.7 A-V:  0.005 ct:  0.054 360/360  2%  1%  1.9% 1 0              
A:  14.7 V:  14.7 A-V:  0.004 ct:  0.054 361/361  2%  1%  1.9% 1 0              
A:  14.7 V:  14.7 A-V:  0.001 ct:  0.055 362/362  2%  1%  1.9% 1 0              
A:  14.8 V:  14.8 A-V:  0.001 ct:  0.055 363/363  2%  1%  1.9% 1 0              
A:  14.8 V:  14.8 A-V: -0.002 ct:  0.054 364/364  2%  1%  1.8% 1 0              
A:  14.9 V:  14.9 A-V: -0.002 ct:  0.054 365/365  2%  1%  1.9% 1 0              
A:  14.9 V:  14.9 A-V: -0.002 ct:  0.054 366/366  2%  1%  1.9% 1 0              
A:  14.9 V:  14.9 A-V: -0.005 ct:  0.053 367/367  2%  1%  1.9% 1 0              
A:  15.0 V:  15.0 A-V: -0.007 ct:  0.053 368/368  2%  1%  1.9% 1 0              
A:  15.0 V:  15.0 A-V: -0.008 ct:  0.052 369/369  2%  1%  1.9% 1 0              
A:  15.1 V:  15.1 A-V: -0.009 ct:  0.051 370/370  2%  1%  1.9% 1 0              
A:  15.1 V:  15.1 A-V: -0.005 ct:  0.051 371/371  2%  1%  1.9% 1 0              
A:  15.2 V:  15.1 A-V:  0.016 ct:  0.052 372/372  2%  1%  1.9% 1 0              
A:  15.2 V:  15.2 A-V:  0.014 ct:  0.054 373/373  2%  1%  1.9% 1 0              
A:  15.2 V:  15.2 A-V:  0.008 ct:  0.054 374/374  2%  1%  1.9% 1 0              
A:  15.3 V:  15.3 A-V:  0.009 ct:  0.055 375/375  2%  1%  1.8% 1 0              
A:  15.3 V:  15.3 A-V:  0.007 ct:  0.056 376/376  2%  1%  1.9% 1 0              
A:  15.3 V:  15.3 A-V:  0.004 ct:  0.056 377/377  2%  1%  1.9% 1 0              
A:  15.4 V:  15.4 A-V:  0.001 ct:  0.056 378/378  2%  1%  1.9% 1 0              
A:  15.4 V:  15.4 A-V: -0.001 ct:  0.056 379/379  2%  1%  1.9% 1 0              
A:  15.5 V:  15.5 A-V:  0.001 ct:  0.056 380/380  2%  1%  1.9% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.5 V:  15.5 A-V:  0.003 ct:  0.057 381/381  2%  1%  1.9% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.5 V:  15.5 A-V:  0.003 ct:  0.057 382/382  2%  1%  1.9% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.6 V:  15.6 A-V:  0.003 ct:  0.057 383/383  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.6 V:  15.6 A-V:  0.001 ct:  0.057 384/384  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.7 V:  15.7 A-V:  0.001 ct:  0.057 385/385  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.7 V:  15.7 A-V:  0.002 ct:  0.058 386/386  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.7 V:  15.7 A-V:  0.002 ct:  0.058 387/387  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.8 V:  15.8 A-V:  0.002 ct:  0.058 388/388  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.8 V:  15.8 A-V:  0.001 ct:  0.058 389/389  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.9 V:  15.9 A-V:  0.001 ct:  0.058 390/390  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.9 V:  15.9 A-V:  0.003 ct:  0.058 391/391  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  15.9 V:  15.9 A-V:  0.003 ct:  0.059 392/392  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  16.0 V:  16.0 A-V:  0.003 ct:  0.059 393/393  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  16.0 V:  16.0 A-V: -0.037 ct:  0.055 394/394  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  16.0 V:  16.1 A-V: -0.077 ct:  0.051 395/395  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
A:  16.0 V:  16.1 A-V: -0.117 ct:  0.047 396/396  2%  1%  1.8% 1 0              
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
Cannot sync MAD frame
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
A:  16.0 V:  16.1 A-V: -0.117 ct:  0.043 396/396  2%  1%  1.8% 1 0              
EOF code: 1  

Uninit audio filters...
[libaf] Removing filter volnorm 
Uninit audio: libmad
Uninit video: libmpeg2
Successfully enabled DPMS
[GUI] done.
get_path('gui.conf') -> '/home/monk/.mplayer/gui.conf'
get_path('gui.pl') -> '/home/monk/.mplayer/gui.pl'
get_path('gui.url') -> '/home/monk/.mplayer/gui.url'
get_path('gui.history') -> '/home/monk/.mplayer/gui.history'

Exiting... (Quit)
```

Here is the log when the freeze occurs:

```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/monk/Videos/Test.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1150.0 kbps (143.8 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO: [xv] 352x288 => 376x288 Planar YV12 
A:   0.3 V:   0.0 A-V:  0.309 ct:  0.000   1/  1 ??% ??% ??,?% 0 0              
A:   0.3 V:   0.3 A-V:  0.002 ct:  0.000   2/  2 ??% ??% ??,?% 0 0              
A:   0.5 V:   0.4 A-V:  0.074 ct:  0.004   3/  3 ??% ??% ??,?% 0 0              

```

Like a fool, I neglected to set the -v option prior to capturing the freeze. However, the relevant details are still in the log. There is essentially no difference. For some reason, mplayer begins to play the file and then there's a lockup of the entire desktop except the mouse.

At this point, I am not sure if anything can be done to fix the problem in Hardy. It looks as though the simplest solution would be install the latest version of Ubuntu. I personally had a lot of different problems with later versions, so that's why I have stayed with Hardy.

---

### Post by Lavahead on 2009-11-03
I neglected to mention in the previous post that the log results were not unexpected. Since all video players cause the same freezing problem, then mplayer is not the culprit. The log shows that mplayer initializes, then starts to play the test video. After a few frames, it ceases to function. The problem is external to mplayer.

In my last attempt to isolate the problem, I try to copy the Xsession-errors file after another freeze. Since Xsession-errors is overwritten once a new session starts, I must reboot the computer with the Live CD and try to copy the file on the hard drive.

---

### Post by mask13 on 2009-11-03
GOT IT!! 

[http://ubuntuforums.org/showthread.php?t=872309&highlight=freezes+totem](http://ubuntuforums.org/showthread.php?t=872309&highlight=freezes+totem)

Post #8 has solutions for several players. I've only tried VLC so far because that is my preference, but it works for me now. Audio and video are perfectly fine with no problems.

:popcorn:Time to sit back and watch a movie! :D

Now if anyone can point me in the right direction for connecting this to my TV. Again, it worked with Vista, but the keyboard shortcut doesn't now (go figure, I didn't expect it too). When I go to system->preferences->screen resolution and try detect displays nothing happens, same when I hit clone screens.

---

### Post by Lavahead on 2009-11-03
Thanks, mask13 for finding the solution. I will try the fix myself and monitor the result.

---

