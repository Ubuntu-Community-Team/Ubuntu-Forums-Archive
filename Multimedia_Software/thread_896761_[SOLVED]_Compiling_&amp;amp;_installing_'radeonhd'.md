---
title: "[SOLVED] Compiling &amp;amp; installing 'radeonhd' driver on Feisty"
date: 2008-08-21
forum: Multimedia Software
---

### Post by antonr on 2008-08-21
13-Aug-2008
Status: [13-Aug-2008 **Feisty; not working** - black screen. 
	**22-Aug-2008 Gutsy; working** well at my desired resolution.]

This document details my failed attempt to get the open-source 'radeonhd' video driver to work on a Kubuntu 7.04 'Feisty' linux system, and my **success** with it on **Kubuntu 7.10 'Gutsy'** after a **distro upgrade**.

[I couldn't get it to work on Kubuntu 7.04 Feisty, and it's not clear to me that it can, at the moment. I think only the developers of radeonhd could make this happen.]

**Hardware:**
 Graphics card: Asus EAH3450 (RV620 chipset)  (purchased new 21-Jul-2008)
 Motherboard: Asus M3A32-MVP Deluxe  (purchased new 21-Jul-2008)

OS: Kubuntu 7.04 Feisty 32-bit desktop, linux kernel 2.6.20-16-lowlatency

**Background:** 

I am fairly new to linux (< 2 years) and don't have much experience compiling stuff on it. This is my first attempt at compiling and installing a video driver.

What's happened is my old motherboard with 32bit cpu became unreliable, so I bought a new motherboard, cpu, ram, gfx card, and replaced the old ones with them.
I wanted to keep my existing Kubuntu 7.04 installation as it is.
(I've gone to a lot of effort to install and configure software on this base, and I don't enjoy the idea of possible mass breakage by doing a distro upgrade.)
So Kubuntu 7.04 booted up one day recently and found itself with new hardware.
A little bit too new. The splash screen showed its progress bar, but at the end the screen went blank except for a non-responsive flashing cursor. I could switch to virtual terminals for console work, but X refused to start.

After some investigation, I determined that my card wasn't supported by the older 'radeon' driver which comes with Kubuntu 7.04. What I need is the newer 'radeonhd' driver, which is being actively developed from day to day at the moment.
Being actively developed means that easy-to-install packages aren't available yet - I must download the latest source code from the 'git' repository and compile it.

Once I downloaded the source, I began to follow the instructions for compiling, but quickly ran into some errors. I resolved several of these errors by installing missing development packages. I then hacked my way through several compile errors and managed to get the compile to complete. I installed the resulting driver file, but I found when testing it that all I got was a black screen, and the 'usplash' process was consuming 100% cpu.

I'm not yet a master at configuring xorg.conf, so I thought there could be some options there which could get it to work. (I did try several things, eg. disabling DRI.)

Some of the things I did to get it to compile were hacks, and it turned out that these hacks did not really help.


**Diagnosis of the problem:**

The first thing was the blank screen, of course.
Attempting to 'startx' from the console returned with error messages:
"(EE) No devices detected." and "no screens found".
I could find these errors in  /var/log/Xorg.0.log  as well.


I installed xresprobe
	[INDENT]sudo apt-get install xresprobe[/INDENT]
in order to
	[INDENT]sudo ddcprobe[/INDENT]
which told me which chipset the graphics card has (RV620), but failed to read EDID.

At this point, I determined, after lots of reading, that the chipset (RV620) was not supported by the old 'radeon' driver, but that support for it had recently been added to the 'radeonhd', currently in development. [2][3][4][5]

[5] Says we can get the latest source using 'git' (a repository manager), which I installed:

	[INDENT]sudo apt-get install git-core[/INDENT]

and to actually download the source:

	[INDENT]git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-radeonhd
[/INDENT]
which creates a directory named 'xf86-video-radeonhd'.


**Good stuff I've done to prepare for compilation:**

	[INDENT]cd xf86-video-radeonhd[/INDENT]

  Install packages:
    To avoid the error: "./autogen.sh: 9: autoreconf: not found", I installed autoconf:
	[INDENT]sudo apt-get install autoconf[/INDENT]
    To avoid other errors:
	[INDENT]sudo apt-get install automake
	sudo apt-get install libtool
	sudo apt-get install pciutils-dev
	sudo apt-get install libdrm-dev[/INDENT]
    One of these gave me the necessary /usr/include/GL/gl.h file:
	[INDENT]sudo apt-get install libglu1-xorg libgl1-mesa-dev mesa-swx11-source[/INDENT]
    Other packages (not sure if they helped):
	[INDENT]sudo apt-get install xorg-dev
	sudo apt-get install render-dev x-dev libxcb1 libxcb1-dev libxcb-glx0-dev[/INDENT]


