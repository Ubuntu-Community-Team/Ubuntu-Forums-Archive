---
title: "RandR 1.3 won't support multiple video cards - what do multimonitor users do?"
date: 2009-02-03
forum: Multimedia Software
---

### Post by langelgjm on 2009-02-03
As some of you may know, X Server 1.6 will probably be released very soon, and it is due to include RandR 1.3.

For a long time, those of us with multiple monitor (i.e., > 2 monitors) setups have been looking forward to RandR 1.3 because it was supposed to include support for multiple video cards. RandR 1.2 only supports one card per X session.

However, I just found out from the X.org mailing list that RandR 1.3 will **not** include support for multiple video cards - see [[COLOR="Blue"]_this post_[/COLOR]]("http://lists.freedesktop.org/archives/xorg/2009-February/043242.html"). Furthermore, it appears that the current radeon driver in Intrepid Ibex 8.10 breaks support for Xinerama on dual-head cards. If I try to enable Xinerama on a dual-head card with the radeon driver, X simply crashes (but it will work on two separate cards).

This means that in 8.10, there is no way for radeon users to have more than two monitors in a Xinerama style setup. This is a huge step backwards.

Questions:

1) Am I correct about the problem? Or do people have Xinerama working in 8.10 with more than two monitors using the radeon driver?

2) What is the fix for this? Is the problem due to a bug in the radeon driver? Obviously, waiting for RandR to support multiple cards is not an option...

---

### Post by Blue Beard on 2009-02-03
I am using x-server 1.6.0 rc1 in Jaunty Alpha 3 updated to two days ago.  I have an integrated RS690 and a HD3450.

Until the release a couple of days ago I had to install using the vesa driver and then switch over to the radeon driver later. I use xrandr to configure the two monitors I have on the HD3450 card (i.e. RS690 unused).

Currently x-server configures the HD3450 to use radeon.  I get some strange but minor layout issues using two monitors and xrandr but it works.

I will be doing a fresh install with Jaunty Alpha 4 this weekend.  It would be nice to use both video adapters since three screens would be nice.

---

### Post by langelgjm on 2009-02-03
Could you say more about your "strange but minor layout issues using two monitors and xrandr"?

I am using xrandr to handle two monitors attached to a Radeon X800, and the third monitor, attached to a Radeon X300, runs a separate X session.

The problem I have with the xrandr setup is that windows maximize to fill both monitors, and dialog boxes pop up centered between the two monitors.

---

### Post by Blue Beard on 2009-02-05
Jaunty Alpha 4 cleaned up all my problems except 3.  
1. The initial install tries to use 1152x864 on my 1024x768 LCD
2. My second monitor used to use 1280x1024
3. Second card/3rd monitor not configured.

mur@ubuntu2:~$ xrandr --version
Server reports RandR version 1.3
mur@ubuntu2:~$ xrandr --output VGA-0 --mode 1024x768
mur@ubuntu2:~$ xrandr --output DVI-0 --mode 1152x864
mur@ubuntu2:~$ xrandr --output DVI-0 --right-of VGA-0
mur@ubuntu2:~$ xrandr -q
Screen 0: minimum 320 x 200, current 2176 x 864, maximum 2704 x 1050
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1152x864       60.0 +   60.0  
   1360x768       59.8  
   1024x768       60.0*    59.9  
   800x600        60.3  
   640x480        59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1152x864+1024+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1152x864       60.0*+   60.0  
   1360x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3  
   640x480        59.9  

I suspect I will have to manually add this to xorg.conf using BusID = "PCI:0:2:0"

lspci -vvnn for second video card not found in Xorg.0.log 

00:02.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) [1002:7913]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

---

### Post by jbaird on 2009-04-23
Have you been successful with 2 cards / 3 monitors yet?  I am trying to get this to work in 9.04/xrandr 1.3, with no success.  Any help would be appreciated!

---

### Post by CHaoSlayeR on 2009-04-23
There are some big fat bugs since x-server 1.6 got introduced regarding multiple cards. It's not a problem of RandR! People are working on the several issues (which is basically a bug during graphics BIOS initialization of the second, third, ... card).

If you have two or more cards that work with the same BIOS you may have luck (otherwise CrossFire/SLI wouldn't work either) but as soon as you have two or more cards from different vendors (AMD, nVidia, Matrox, Intel, ...) you won't get any othe card to work as the first one.

The bugs I'm talking about are here:
[http://bugzilla.kernel.org/show_bug.cgi?id=12168](http://bugzilla.kernel.org/show_bug.cgi?id=12168)
[http://bugs.freedesktop.org/show_bug.cgi?id=18160](http://bugs.freedesktop.org/show_bug.cgi?id=18160)
[http://bugs.freedesktop.org/show_bug.cgi?id=20816](http://bugs.freedesktop.org/show_bug.cgi?id=20816)
[http://bugs.freedesktop.org/show_bug.cgi?id=20817](http://bugs.freedesktop.org/show_bug.cgi?id=20817)

I hope those problem get fixed soon and that the Ubuntu package maintainers update fast. :)


Greetz,

    C]-[aoZ

P.S.: There is no workaround!

---

### Post by jbaird on 2009-04-23
Yeah, I have two ATI Radeon 9250's.  Unfortuantly, I also have an onboard Intel based card that I am unable to disable via the BIOS (Dell Optiplex GX520).  This sounds like it may be causing the problem.  lspci shows all three.. the 2 ATI's and the onboard Intel.

Josh

---

### Post by CHaoSlayeR on 2009-04-23
If the intel chip does keep your system from come up properly you can try to use the "NoInt10" option on that device in your xorg.conf.

C]-[aoZ

---

### Post by Almighty on 2009-04-24
I've been fighting trying to get 3 monitors up and running. I wish I knew more about this stuff.

---

### Post by hyphenistic on 2009-04-24
I'm trying to drive 4 monitors without any luck.  My motherboard has an Intel Q963 graphics chip with an ADD2 SDVO add-on card to give it dual-head capability.  I've also got two nVidia GeForce FX 5200s.  The best I've been able to do so far is to get the onboard adapter to show up as the primary monitor and the add-on card to show up as a mirror.  The nVidia cards never work and I'm not sure if X even recognizes the add-on card as a separate device.  My xorg.conf only shows 3 screens.  The Intel display only works when I tell it to use the vesa driver.  The nVidia adapters don't work using the nv or nvidia driver.  When I was able to get into X, I had the option to enable the proprietary nVidia drivers which I did but didn't help.  I'd really like to make the switch but nothing can handle multiple displays like XP.  It seems like things were better before 8.10.  Is it thought that these issues will be resolved with 9.04 or do I need to just wait another 6 months and try again?

---

### Post by Almighty on 2009-04-24
I may be wrong but if you use the onboard graphics port, it pretty much negates the fact you have graphics cards. Try using only the graphics card ports and install nvidia drivers.

---

### Post by CHaoSlayeR on 2009-04-24
In the ServerLayout section you can specify the screen setup and within the screens you can just omit the intel device. Additionally you may be forced to use the "SingleCard" "true" option within the ServerLayout section to force X to just ignore any other card than the first specified screen.

That way I've configured the system at work that contains a Radeon X1300Pro, an old nVidia Riva TNT2 and a Radeon 7000/VE to just use the X1300 for correct initialization.

And remember that the X-Server is not the only one that has problems with graphics cards of different vendors but Vista has the exact same Problem (found that out the hard way).

C]-[aoZ

P.S.: The problem exists since Intrepid and also remains in Jaunty until a new X-Server version gets introduced that has appropriate fixes. And as there is still a lot of work to do I suspect it wouldn't get resolved before the next version of Ubuntu.

---

### Post by hyphenistic on 2009-04-24
I'm sure it's possible to get just one of my screens working but I can't justify switching from XP if it means losing the other 3 screens.  Looks like I'll have to shelve Ubuntu for another 6 months and just keep my fingers crossed.

---

### Post by CHaoSlayeR on 2009-04-24
As an alternative you could take Ubuntu Hardy Heron or Debian Lenny. Both of them use a version of the X-server that isn't affected by the problems and bugs mentioned here.

As an alternative you could use the two FX 5200 in parallel if you let one of them initialize first so that way the same BIOS gets valid for both cards which in turn means that both cards can be used.

As each of the FX 5200 should be able to drive two monitors you could still use 4 monitors.

Greetz,

C]-[aoZ

---

### Post by jbaird on 2009-04-24
So you are saying I could run Hardy Heron (8.04), and use both of my ATI cards to drive 3 monitors total?

---

### Post by hyphenistic on 2009-04-24
I may give 8.04 a try just to see if it works.  Will I be able to upgrade from there or will that start breaking things?

To the best of my knowledge, the nVidia cards I have only drive a single display.  Each card has a DVI and an s-video port.  It looks like the DVI may be dual-link but that doesn't mean I can split it to two separate, non-mirrored displays, does it?

---

### Post by jbaird on 2009-04-24
> **jbaird said:**
> So you are saying I could run Hardy Heron (8.04), and use both of my ATI cards to drive 3 monitors total?

No go with 8.04.. not sure why it would work anyways since it uses xrandr 1.2?  I only get one video card to work.. not both.

---

### Post by hyphenistic on 2009-04-24
I installed 8.04 and it looks like I'm close.  I was able to get all 4 monitors to show something.  Once I enabled Xinerama in my xorg.conf I was able to get really close to what I want.  One of my Intel cards was the primary and both nVidia cards were extended.  The only problem now is getting both Intel devices to act independently.  Like I said, I've got an ADD2 card which essentially just adds another DVI port to the onboard chip.  I did some searching and someone else got this type of card to work right by adding in some DevicePresence options.  I've not been able to find the right configuration yet though.  I found that I can add those options in without a problem but when I toss a Screen command into the Device section things stop working.  I have not been able to find good documentation on the DevicePresence option either to know what I'm attempting to do with it.  Any ideas?

---

### Post by CHaoSlayeR on 2009-04-24
> **jbaird said:**
> No go with 8.04.. not sure why it would work anyways since it uses xrandr 1.2?  I only get one video card to work.. not both.

Once again:

This is **NOT** a RandR issue!!! See my previous link to the bugs that are used to track down the problems behind the issues.

As it should work with Hardy (I had all three cards of mine at work running together nicely which are totally different) it may be a configuration issue. Maybe the Radeon 9250 don't play nicely with RandR 1.2 and need some extra config in the xorg.conf? For troubleshooting could you attach your Xorg.0.log?

@hyphenistic:

With Radeon cards using the open-source drivers I had success following this guide for Intel chips, so give it a try on yours:

[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

C]-[aoZ

---

### Post by jbaird on 2009-04-27
> **hyphenistic said:**
> I installed 8.04 and it looks like I'm close.  I was able to get all 4 monitors to show something.  Once I enabled Xinerama in my xorg.conf I was able to get really close to what I want.  One of my Intel cards was the primary and both nVidia cards were extended.  The only problem now is getting both Intel devices to act independently.  Like I said, I've got an ADD2 card which essentially just adds another DVI port to the onboard chip.  I did some searching and someone else got this type of card to work right by adding in some DevicePresence options.  I've not been able to find the right configuration yet though.  I found that I can add those options in without a problem but when I toss a Screen command into the Device section things stop working.  I have not been able to find good documentation on the DevicePresence option either to know what I'm attempting to do with it.  Any ideas?

So, with a clean install of 8.04 and an unmodified xorg.conf, you were able to get all 4 of your monitors displaying SOMETHING?

---

### Post by hyphenistic on 2009-04-27
That's correct.  I have done some more fiddling and have tuned my setup a little more.

@CHaoSlayeR The link you posted allowed me to get my two Intel screens setup but since xrandr doesn't support multiple video cards, I wasn't able to add my nVidia cards to the mix.

I have now narrowed the issue down to getting Pipe B on my Intel chip to work properly.  Using MonitorLayout DFP I was able to break the cloning that was going on and enable just my DFP.  If I changed it to CRT, only the CRT would turn on.  If I changed it to DFP+CRT, both would come on in clone mode.  It makes sense then that DFP,CRT would split them to different displays but I'm not getting that to work.

I have my nVidia cards turned back on and Xinerama working.  So if I could just get Pipe B to make to a monitor and screen then I would be set.

---

### Post by jbaird on 2009-04-27
Could someone take a look at my xorg.conf to see if they see any problems.  I have two ATI Radeon 9250's in this machine, and one Intel onboard card which I am not using.  The result here is that I get two mirrored low res screens, nothing on the third.  This is in 8.04.

```

## Monitors

Section "Monitor"
        Identifier "Lcd0"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "Lcd1"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "Lcd2"
        Option  "DPMS"
EndSection

## Video Cards

Section "Device"
        Identifier      "ati0"
        Driver          "radeon"
        BusID           "PCI:4:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "ati1"
        Driver          "radeon"
        BusID           "PCI:4:2:0"
        Screen          2
EndSection


## Screens

Section "Screen"
        Identifier      "screen0"
        Device          "ati0"
        Monitor         "Lcd0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "ati0"
        Monitor         "Lcd1"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen2"
        Device          "ati1"
        Monitor         "Lcd2"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Multihead"
        Screen  "screen0"
        Screen  "screen1" RightOf "screen0"
        Screen  "screen2" RightOf "screen1"
        InputDevice     "mouse1" "CorePointer"
        InputDevice     "keyboard1" "CoreKeyboard"
        Option "Xinerama"       true
EndSection


```

Thanks,

Josh

---

### Post by jbaird on 2009-04-27
And here is my Xorg.0.log:

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux cnsmonitor 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 27 02:34:49 2009
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
	Using the first mouse device.
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
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1028,01ad rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2772 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2776 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01ad rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01ad rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,27de card 1028,01ad rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,27b8 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1028,01ad rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1028,01ad rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01ad rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,1677 card 1028,01ad rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: 04:02:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe700000 - 0xfe7fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe6fffff (0x200000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xefffffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/19, 0xc0000000/28, 0xfeac0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/19
(--) PCI: (4:0:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xe0000000/28, 0xfe5e0000/16, I/O @ 0xd800/8, BIOS @ 0xfe600000/17
(--) PCI:*(4:2:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xd0000000/28, 0xfe5f0000/16, I/O @ 0xdc00/8, BIOS @ 0xfe600000/17
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
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 04:02:0
(WW) VESA: No matching Device section for instance (BusID PCI:4:0:0) found
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[24] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[36] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[37] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[38] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[40] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[41] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI RADEON 9200
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: V280
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 2 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: DEL  Model: a00b  Serial#: 810899027
(II) VESA(0): Year: 2005  Week: 17
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VESA(0): Sync:  Separate
(II) VESA(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) VESA(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) VESA(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) VESA(0): Serial No: D542854J0UVS
(II) VESA(0): Monitor name: DELL E173FP
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0010ac0ba053565530
(II) VESA(0): 	110f010368221b78eecaf6a357479e23
(II) VESA(0): 	114f54a54b00714f8180010101010101
(II) VESA(0): 	010101010101302a009851002a403070
(II) VESA(0): 	1300520e1100001e000000fd00384b1f
(II) VESA(0): 	500e000a202020202020000000ff0044
(II) VESA(0): 	3534323835344a305556530a000000fc
(II) VESA(0): 	0044454c4c204531373346500a20007b
(II) VESA(0): EDID vendor "DEL", prod id 40971
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) VESA(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 6a (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 102 (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 104 (1024x768)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 182 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 10d (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 10e (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 10f (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 960
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 120 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 192 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 193 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 194 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 195 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 960
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 196 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1a2 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 400
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1a3 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 1a4 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1a5 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1200
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1a6 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1600
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1b2 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 512
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1b3 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 1b4 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1b5 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1536
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1b6 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2048
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1c2 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1c3 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 1c4 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1c5 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 22
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 1c6 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 17
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 183 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 184 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 185 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 186 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 101 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 110 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 111 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 112 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 121 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 103 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 113 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 114 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 115 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2400
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 122 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 105 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 116 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 117 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 118 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 3072
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 123 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 107 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 119 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
*Mode: 11a (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 11b (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 3840
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 124 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc0005411
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
Mode: 109 (132x25)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 10a (132x43)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 130 (132x44)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 44
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.00-80.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Configured Monitor: Using maximum pixel clock of 140.00 MHz
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "400x300" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0): Display dimensions: (340, 270) mm
(**) VESA(0): DPI set to (59, 56)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[24] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[36] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[37] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[38] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[40] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[41] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI RADEON 9200
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: V280
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0xd0000000,0x1000000)
(II) VESA(0): virtual address = 0xb6929000,
	physical address = 0xd0000000, size = 16777216
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by CHaoSlayeR on 2009-04-27
@jbaird:

As you can read in the log your X is using the **xorg.conf.failsafe** which just chooses one of the graphics card for display and later on you can see that it uses the **VESA** driver to set your resolution to 800x600. So the first thing you will need to do is to get rid of the failsafe mode. For that we will need your Xorg.0.log.old. Please attach it here too as it should contain the real errors.


Greetz,

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-04-27
@hyphenistic:

Could you please post your current xorg.conf? I think I know what there is missing but I want to be sure.

Thanx,

C]-[aoZ

---

### Post by jbaird on 2009-04-27
OK.. fixed a few problems with my xorg.conf (missing mouse, etc).  Here is the new xorg.conf, as well as the Xorg.0.log.old.  I appreciate your help!  I think part of my problem here is that I am unclear as to how to define the Screen/Device relationships for two physical cards -- 2 lcd's on the first, and 1 lcd on the second.

```

## Monitors

Section "Monitor"
        Identifier "Lcd0"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "Lcd1"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "Lcd2"
        Option  "DPMS"
EndSection

## Video Cards

Section "Device"
        Identifier      "ati0"
        Driver          "radeon"
        BusID           "PCI:4:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "ati1"
        Driver          "radeon"
        BusID           "PCI:4:2:0"
        Screen          2
EndSection

## Screens

Section "Screen"
        Identifier      "screen0"
        Device          "ati0"
        Monitor         "Lcd0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "ati0"
        Monitor         "Lcd1"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen2"
        Device          "ati1"
        Monitor         "Lcd2"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

# Input Devices

Section "InputDevice"
        Identifier      "mouse1"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "keyboard1"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

# Server Layouts

Section "ServerLayout"
        Identifier "Multihead"
        Screen  "screen0"
        Screen  "screen1" RightOf "screen0"
        Screen  "screen2" RightOf "screen1"
        InputDevice     "mouse1" "CorePointer"
        InputDevice     "keyboard1" "CoreKeyboard"
        Option "Xinerama"
EndSection

```

Xorg.0.log.old:

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux cnsmonitor 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 27 07:10:31 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "screen0" (0)a
(**) |   |-->Monitor "Lcd0"
(**) |   |-->Device "ati0"
(**) |-->Screen "screen1" (1)
(**) |   |-->Monitor "Lcd1"
(**) |   |-->Device "ati0"
(**) |-->Screen "screen2" (2)
(**) |   |-->Monitor "Lcd2"
(**) |   |-->Device "ati1"
(**) |-->Input Device "mouse1"
(**) |-->Input Device "keyboard1"
(**) Option "Xinerama"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
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

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1028,01ad rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2772 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2776 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01ad rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01ad rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,27de card 1028,01ad rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,27b8 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1028,01ad rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1028,01ad rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01ad rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,1677 card 1028,01ad rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: 04:02:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe700000 - 0xfe7fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe6fffff (0x200000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xefffffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/19, 0xc0000000/28, 0xfeac0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/19
(--) PCI: (4:0:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xe0000000/28, 0xfe5e0000/16, I/O @ 0xd800/8, BIOS @ 0xfe600000/17
(--) PCI:*(4:2:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xd0000000/28, 0xfe5f0000/16, I/O @ 0xdc00/8, BIOS @ 0xfe600000/17
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
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 04:02:0
(WW) RADEON: More than one matching Device section for instances
	(BusID: PCI:4:0:0) found: ati0
(WW) RADEON: No matching Device section for instance (BusID PCI:4:2:0) found
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(EE) Screen 1 deleted because of no matching config section.
(II) UnloadModule: "radeon"
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[39] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[40] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[41] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[43] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[44] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[47] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000fe5e0000: size 64KB
(II) RADEON(0): PCI bus 4 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:04:00.0/rom: got 52KB
(--) RADEON(0): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(--) RADEON(0): BIOS at 0xfe600000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 18225, sclk: 182.250000, mclk: 238.500000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=18225
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Lcd0
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (340, 270) mm
(**) RADEON(0): DPI set to (95, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[7] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[8] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[9] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[10] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[15] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[19] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[24] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[25] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[26] 0	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[29] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[30] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[31] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[32] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[33] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[34] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[37] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[38] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[41] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[42] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[43] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[44] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[45] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[46] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[47] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[48] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[49] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[50] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[51] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit e0000000 0 0
(==) RADEON(0): Write-combining range (0xe0000000,0x10000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(0): Largest offscreen area available: 1280 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1838000
(II) RADEON(0): Will use depth buffer at offset 0x1e14000
(II) RADEON(0): Will use 225280 kb for textures at offset 0x23f0000
(WW) RADEON(0): Direct rendering is not supported when Xinerama is enabled
(EE) RADEON(0): [dri] DRIScreenInit failed.  Disabling DRI.
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1205)
(II) RADEON(0): Largest offscreen area available: 1280 x 6982
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7f84420]
2: /usr/bin/X(xf86RandR12SetRotations+0x6b) [0x80f9d2b]
3: /usr/bin/X(xf86CrtcScreenInit+0x9e) [0x80f588e]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONScreenInit+0x135a) [0xb7b29f3a]
5: /usr/bin/X(AddScreen+0x1fc) [0x8073d9c]
6: /usr/bin/X(InitOutput+0x21e) [0x80a9c4e]
7: /usr/bin/X(main+0x296) [0x8074526]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d1e450]
9: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

disable montype: 1
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV

```

Thanks

---

### Post by jbaird on 2009-04-27
I'm wondering if my second card is even being detected?

```

04:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
04:02.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

```

Is this one dual headed card, or is this showing both physical cards?

EDIT:  Nevermind.. I have confirmed that this is both physical cards.

---

### Post by CHaoSlayeR on 2009-04-27
OK, the first thing you do is getting rid of the Xinerama statement, as it prevents DRI:

```

...
(WW) RADEON(0): Direct rendering is not supported when Xinerama is enabled
(EE) RADEON(0): [dri] DRIScreenInit failed.  Disabling DRI.
...

```

The next thing is that the card probing yield to PCI paths not specified in the xorg.conf, so your card at **4:2:0** should be specified with BusID **4:02:0** instead, at least this is what I think the log wants to tell us:
```

...
(II) Primary Device is: PCI 04:02:0
(WW) RADEON: More than one matching Device section for instances
	(BusID: PCI:4:0:0) found: ati0
(WW) RADEON: No matching Device section for instance (BusID PCI:4:2:0) found
...

```

Then please get rid of those **Screen X** things in your Monitor sections as the monitors are already attached using the screen sections:

```

...
(EE) Screen 1 deleted because of no matching config section.
(II) UnloadModule: "radeon"
...

```

And then comes your dual-head issue on the first card. We will need to specify a **virtual** line if you want to have 2x 1280x1024 on one card:

```

(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf

```

What we will do now is setting up the dual-head card using the natural way without xinerama and with only a single screen section for both monitors on that card. First we need the available outputs, which we already found in the log:

```

(II) RADEON(0): Output **VGA-0** using monitor section Lcd0
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output **DVI-0** has no monitor section
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output **S-video** has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 

```

So here is your new xorg.conf (that should at least give us something to work with):

```

## Monitors

Section "Monitor"
        Identifier "Lcd0"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "Lcd1"
        Option  "DPMS"
        **Option  "RightOf" "Lcd0"**
EndSection

Section "Monitor"
        Identifier "Lcd2"
        Option  "DPMS"
EndSection

## Video Cards

Section "Device"
        Identifier      "ati0"
        Driver          "radeon"
        BusID           "PCI:4:0:0"
        **Option          "monitor-VGA-0" "Lcd0"**
        **Option          "monitor-DVI-0" "Lcd1"**
EndSection

Section "Device"
        Identifier      "ati1"
        Driver          "radeon"
        BusID           "PCI:4:02:0"
        **Option          "monitor-VGA-0" "Lcd2"**
EndSection

## Screens

Section "Screen"
        Identifier      "screen0"
        Device          "ati0"
        Monitor         "Lcd0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
                **Virtual 2560 1024**
        EndSubSection
EndSection

Section "Screen"
        Identifier      **"screen1"**
        Device          "ati1"
        Monitor         "Lcd2"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

# Input Devices

Section "InputDevice"
        Identifier      "mouse1"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "keyboard1"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

# Server Layouts

Section "ServerLayout"
        Identifier "Multihead"
        [b]Screen  "screen0"
        Screen  "screen1" RightOf "screen0"[/b]
        InputDevice     "mouse1" "CorePointer"
        InputDevice     "keyboard1" "CoreKeyboard"
EndSection

```


This should give us a picture or at least some new errors to work with.

Greetz,

C]-[aoZ

---

### Post by jbaird on 2009-04-28
OK.. getting closer!  The result of this xorg.conf is that the monitor connected to at1/monitor-VGA-0 is showing the GNOME login screen, but the keyboard and mouse do not work on this screen.  The other two screens (connected to ati0) are just showing the X11 "X" cursor mirrored.  I do have mouse control on these two screens, although they are mirrored.

Should I be able to move between all three screens eventually, or is this a limitation of this setup?

Here is my Xorg.0.log.. again, thanks for your help!

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux cnsmonitor 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 28 00:08:52 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "screen0" (0)
(**) |   |-->Monitor "Lcd0"
(**) |   |-->Device "ati0"
(**) |-->Screen "screen1" (1)
(**) |   |-->Monitor "Lcd2"
(**) |   |-->Device "ati1"
(**) |-->Input Device "mouse1"
(**) |-->Input Device "keyboard1"
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

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1028,01ad rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2772 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2776 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01ad rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01ad rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,27de card 1028,01ad rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,27b8 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1028,01ad rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1028,01ad rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01ad rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,1677 card 1028,01ad rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: 04:02:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe700000 - 0xfe7fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe6fffff (0x200000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xefffffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/19, 0xc0000000/28, 0xfeac0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/19
(--) PCI: (4:0:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xe0000000/28, 0xfe5e0000/16, I/O @ 0xd800/8, BIOS @ 0xfe600000/17
(--) PCI:*(4:2:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xd0000000/28, 0xfe5f0000/16, I/O @ 0xdc00/8, BIOS @ 0xfe600000/17
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
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 04:02:0
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[39] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[40] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[41] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[43] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[44] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[47] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) RADEON(0): MMIO registers at 0x00000000fe5e0000: size 64KB
(II) RADEON(0): PCI bus 4 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03b0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:04:00.0/rom: got 52KB
(--) RADEON(0): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(--) RADEON(0): BIOS at 0xfe600000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(WW) RADEON(0): Requested desktop size exceeds surface limts for tiling, ColorTiling disabled
(II) RADEON(0): Max desktop size set to 2560x1024
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 18225, sclk: 182.250000, mclk: 238.500000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=18225
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Lcd0
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 using monitor section Lcd1
(**) RADEON(0): Option "RightOf" "Lcd0"
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (340, 270) mm
(**) RADEON(0): DPI set to (191, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) RADEON(1): MMIO registers at 0x00000000fe5f0000: size 64KB
(II) RADEON(1): PCI bus 4 card 2 func 0
(**) RADEON(1): Depth 24, (--) framebuffer bpp 32
(II) RADEON(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(1): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) RADEON(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(1): RGB weight 888
(II) RADEON(1): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(1): initializing int10
(II) RADEON(1): Primary V_BIOS segment is: 0xc000
(--) RADEON(1): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(1): Linear framebuffer at 0x00000000d0000000
(--) RADEON(1): BIOS at 0xfe600000
(II) RADEON(1): PCI card detected
(II) RADEON(1): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
(II) RADEON(1): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(1): Page Flipping disabled
(II) RADEON(1): Will try to use DMA for Xv image transfers
(II) RADEON(1): Generation 2 PCI interface, using max accessible memory
(II) RADEON(1): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(1): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(1): Color tiling enabled by default
(II) RADEON(1): Max desktop size set to 2048x1200
(II) RADEON(1): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(1): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(1): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 18225, sclk: 182.250000, mclk: 238.500000
(II) RADEON(1): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=18225
(II) RADEON(1): Bios Connector table: 
(II) RADEON(1): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(1): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(1): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(1): Output VGA-0 using monitor section Lcd2
(II) RADEON(1): I2C bus "VGA-0" initialized.
(II) RADEON(1): Output DVI-0 has no monitor section
(II) RADEON(1): DFP table revision: 4
(II) RADEON(1): I2C bus "DVI-0" initialized.
(II) RADEON(1): Output S-video has no monitor section
(II) RADEON(1): Default TV standard: PAL
(II) RADEON(1): TV standards supported by chip: NTSC PAL 
(II) RADEON(1): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(1): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(1): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(1): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Using EDID range info for horizontal sync
(II) RADEON(1): Using EDID range info for vertical refresh
(II) RADEON(1): Printing DDC gathered Modelines:
(II) RADEON(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(1): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00b  Serial#: 810899027
(II) RADEON(1): Year: 2005  Week: 17
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): Default color space is primary color space
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) RADEON(1): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): Serial No: D542854J0UVS
(II) RADEON(1): Monitor name: DELL E173FP
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0ba053565530
(II) RADEON(1): 	110f010368221b78eecaf6a357479e23
(II) RADEON(1): 	114f54a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000fd00384b1f
(II) RADEON(1): 	500e000a202020202020000000ff0044
(II) RADEON(1): 	3534323835344a305556530a000000fc
(II) RADEON(1): 	0044454c4c204531373346500a20007b
finished output detect: 0
(II) RADEON(1): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(1): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00a  Serial#: 1095388726
(II) RADEON(1): Year: 2004  Week: 5
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(1): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Serial No: J180641VAJN6
(II) RADEON(1): Monitor name: DELL E172FP
(II) RADEON(1): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0aa0364e4a41
(II) RADEON(1): 	050e010368221b78eaaea5a6544c9926
(II) RADEON(1): 	145054a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000ff004a3138
(II) RADEON(1): 	3036343156414a4e360a000000fc0044
(II) RADEON(1): 	454c4c204531373246500a20000000fd
(II) RADEON(1): 	00384c1f500e000a2020202020200027
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Using hsync ranges from config file
(II) RADEON(1): Using vrefresh ranges from config file
(II) RADEON(1): Printing DDC gathered Modelines:
(II) RADEON(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(1): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00b  Serial#: 810899027
(II) RADEON(1): Year: 2005  Week: 17
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): Default color space is primary color space
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) RADEON(1): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): Serial No: D542854J0UVS
(II) RADEON(1): Monitor name: DELL E173FP
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0ba053565530
(II) RADEON(1): 	110f010368221b78eecaf6a357479e23
(II) RADEON(1): 	114f54a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000fd00384b1f
(II) RADEON(1): 	500e000a202020202020000000ff0044
(II) RADEON(1): 	3534323835344a305556530a000000fc
(II) RADEON(1): 	0044454c4c204531373346500a20007b
in RADEONProbeOutputModes
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00a  Serial#: 1095388726
(II) RADEON(1): Year: 2004  Week: 5
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(1): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Serial No: J180641VAJN6
(II) RADEON(1): Monitor name: DELL E172FP
(II) RADEON(1): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0aa0364e4a41
(II) RADEON(1): 	050e010368221b78eaaea5a6544c9926
(II) RADEON(1): 	145054a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000ff004a3138
(II) RADEON(1): 	3036343156414a4e360a000000fc0044
(II) RADEON(1): 	454c4c204531373246500a20000000fd
(II) RADEON(1): 	00384c1f500e000a2020202020200027
in RADEONProbeOutputModes
(II) RADEON(1): EDID vendor "DEL", prod id 40970
(II) RADEON(1): Output VGA-0 connected
(II) RADEON(1): Output DVI-0 connected
(II) RADEON(1): Output S-video disconnected
(II) RADEON(1): Output VGA-0 using initial mode 1280x1024
(II) RADEON(1): Output DVI-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(1): Display dimensions: (340, 270) mm
(**) RADEON(1): DPI set to (95, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(==) RADEON(1): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(1): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(==) RADEON(1): Assuming overlay scaler buffer width is 1536
(II) RADEON(1): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(1): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(1): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B]
	[1] 1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B]
	[3] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[9] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[10] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[16] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[17] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[20] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[25] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[26] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[27] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[28] 1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[29] 0	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[33] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[34] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[35] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[36] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[37] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[38] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[39] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[40] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[41] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[42] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[43] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[45] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[46] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[47] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[48] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[49] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[50] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[53] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[54] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
(==) RADEON(0): Write-combining range (0xe0000000,0x10000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (2560,8191)
(II) RADEON(0): Reserved area from (0,1024) to (2560,1026)
(II) RADEON(0): Largest offscreen area available: 2560 x 7165
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x2800000
(II) RADEON(0): Will use depth buffer at offset 0x3200000
(II) RADEON(0): Will use 200704 kb for textures at offset 0x3c00000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 8192 kB allocated with handle 0x00000000
(II) RADEON(0): [pci] ring handle = 0xf8e0e000
(II) RADEON(0): [pci] Ring mapped at 0xb7977000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf8f0f000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb7976000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8f10000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xa76b4000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf9110000
(II) RADEON(0): [pci] GART Texture map mapped at 0xa71d4000
(II) RADEON(0): [drm] register handle = 0xfe5e0000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xefffe000 is: 0xefffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xffffffc0
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1026)
(II) RADEON(0): Using hardware cursor 1 (scanline 1027)
(II) RADEON(0): Largest offscreen area available: 2560 x 7161
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) RADEON(1): RADEONScreenInit d0000000 0 0
(==) RADEON(1): Write-combining range (0xd0000000,0x10000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
disable montype: 1
(==) RADEON(1): Using 24 bit depth buffer
(II) RADEON(1): RADEONInitMemoryMap() : 
(II) RADEON(1):   mem_size         : 0x10000000
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(1): Depth moves disabled by default
(II) RADEON(1): CP in BM mode
(II) RADEON(1): Using 8 MB GART aperture
(II) RADEON(1): Using 1 MB for the ring buffer
(II) RADEON(1): Using 2 MB for vertex/indirect buffers
(II) RADEON(1): Using 5 MB for GART textures
(II) RADEON(1): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(1): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(1): Largest offscreen area available: 1280 x 6989
(II) RADEON(1): Will use front buffer at offset 0x0
(II) RADEON(1): Will use back buffer at offset 0x1838000
(II) RADEON(1): Will use depth buffer at offset 0x1e14000
(II) RADEON(1): Will use 225280 kb for textures at offset 0x23f0000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(1): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(1): [drm] framebuffer handle = 0xd0000000
(II) RADEON(1): [drm] added 1 reserved context for kernel
(II) RADEON(1): X context handle = 0x1
(II) RADEON(1): [drm] installed DRM signal handler
(II) RADEON(1): [pci] 8192 kB allocated with handle 0x00000000
(II) RADEON(1): [pci] ring handle = 0xf9631000
(II) RADEON(1): [pci] Ring mapped at 0x96ec1000
(II) RADEON(1): [pci] Ring contents 0x00000000
(II) RADEON(1): [pci] ring read ptr handle = 0xf9732000
(II) RADEON(1): [pci] Ring read ptr mapped at 0x96ec0000
(II) RADEON(1): [pci] Ring read ptr contents 0x00000000
(II) RADEON(1): [pci] vertex/indirect buffers handle = 0xf9733000
(II) RADEON(1): [pci] Vertex/indirect buffers mapped at 0x96cc0000
(II) RADEON(1): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(1): [pci] GART texture map handle = 0xf9933000
(II) RADEON(1): [pci] GART Texture map mapped at 0x967e0000
(II) RADEON(1): [drm] register handle = 0xfe5f0000
(II) RADEON(1): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0x1fff0000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
disable montype: 1
init memmap
init common
init crtc2
init pll2
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
disable montype: 1
disable montype: 1
(==) RADEON(1): Backing store disabled
(II) RADEON(1): [DRI] installation complete
(II) RADEON(1): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(1): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(1): [drm] dma control initialized, using IRQ 20
(II) RADEON(1): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(1): DRI init changed memory map, adjusting ...
(WW) RADEON(1):   MC_FB_LOCATION  was: 0xdfffd000 is: 0xdfffd000
(WW) RADEON(1):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xffffffc0
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(1): Direct rendering enabled
(II) RADEON(1): Render acceleration enabled
(II) RADEON(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(1): Acceleration enabled
(**) Option "dpms"
(**) RADEON(1): DPMS enabled
(==) RADEON(1): Silken mouse enabled
(II) RADEON(1): Using hardware cursor 0 (scanline 1202)
(II) RADEON(1): Using hardware cursor 1 (scanline 1205)
(II) RADEON(1): Largest offscreen area available: 1280 x 6982
(II) RADEON(1): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Reloading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) RADEON(1): no multimedia table present, disabling Rage Theatre.
(II) RADEON(1): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 1
(II) RADEON(0): Setting screen physical size to 338 x 270
(II) RADEON(1): Setting screen physical size to 338 x 270
(WW) mouse1: No Device specified, looking for one...
(II) mouse1: Setting Device option to "/dev/input/mice"
(--) mouse1: Device: "/dev/input/mice"
(==) mouse1: Protocol: "Auto"
(**) Option "CorePointer"
(**) mouse1: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) mouse1: Emulate3Buttons, Emulate3Timeout: 50
(**) mouse1: ZAxisMapping: buttons 4 and 5
(**) mouse1: Buttons: 9
(**) mouse1: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) keyboard1: always reports core events
(**) Option "Protocol" "standard"
(**) keyboard1: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) keyboard1: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) keyboard1: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) keyboard1: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) keyboard1: CustomKeycodes disabled
(II) evaluating device (keyboard1)
(II) XINPUT: Adding extended input device "keyboard1" (type: KEYBOARD)
(II) evaluating device (mouse1)
(II) XINPUT: Adding extended input device "mouse1" (type: MOUSE)
(--) mouse1: PnP-detected protocol: "ExplorerPS/2"
(II) mouse1: ps2EnableDataReporting: succeeded
enable montype: 1
enable montype: 1
enable montype: 1
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0

```

---

### Post by arazyal on 2009-04-28
Could you try the following and tell me what you get?

It seems like we have the same setup, both my cards are radeon as well

I get 2 out of the 3 working monitors
Basicly screen1 and both monitors come on
screen2 with the single monitor never comes on :/

```


Section "Monitor"
        Identifier      "screen1"
        Gamma   1.0
EndSection

Section "Monitor"
        Identifier      "screen2"
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "screen1"
        Defaultdepth    24
        Monitor         "screen1"
        SubSection "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen2"
        Device          "screen2"
        Defaultdepth    24
        Monitor         "screen2"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen  "screen1" 0 0
        screen  "screen2" leftof "screen1"
EndSection

Section "Device"
        Identifier      "screen2"
        BusID           "PCI:4:00:0"
EndSection

Section "Device"
        Identifier      "screen1"
        BusID           "PCI:4:02:0"
EndSection


```

---

### Post by jbaird on 2009-04-28
Hm.. you aren't even specifying which driver to use on the devices?

---

### Post by CHaoSlayeR on 2009-04-28
@jbaird:

I'm a bit unsure what to do next because overall the log looks good. Although some details disturb me a bit, e.g.:

```

...
(WW) RADEON(0): Requested desktop size exceeds surface limts for tiling, ColorTiling disabled
...
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
...

```

^^ This is for the card with the dual-head setup and it might be that this does interfere correct desktop setup. Could you try again with another login manager, e.g. the XDM?

Additional can you try to simply omit the mouse sections and let the X do the detection? It also might fix some things (unless it doesn't work without such a section for you):

```

...
(WW) mouse1: No Device specified, looking for one...
...

```

In the end we are on the right track as even DRI gets initialized for both cards without problems:
```

...
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
...
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 1
...

```

Furthermore I would be interested in the output of **xrandr --verbose**.


@arazyal:

I don't think that it is of much help when you reuse "screen1" or the like for all types of sections as identifier. In addition what version of Ubuntu are you using, which graphics cards and setup? And please attach your Xorg.0.log as only that one provides reasonable information for troubleshooting your configuration.

But as a frist start try to use some reasonable identifiers for non-screen sections and specify the driver for the devices. Although the right should be picked by the system it enables you to use special configuration options.

Greetz,

C]-[aoZ

---

### Post by jbaird on 2009-04-28
CHaoSlayeR,

With this setup in it's optimal state.. does it provide three screens that you can drag windows across (ie, one large desktop)?

---

### Post by CHaoSlayeR on 2009-04-28
That depends. At least in my previous setup with Hardy and three cards it did. So I think it should on yours. Also I must say that I did use Xubuntu as the XFCE just did what it was supposed to do. As I haven't used Gnome ever on one of my machines I can't say if there are differences in display/desktop setup.

---

### Post by jbaird on 2009-04-28
Ahh.. ok, maybe I should try Xbunutu.  I was under the impression that you had to enable Xinerama to have one large desktop shared between the 3 monitors.

---

### Post by jbaird on 2009-04-29
OK.. much closer with Xubuntu!  I have all three monitors working right now.  The dual headed card with two monitors connected is showing two mirrors of each other with no Gnome taskbar.  The other monitor connected to the other card is the main monitor, but after logging in, I can't get the mouse to move over to this screen.

So.. how do we make all three of these monitors act as one large desktop?  And, how do I make the mouse move back over to the main display?

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux cnsmonitor 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 29 00:54:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "screen0" (0)
(**) |   |-->Monitor "Lcd0"
(**) |   |-->Device "ati0"
(**) |-->Screen "screen1" (1)
(**) |   |-->Monitor "Lcd2"
(**) |   |-->Device "ati1"
(**) |-->Input Device "mouse1"
(**) |-->Input Device "keyboard1"
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

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1028,01ad rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2772 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2776 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01ad rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01ad rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,27de card 1028,01ad rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,27b8 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1028,01ad rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1028,01ad rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01ad rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,1677 card 1028,01ad rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: 04:02:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe700000 - 0xfe7fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe6fffff (0x200000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xefffffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/19, 0xc0000000/28, 0xfeac0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/19
(--) PCI: (4:0:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xe0000000/28, 0xfe5e0000/16, I/O @ 0xd800/8, BIOS @ 0xfe600000/17
(--) PCI:*(4:2:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xd0000000/28, 0xfe5f0000/16, I/O @ 0xdc00/8, BIOS @ 0xfe600000/17
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
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 04:02:0
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[39] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[40] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[41] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[43] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[44] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[47] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) RADEON(0): MMIO registers at 0x00000000fe5e0000: size 64KB
(II) RADEON(0): PCI bus 4 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03b0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:04:00.0/rom: got 52KB
(--) RADEON(0): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(--) RADEON(0): BIOS at 0xfe600000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(WW) RADEON(0): Requested desktop size exceeds surface limts for tiling, ColorTiling disabled
(II) RADEON(0): Max desktop size set to 2560x1024
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 18225, sclk: 182.250000, mclk: 238.500000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=18225
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Lcd0
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 using monitor section Lcd1
(**) RADEON(0): Option "RightOf" "Lcd0"
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (340, 270) mm
(**) RADEON(0): DPI set to (191, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) RADEON(1): MMIO registers at 0x00000000fe5f0000: size 64KB
(II) RADEON(1): PCI bus 4 card 2 func 0
(**) RADEON(1): Depth 24, (--) framebuffer bpp 32
(II) RADEON(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(1): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) RADEON(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(1): RGB weight 888
(II) RADEON(1): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(1): initializing int10
(II) RADEON(1): Primary V_BIOS segment is: 0xc000
(--) RADEON(1): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(1): Linear framebuffer at 0x00000000d0000000
(--) RADEON(1): BIOS at 0xfe600000
(II) RADEON(1): PCI card detected
(II) RADEON(1): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
(II) RADEON(1): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(1): Page Flipping disabled
(II) RADEON(1): Will try to use DMA for Xv image transfers
(II) RADEON(1): Generation 2 PCI interface, using max accessible memory
(II) RADEON(1): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(1): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(1): Color tiling enabled by default
(II) RADEON(1): Max desktop size set to 2048x1200
(II) RADEON(1): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(1): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(1): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 18225, sclk: 182.250000, mclk: 238.500000
(II) RADEON(1): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=18225
(II) RADEON(1): Bios Connector table: 
(II) RADEON(1): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(1): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(1): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(1): Output VGA-0 using monitor section Lcd2
(II) RADEON(1): I2C bus "VGA-0" initialized.
(II) RADEON(1): Output DVI-0 has no monitor section
(II) RADEON(1): DFP table revision: 4
(II) RADEON(1): I2C bus "DVI-0" initialized.
(II) RADEON(1): Output S-video has no monitor section
(II) RADEON(1): Default TV standard: PAL
(II) RADEON(1): TV standards supported by chip: NTSC PAL 
(II) RADEON(1): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(1): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(1): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(1): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Using EDID range info for horizontal sync
(II) RADEON(1): Using EDID range info for vertical refresh
(II) RADEON(1): Printing DDC gathered Modelines:
(II) RADEON(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(1): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00b  Serial#: 810899027
(II) RADEON(1): Year: 2005  Week: 17
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): Default color space is primary color space
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) RADEON(1): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): Serial No: D542854J0UVS
(II) RADEON(1): Monitor name: DELL E173FP
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0ba053565530
(II) RADEON(1): 	110f010368221b78eecaf6a357479e23
(II) RADEON(1): 	114f54a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000fd00384b1f
(II) RADEON(1): 	500e000a202020202020000000ff0044
(II) RADEON(1): 	3534323835344a305556530a000000fc
(II) RADEON(1): 	0044454c4c204531373346500a20007b
finished output detect: 0
(II) RADEON(1): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(1): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00a  Serial#: 1095388726
(II) RADEON(1): Year: 2004  Week: 5
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(1): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Serial No: J180641VAJN6
(II) RADEON(1): Monitor name: DELL E172FP
(II) RADEON(1): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0aa0364e4a41
(II) RADEON(1): 	050e010368221b78eaaea5a6544c9926
(II) RADEON(1): 	145054a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000ff004a3138
(II) RADEON(1): 	3036343156414a4e360a000000fc0044
(II) RADEON(1): 	454c4c204531373246500a20000000fd
(II) RADEON(1): 	00384c1f500e000a2020202020200027
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Using hsync ranges from config file
(II) RADEON(1): Using vrefresh ranges from config file
(II) RADEON(1): Printing DDC gathered Modelines:
(II) RADEON(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(1): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00b  Serial#: 810899027
(II) RADEON(1): Year: 2005  Week: 17
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): Default color space is primary color space
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) RADEON(1): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): Serial No: D542854J0UVS
(II) RADEON(1): Monitor name: DELL E173FP
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0ba053565530
(II) RADEON(1): 	110f010368221b78eecaf6a357479e23
(II) RADEON(1): 	114f54a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000fd00384b1f
(II) RADEON(1): 	500e000a202020202020000000ff0044
(II) RADEON(1): 	3534323835344a305556530a000000fc
(II) RADEON(1): 	0044454c4c204531373346500a20007b
in RADEONProbeOutputModes
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00a  Serial#: 1095388726
(II) RADEON(1): Year: 2004  Week: 5
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(1): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Serial No: J180641VAJN6
(II) RADEON(1): Monitor name: DELL E172FP
(II) RADEON(1): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0aa0364e4a41
(II) RADEON(1): 	050e010368221b78eaaea5a6544c9926
(II) RADEON(1): 	145054a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000ff004a3138
(II) RADEON(1): 	3036343156414a4e360a000000fc0044
(II) RADEON(1): 	454c4c204531373246500a20000000fd
(II) RADEON(1): 	00384c1f500e000a2020202020200027
in RADEONProbeOutputModes
(II) RADEON(1): EDID vendor "DEL", prod id 40970
(II) RADEON(1): Output VGA-0 connected
(II) RADEON(1): Output DVI-0 connected
(II) RADEON(1): Output S-video disconnected
(II) RADEON(1): Output VGA-0 using initial mode 1280x1024
(II) RADEON(1): Output DVI-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(1): Display dimensions: (340, 270) mm
(**) RADEON(1): DPI set to (95, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(==) RADEON(1): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(1): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(==) RADEON(1): Assuming overlay scaler buffer width is 1536
(II) RADEON(1): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(1): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(1): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B]
	[1] 1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B]
	[3] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[9] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[10] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[16] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[17] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[20] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[25] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[26] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[27] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[28] 1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[29] 0	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[33] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[34] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[35] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[36] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[37] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[38] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[39] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[40] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[41] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[42] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[43] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[45] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[46] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[47] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[48] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[49] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[50] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[53] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[54] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
(==) RADEON(0): Write-combining range (0xe0000000,0x10000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (2560,8191)
(II) RADEON(0): Reserved area from (0,1024) to (2560,1026)
(II) RADEON(0): Largest offscreen area available: 2560 x 7165
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x2800000
(II) RADEON(0): Will use depth buffer at offset 0x3200000
(II) RADEON(0): Will use 200704 kb for textures at offset 0x3c00000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 8192 kB allocated with handle 0x00000000
(II) RADEON(0): [pci] ring handle = 0xf8e0e000
(II) RADEON(0): [pci] Ring mapped at 0xb7945000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf8f0f000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb7944000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8f10000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xa7682000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf9110000
(II) RADEON(0): [pci] GART Texture map mapped at 0xa71a2000
(II) RADEON(0): [drm] register handle = 0xfe5e0000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xefffe000 is: 0xefffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xffffffc0
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1026)
(II) RADEON(0): Using hardware cursor 1 (scanline 1027)
(II) RADEON(0): Largest offscreen area available: 2560 x 7161
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) RADEON(1): RADEONScreenInit d0000000 0 0
(==) RADEON(1): Write-combining range (0xd0000000,0x10000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
disable montype: 1
(==) RADEON(1): Using 24 bit depth buffer
(II) RADEON(1): RADEONInitMemoryMap() : 
(II) RADEON(1):   mem_size         : 0x10000000
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(1): Depth moves disabled by default
(II) RADEON(1): CP in BM mode
(II) RADEON(1): Using 8 MB GART aperture
(II) RADEON(1): Using 1 MB for the ring buffer
(II) RADEON(1): Using 2 MB for vertex/indirect buffers
(II) RADEON(1): Using 5 MB for GART textures
(II) RADEON(1): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(1): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(1): Largest offscreen area available: 1280 x 6989
(II) RADEON(1): Will use front buffer at offset 0x0
(II) RADEON(1): Will use back buffer at offset 0x1838000
(II) RADEON(1): Will use depth buffer at offset 0x1e14000
(II) RADEON(1): Will use 225280 kb for textures at offset 0x23f0000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(1): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(1): [drm] framebuffer handle = 0xd0000000
(II) RADEON(1): [drm] added 1 reserved context for kernel
(II) RADEON(1): X context handle = 0x1
(II) RADEON(1): [drm] installed DRM signal handler
(II) RADEON(1): [pci] 8192 kB allocated with handle 0x00000000
(II) RADEON(1): [pci] ring handle = 0xf9631000
(II) RADEON(1): [pci] Ring mapped at 0x96e8f000
(II) RADEON(1): [pci] Ring contents 0x00000000
(II) RADEON(1): [pci] ring read ptr handle = 0xf9732000
(II) RADEON(1): [pci] Ring read ptr mapped at 0x96e8e000
(II) RADEON(1): [pci] Ring read ptr contents 0x00000000
(II) RADEON(1): [pci] vertex/indirect buffers handle = 0xf9733000
(II) RADEON(1): [pci] Vertex/indirect buffers mapped at 0x96c8e000
(II) RADEON(1): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(1): [pci] GART texture map handle = 0xf9933000
(II) RADEON(1): [pci] GART Texture map mapped at 0x967ae000
(II) RADEON(1): [drm] register handle = 0xfe5f0000
(II) RADEON(1): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0x1fff0000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
disable montype: 1
init memmap
init common
init crtc2
init pll2
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
disable montype: 1
disable montype: 1
(==) RADEON(1): Backing store disabled
(II) RADEON(1): [DRI] installation complete
(II) RADEON(1): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(1): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(1): [drm] dma control initialized, using IRQ 20
(II) RADEON(1): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(1): DRI init changed memory map, adjusting ...
(WW) RADEON(1):   MC_FB_LOCATION  was: 0xdfffd000 is: 0xdfffd000
(WW) RADEON(1):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xffffffc0
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(1): Direct rendering enabled
(II) RADEON(1): Render acceleration enabled
(II) RADEON(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(1): Acceleration enabled
(**) Option "dpms"
(**) RADEON(1): DPMS enabled
(==) RADEON(1): Silken mouse enabled
(II) RADEON(1): Using hardware cursor 0 (scanline 1202)
(II) RADEON(1): Using hardware cursor 1 (scanline 1205)
(II) RADEON(1): Largest offscreen area available: 1280 x 6982
(II) RADEON(1): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Reloading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) RADEON(1): no multimedia table present, disabling Rage Theatre.
(II) RADEON(1): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 1
(II) RADEON(0): Setting screen physical size to 338 x 270
(II) RADEON(1): Setting screen physical size to 338 x 270
(WW) mouse1: No Device specified, looking for one...
(II) mouse1: Setting Device option to "/dev/input/mice"
(--) mouse1: Device: "/dev/input/mice"
(==) mouse1: Protocol: "Auto"
(**) Option "CorePointer"
(**) mouse1: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) mouse1: Emulate3Buttons, Emulate3Timeout: 50
(**) mouse1: ZAxisMapping: buttons 4 and 5
(**) mouse1: Buttons: 9
(**) mouse1: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) keyboard1: always reports core events
(**) Option "Protocol" "standard"
(**) keyboard1: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) keyboard1: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) keyboard1: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) keyboard1: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) keyboard1: CustomKeycodes disabled
(II) evaluating device (keyboard1)
(II) XINPUT: Adding extended input device "keyboard1" (type: KEYBOARD)
(II) evaluating device (mouse1)
(II) XINPUT: Adding extended input device "mouse1" (type: MOUSE)
(--) mouse1: PnP-detected protocol: "ExplorerPS/2"
(II) mouse1: ps2EnableDataReporting: succeeded
enable montype: 1
enable montype: 1
enable montype: 1
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
SetClientVersion: 0 9
SetKbdSettings - type: -1081007156 rate: 30 delay: 500 snumlk: 28
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux cnsmonitor 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 29 00:54:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Multihead"
(**) |-->Screen "screen0" (0)
(**) |   |-->Monitor "Lcd0"
(**) |   |-->Device "ati0"
(**) |-->Screen "screen1" (1)
(**) |   |-->Monitor "Lcd2"
(**) |   |-->Device "ati1"
(**) |-->Input Device "mouse1"
(**) |-->Input Device "keyboard1"
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

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1028,01ad rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2772 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2776 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01ad rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01ad rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,27de card 1028,01ad rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,27b8 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1028,01ad rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1028,01ad rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01ad rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,1677 card 1028,01ad rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: 04:02:0: chip 1002,5960 card 1092,0160 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe700000 - 0xfe7fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfe500000 - 0xfe6fffff (0x200000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xefffffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/19, 0xc0000000/28, 0xfeac0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/19
(--) PCI: (4:0:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xe0000000/28, 0xfe5e0000/16, I/O @ 0xd800/8, BIOS @ 0xfe600000/17
(--) PCI:*(4:2:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xd0000000/28, 0xfe5f0000/16, I/O @ 0xdc00/8, BIOS @ 0xfe600000/17
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
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[1] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[2] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[5] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[22] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[1] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[3] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[4] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[5] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[7] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 04:02:0
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(--) Chipset ATI Radeon 9250 5960 (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[21] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[33] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[5] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[6] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[9] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[12] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[27] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[28] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[29] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[30] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[31] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[34] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[35] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[38] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[39] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[40] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[41] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[43] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[44] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[47] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) RADEON(0): MMIO registers at 0x00000000fe5e0000: size 64KB
(II) RADEON(0): PCI bus 4 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03b0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:04:00.0/rom: got 52KB
(--) RADEON(0): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(0): Linear framebuffer at 0x00000000e0000000
(--) RADEON(0): BIOS at 0xfe600000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(WW) RADEON(0): Requested desktop size exceeds surface limts for tiling, ColorTiling disabled
(II) RADEON(0): Max desktop size set to 2560x1024
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 18225, sclk: 182.250000, mclk: 238.500000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=18225
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Lcd0
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 using monitor section Lcd1
(**) RADEON(0): Option "RightOf" "Lcd0"
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (340, 270) mm
(**) RADEON(0): DPI set to (191, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) RADEON(1): MMIO registers at 0x00000000fe5f0000: size 64KB
(II) RADEON(1): PCI bus 4 card 2 func 0
(**) RADEON(1): Depth 24, (--) framebuffer bpp 32
(II) RADEON(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(1): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) RADEON(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(1): RGB weight 888
(II) RADEON(1): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(1): initializing int10
(II) RADEON(1): Primary V_BIOS segment is: 0xc000
(--) RADEON(1): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(1): Linear framebuffer at 0x00000000d0000000
(--) RADEON(1): BIOS at 0xfe600000
(II) RADEON(1): PCI card detected
(II) RADEON(1): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
(II) RADEON(1): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(==) RADEON(1): Page Flipping disabled
(II) RADEON(1): Will try to use DMA for Xv image transfers
(II) RADEON(1): Generation 2 PCI interface, using max accessible memory
(II) RADEON(1): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(1): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(1): Color tiling enabled by default
(II) RADEON(1): Max desktop size set to 2048x1200
(II) RADEON(1): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(1): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(1): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 18225, sclk: 182.250000, mclk: 238.500000
(II) RADEON(1): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=18225
(II) RADEON(1): Bios Connector table: 
(II) RADEON(1): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(1): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(1): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(1): Output VGA-0 using monitor section Lcd2
(II) RADEON(1): I2C bus "VGA-0" initialized.
(II) RADEON(1): Output DVI-0 has no monitor section
(II) RADEON(1): DFP table revision: 4
(II) RADEON(1): I2C bus "DVI-0" initialized.
(II) RADEON(1): Output S-video has no monitor section
(II) RADEON(1): Default TV standard: PAL
(II) RADEON(1): TV standards supported by chip: NTSC PAL 
(II) RADEON(1): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(1): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(1): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(1): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Using EDID range info for horizontal sync
(II) RADEON(1): Using EDID range info for vertical refresh
(II) RADEON(1): Printing DDC gathered Modelines:
(II) RADEON(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(1): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00b  Serial#: 810899027
(II) RADEON(1): Year: 2005  Week: 17
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): Default color space is primary color space
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) RADEON(1): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): Serial No: D542854J0UVS
(II) RADEON(1): Monitor name: DELL E173FP
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0ba053565530
(II) RADEON(1): 	110f010368221b78eecaf6a357479e23
(II) RADEON(1): 	114f54a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000fd00384b1f
(II) RADEON(1): 	500e000a202020202020000000ff0044
(II) RADEON(1): 	3534323835344a305556530a000000fc
(II) RADEON(1): 	0044454c4c204531373346500a20007b
finished output detect: 0
(II) RADEON(1): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(1): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00a  Serial#: 1095388726
(II) RADEON(1): Year: 2004  Week: 5
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(1): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Serial No: J180641VAJN6
(II) RADEON(1): Monitor name: DELL E172FP
(II) RADEON(1): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0aa0364e4a41
(II) RADEON(1): 	050e010368221b78eaaea5a6544c9926
(II) RADEON(1): 	145054a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000ff004a3138
(II) RADEON(1): 	3036343156414a4e360a000000fc0044
(II) RADEON(1): 	454c4c204531373246500a20000000fd
(II) RADEON(1): 	00384c1f500e000a2020202020200027
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Using hsync ranges from config file
(II) RADEON(1): Using vrefresh ranges from config file
(II) RADEON(1): Printing DDC gathered Modelines:
(II) RADEON(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(1): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00b  Serial#: 810899027
(II) RADEON(1): Year: 2005  Week: 17
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): Default color space is primary color space
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) RADEON(1): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): Serial No: D542854J0UVS
(II) RADEON(1): Monitor name: DELL E173FP
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0ba053565530
(II) RADEON(1): 	110f010368221b78eecaf6a357479e23
(II) RADEON(1): 	114f54a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000fd00384b1f
(II) RADEON(1): 	500e000a202020202020000000ff0044
(II) RADEON(1): 	3534323835344a305556530a000000fc
(II) RADEON(1): 	0044454c4c204531373346500a20007b
in RADEONProbeOutputModes
(II) RADEON(1): EDID vendor "DEL", prod id 40971
(II) RADEON(1): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(1): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(1): Manufacturer: DEL  Model: a00a  Serial#: 1095388726
(II) RADEON(1): Year: 2004  Week: 5
(II) RADEON(1): EDID Version: 1.3
(II) RADEON(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(1): Sync:  Separate
(II) RADEON(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(1): Gamma: 2.20
(II) RADEON(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(1): First detailed timing is preferred mode
(II) RADEON(1): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(1): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(1): Supported VESA Video Modes:
(II) RADEON(1): 720x400@70Hz
(II) RADEON(1): 640x480@60Hz
(II) RADEON(1): 640x480@75Hz
(II) RADEON(1): 800x600@60Hz
(II) RADEON(1): 800x600@75Hz
(II) RADEON(1): 1024x768@60Hz
(II) RADEON(1): 1024x768@75Hz
(II) RADEON(1): 1280x1024@75Hz
(II) RADEON(1): Manufacturer's mask: 0
(II) RADEON(1): Supported Future Video Modes:
(II) RADEON(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(1): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(1): Supported additional Video Mode:
(II) RADEON(1): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(1): Serial No: J180641VAJN6
(II) RADEON(1): Monitor name: DELL E172FP
(II) RADEON(1): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(1): EDID (in hex):
(II) RADEON(1): 	00ffffffffffff0010ac0aa0364e4a41
(II) RADEON(1): 	050e010368221b78eaaea5a6544c9926
(II) RADEON(1): 	145054a54b00714f8180010101010101
(II) RADEON(1): 	010101010101302a009851002a403070
(II) RADEON(1): 	1300520e1100001e000000ff004a3138
(II) RADEON(1): 	3036343156414a4e360a000000fc0044
(II) RADEON(1): 	454c4c204531373246500a20000000fd
(II) RADEON(1): 	00384c1f500e000a2020202020200027
in RADEONProbeOutputModes
(II) RADEON(1): EDID vendor "DEL", prod id 40970
(II) RADEON(1): Output VGA-0 connected
(II) RADEON(1): Output DVI-0 connected
(II) RADEON(1): Output S-video disconnected
(II) RADEON(1): Output VGA-0 using initial mode 1280x1024
(II) RADEON(1): Output DVI-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(1): Display dimensions: (340, 270) mm
(**) RADEON(1): DPI set to (95, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(==) RADEON(1): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) RADEON(1): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(==) RADEON(1): Assuming overlay scaler buffer width is 1536
(II) RADEON(1): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(1): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(1): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B]
	[1] 1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B]
	[3] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xfe8f0000 - 0xfe8fffff (0x10000) MX[B]
	[9] -1	0	0xfeabf900 - 0xfeabf9ff (0x100) MX[B]
	[10] -1	0	0xfeabfa00 - 0xfeabfbff (0x200) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xfe520000 - 0xfe53ffff (0x20000) MX[B](B)
	[13] -1	0	0xfe5f0000 - 0xfe5fffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[16] -1	0	0xfe500000 - 0xfe51ffff (0x20000) MX[B](B)
	[17] -1	0	0xfe5e0000 - 0xfe5effff (0x10000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[19] -1	0	0xfeac0000 - 0xfeafffff (0x40000) MX[B](B)
	[20] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xfeb00000 - 0xfeb7ffff (0x80000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[25] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[26] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[27] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[28] 1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[29] 0	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[33] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[34] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[35] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[36] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[37] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[38] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[39] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[40] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[41] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[42] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[43] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[44] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[45] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[46] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[47] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[48] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B](B)
	[49] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B](B)
	[50] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[53] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[54] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e0000000 0 0
(==) RADEON(0): Write-combining range (0xe0000000,0x10000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (2560,8191)
(II) RADEON(0): Reserved area from (0,1024) to (2560,1026)
(II) RADEON(0): Largest offscreen area available: 2560 x 7165
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x2800000
(II) RADEON(0): Will use depth buffer at offset 0x3200000
(II) RADEON(0): Will use 200704 kb for textures at offset 0x3c00000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 8192 kB allocated with handle 0x00000000
(II) RADEON(0): [pci] ring handle = 0xf8e0e000
(II) RADEON(0): [pci] Ring mapped at 0xb7945000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf8f0f000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb7944000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8f10000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xa7682000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf9110000
(II) RADEON(0): [pci] GART Texture map mapped at 0xa71a2000
(II) RADEON(0): [drm] register handle = 0xfe5e0000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0x1fff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xefffe000 is: 0xefffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xffffffc0
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xefffe000 0xefffe000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1026)
(II) RADEON(0): Using hardware cursor 1 (scanline 1027)
(II) RADEON(0): Largest offscreen area available: 2560 x 7161
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) RADEON(1): RADEONScreenInit d0000000 0 0
(==) RADEON(1): Write-combining range (0xd0000000,0x10000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
disable montype: 1
(==) RADEON(1): Using 24 bit depth buffer
(II) RADEON(1): RADEONInitMemoryMap() : 
(II) RADEON(1):   mem_size         : 0x10000000
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(1): Depth moves disabled by default
(II) RADEON(1): CP in BM mode
(II) RADEON(1): Using 8 MB GART aperture
(II) RADEON(1): Using 1 MB for the ring buffer
(II) RADEON(1): Using 2 MB for vertex/indirect buffers
(II) RADEON(1): Using 5 MB for GART textures
(II) RADEON(1): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(1): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(1): Largest offscreen area available: 1280 x 6989
(II) RADEON(1): Will use front buffer at offset 0x0
(II) RADEON(1): Will use back buffer at offset 0x1838000
(II) RADEON(1): Will use depth buffer at offset 0x1e14000
(II) RADEON(1): Will use 225280 kb for textures at offset 0x23f0000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(1): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(1): [drm] framebuffer handle = 0xd0000000
(II) RADEON(1): [drm] added 1 reserved context for kernel
(II) RADEON(1): X context handle = 0x1
(II) RADEON(1): [drm] installed DRM signal handler
(II) RADEON(1): [pci] 8192 kB allocated with handle 0x00000000
(II) RADEON(1): [pci] ring handle = 0xf9631000
(II) RADEON(1): [pci] Ring mapped at 0x96e8f000
(II) RADEON(1): [pci] Ring contents 0x00000000
(II) RADEON(1): [pci] ring read ptr handle = 0xf9732000
(II) RADEON(1): [pci] Ring read ptr mapped at 0x96e8e000
(II) RADEON(1): [pci] Ring read ptr contents 0x00000000
(II) RADEON(1): [pci] vertex/indirect buffers handle = 0xf9733000
(II) RADEON(1): [pci] Vertex/indirect buffers mapped at 0x96c8e000
(II) RADEON(1): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(1): [pci] GART texture map handle = 0xf9933000
(II) RADEON(1): [pci] GART Texture map mapped at 0x967ae000
(II) RADEON(1): [drm] register handle = 0xfe5f0000
(II) RADEON(1): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0x1fff0000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
disable montype: 1
init memmap
init common
init crtc2
init pll2
freq: 108000000
best_freq: 108000000
best_feedback_div: 96
best_ref_div: 12
best_post_div: 2
restore memmap
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
disable montype: 1
disable montype: 1
(==) RADEON(1): Backing store disabled
(II) RADEON(1): [DRI] installation complete
(II) RADEON(1): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(1): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(1): [drm] dma control initialized, using IRQ 20
(II) RADEON(1): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(1): DRI init changed memory map, adjusting ...
(WW) RADEON(1):   MC_FB_LOCATION  was: 0xdfffd000 is: 0xdfffd000
(WW) RADEON(1):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xffffffc0
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(1): Direct rendering enabled
(II) RADEON(1): Render acceleration enabled
(II) RADEON(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(1): Acceleration enabled
(**) Option "dpms"
(**) RADEON(1): DPMS enabled
(==) RADEON(1): Silken mouse enabled
(II) RADEON(1): Using hardware cursor 0 (scanline 1202)
(II) RADEON(1): Using hardware cursor 1 (scanline 1205)
(II) RADEON(1): Largest offscreen area available: 1280 x 6982
(II) RADEON(1): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Reloading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) RADEON(1): no multimedia table present, disabling Rage Theatre.
(II) RADEON(1): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:04:02.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r200_dri.so
(II) GLX: Initialized DRI GL provider for screen 1
(II) RADEON(0): Setting screen physical size to 338 x 270
(II) RADEON(1): Setting screen physical size to 338 x 270
(WW) mouse1: No Device specified, looking for one...
(II) mouse1: Setting Device option to "/dev/input/mice"
(--) mouse1: Device: "/dev/input/mice"
(==) mouse1: Protocol: "Auto"
(**) Option "CorePointer"
(**) mouse1: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) mouse1: Emulate3Buttons, Emulate3Timeout: 50
(**) mouse1: ZAxisMapping: buttons 4 and 5
(**) mouse1: Buttons: 9
(**) mouse1: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) keyboard1: always reports core events
(**) Option "Protocol" "standard"
(**) keyboard1: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) keyboard1: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) keyboard1: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) keyboard1: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) keyboard1: CustomKeycodes disabled
(II) evaluating device (keyboard1)
(II) XINPUT: Adding extended input device "keyboard1" (type: KEYBOARD)
(II) evaluating device (mouse1)
(II) XINPUT: Adding extended input device "mouse1" (type: MOUSE)
(--) mouse1: PnP-detected protocol: "ExplorerPS/2"
(II) mouse1: ps2EnableDataReporting: succeeded
enable montype: 1
enable montype: 1
enable montype: 1
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0
SetClientVersion: 0 9
SetKbdSettings - type: -1081007156 rate: 30 delay: 500 snumlk: 28
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a023  Serial#: 827209045
(II) RADEON(0): Year: 2006  Week: 29
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: XH59767H1N5U
(II) RADEON(0): Monitor name: DELL E177FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac23a055354e31
(II) RADEON(0): 	1d10010368221b78eeee91a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff00584835
(II) RADEON(0): 	3937363748314e35550a000000fc0044
(II) RADEON(0): 	454c4c204531373746500a20000000fd
(II) RADEON(0): 	00384b1f500e000a20202020202000ae
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "DEL", prod id 40995
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Detected non-DDC Monitor Type: 0

```

---

### Post by CHaoSlayeR on 2009-04-29
Hi jbaird,

I'm glad that you got this far. So now we will see what we can do next. As the radeon driver doesn't seem to apply the randr-style configuration we gave it we will see what xrandr says.

So if you can log in and post the output of **xrandr** it would be very nice. In addition you can try to configure the layout using xrandr.

In addition if I remember correctly the radeon driver is version 6.8.0 in Hardy, so you could just do a **man radeon** to get additional configuration options. It might be possible that you need to specify a **MergedFB** option for the device to get a non-clone layout.

I remember myself struggling alot to prevent the radeon cards from doing clone mode so it might take some time and a lot of trials to get what you want.

If I get the time I will try to set up Hardy again on some free partition at work to get back to my multicard layout I once had. Then I would be able to help you out a lot more than now by just remembering everything.

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-04-29
Just found a sample that might resolve the clone-mode issue: [http://ubuntuforums.org/showthread.php?t=22412&p=181501]("http://ubuntuforums.org/showthread.php?t=22412&p=181501")

---

### Post by jbaird on 2009-05-01
Same results using MergedFB.. xrandr shows only one screen, the dual headed card (VGA/DVI).  I still can't get the mouse to move over to the "main" screen, and the dual headed card has two mirrored/cloned screens.  Still messing around here, but can't really figure out anything else to try.

---

### Post by CHaoSlayeR on 2009-05-03
Hi jbaird,

sorry that I'm late, much family in these days over here. Unfortunately I'm very busy the next weeks at work so I won't have time to set up an additional Hardy there. That means that I'm currently out of answers for your problem. But as all your three monitors are showing at least something it has to work somehow.

Also as I said earlier your output of xrandr would have been nice to have a start for configuring the displays based on randr data because even Hardy uses randr where it can and the driver sure supports it.

C]-[aoZ

---