**Hacks:**

[These are hacks because I mixed source files from Gutsy (the release after Feisty) into Feisty, without any understanding of how compatible they are. They're probably not compatible in several ways, and so I'm not surprised that the driver couldn't open a screen after this.]

  In order to compile, I got some files from Gutsy (I couldn't find them in any dev package in Feisty):

	[INDENT]wget [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xorg-server_1.3.0.0.dfsg.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xorg-server_1.3.0.0.dfsg.orig.tar.gz)
	tar xvf xorg-server_1.3.0.0.dfsg.orig.tar.gz
	cd xorg-server_1.3.0.0/[/INDENT]

    then I copied all these header files into /usr/include/xorg/

	[INDENT]hw/xfree86/modes/xf86Crtc.h 
	hw/xfree86/modes/xf86Modes.h 
	hw/xfree86/modes/xf86RandR12.h 
	hw/xfree86/modes/xf86Rename.h 
	hw/xfree86/parser/xf86Parser.h 
	hw/xfree86/parser/xf86Optrec.h 
	randr/randrstr.h [/INDENT]


**Compiling:**

    Overview:
	[INDENT]./autogen.sh
	make
	make install[/INDENT]

    Actually, it was necessary for me to specify some options:

	[INDENT]./autogen.sh --libdir=/usr/lib --prefix=/usr[/INDENT]

     (If you are on a 64bit version of Kubuntu, then probably you need:
	[INDENT]./autogen.sh --libdir=/usr/lib64 --prefix=/usr[/INDENT]
     )

    (and I captured the output between compiles, for comparison)

	[INDENT]make ../make-output 2>&1
	make install[/INDENT]

    and see fresh new file  /usr/lib/xorg/modules/drivers/radeonhd_drv.so
    So the radeonhd driver appears to have been installed on my system.


**Testing:**

This is what's necessary to do after 'make install' and the .so driver file
is created:
    Try start X without xorg.conf.
      Remove/rename any existing /etc/X11/xorg.conf file.
      Start X:
	[INDENT]sudo X -logverbose 7[/INDENT]
  If that doesn't work,
    Generate an xorg.conf file (xorg.conf.new will be created in your home directory).
    	[INDENT]sudo Xorg -configure[/INDENT]
     Now either copy that generated file to /etc/X11/xorg.conf (and then start X),
    or 
     test in place with:
	[INDENT]sudo Xorg -config xorg.conf.new[/INDENT]

  but first, examine  /etc/X11/xorg.conf  and ensure that the driver is set to
"radeonhd" in the "Device" section, eg:

	[INDENT]Section "Device"

		[INDENT]Driver "radeonhd"[/INDENT]

	EndSection[/INDENT]

    Stop the K Desktop Manager (if it is running):

	[INDENT]sudo /etc/init.d/kdm stop
[/INDENT]
    now try to start X:

	[INDENT]startx[/INDENT]

    or, recommended by a lead developer:

	[INDENT]sudo X -logverbose 7[/INDENT]

    which gives more output in the  /var/log/Xorg.0.log  file.


...and here is where it didn't work for me.
I just got a black screen. Not even a flashing cursor, and switching VT did not give me text mode either. The machine still responded because I could log in, using ssh, from another machine.

**Feisty and 'radeonhd' not compatible?:**

It appears to me that the current (as of 9-Aug-2008) version of 'radeonhd' video driver is not compatible with Kubuntu Feisty 7.04, which comes with an older version of X.
While the developers wrote that it "should" build and work against older versions of X [6], and "it was one of the design goals" [7], it appears that is not true, at least not yet.
The radeonhd driver requires source files which are not present in the older version of Xorg found in Feisty.
(Here's where I *might* have fallen down, too - I did not do a 100% comprehensive search of Feisty packages looking for those files, as I don't yet know how to do that efficiently. However, I tried probably all the likely-looking 'dev' packages I could find using 'apt-cache search'.)

**Conclusion:**

If I've done everything roughly correctly, then I've shown that if you're on Feisty, like me, then it's a bag of worms to try to compile the radeonhd driver properly.

**The distro upgrade:**

I was advised to update to a newer stable release of Xorg server.
However, I couldn't determine with confidence if Kubuntu 7.04 would react well to that. I read someone's report that when they tried this, the dependencies kept spreading so they ended up doing a distro upgrade anyway.
I thought I'd do things more by the book and do a Kubuntu distro upgrade.

After a distro upgrade from 7.04 Feisty to 7.10 Gutsy (a fairly lengthy process,
taking some hours), the graphics card was successfully utilised by default, able to bring up the desktop (in a low resolution), without even compiling the driver, so that was encouraging.
The radeonhd driver also compiled and installed ok.

Only some lower-end resolutions were available.
The Xorg.0.log had "hsync/vrefresh out of range" errors.

	[INDENT](WW) RADEONHD(0): Connector "VGA 1": Failed to retrieve Monitor information.
	(II) RADEONHD(0): No monitors autodetected; attempting to work around this.
	(II) RADEONHD(0): Created monitor from config: "Monitor0":
		[INDENT]Bandwidth: 0MHz
		Horizontal timing:
		    31.5 - 31.5kHz
		    35.2 - 35.2kHz
		    35.5 - 35.5kHz
		Vertical timing:
		    50.0 - 61.0Hz
		DPI: 0x0
		...[/INDENT][/INDENT]

Those values looked quite wrong to me. I have studied my monitor previously, and I got timings and modes for it when using a previous gfx card.
I merged in a detailed Monitor section containing lots of modelines to my xorg.conf, and I got the 1152x864 mode that I wanted - *success!* The KDE desktop opens. **HOORAY!!!!**

There is a message during boot up:
	[INDENT]Starting up...
	[    0.680000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0[/INDENT]
this does not seem to affect anything though..

21-Aug-2008
There seems also to be an issue sometimes where the monitor modes I specified seem to be attached to the wrong connector by the driver, and so I get a basic, default mode used instead of my desired mode. This only happened once so far, and was ok after the next boot. There is an "ignoreconnector" option in xorg.conf's device section, but I haven't tried it yet.

Another issue is garbage characters when switching to a virtual terminal (VT). Most characters are ok, but it looks like the space char is composed of random pixels.


**Recommendations:**

Therefore, if you are on Feisty and wish to compile the 'radeonhd' video driver, I recommend to first do a distro upgrade to Gutsy.


----------------------------------
**References:**

[http://www.radeonhd.org/?page=archive_listings&m=8&y=2008](http://www.radeonhd.org/?page=archive_listings&m=8&y=2008)
    Phoronix IRC logs. The 'phoronix' website has IRC logs in which the radeonhd
    driver developers participate regularly.

[http://users.erols.com/chare/video.htm](http://users.erols.com/chare/video.htm)
    This site pretty comprehensively lists chipsets and associated graphics card model names.
    Very useful.

[2] [http://dri.freedesktop.org/wiki/Status](http://dri.freedesktop.org/wiki/Status)
[3] [http://dri.freedesktop.org/wiki/AMD?action=show&redirect=ATI](http://dri.freedesktop.org/wiki/AMD?action=show&redirect=ATI)
[4] [http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-radeonhd](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-radeonhd)
[5] [http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)
    I found mentions here of work done for the RV620 chipset.

[6] [http://www.radeonhd.org/?page=archive_display&c=radeonhd&m=8&y=2008&d=2008-8-04](http://www.radeonhd.org/?page=archive_display&c=radeonhd&m=8&y=2008&d=2008-8-04)
    Excerpt:
	libvde: you don't need a hot new version of X
	libvde: our driver should build and work against many X versions, apart from some typing issues recently
[7] [http://www.radeonhd.org/?page=archive_display&c=radeonhd&m=8&y=2008&d=2008-8-13](http://www.radeonhd.org/?page=archive_display&c=radeonhd&m=8&y=2008&d=2008-8-13)
    Excerpt:
	yangman: radeonhd is meant to work with fairly old versions of Xorg ... it was one of the design goals

More interesting pages to explore:

[http://wiki.x.org/wiki/radeonhd%3Apackages](http://wiki.x.org/wiki/radeonhd%3Apackages)
[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd](https://launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd)

---

### Post by clarknova on 2008-09-12
According to [_phoronix_]("http://www.phoronix.com/scan.php?page=article&item=843&num=1"), radeonhd only works with xserver 1.3 and newer, while Feisty uses 1.2.

Good job upgrading and making it work.

db

---

