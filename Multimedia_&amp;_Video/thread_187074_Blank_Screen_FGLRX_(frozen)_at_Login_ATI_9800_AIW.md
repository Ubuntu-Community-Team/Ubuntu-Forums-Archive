---
title: "Blank Screen FGLRX (frozen) at Login: ATI 9800 AIW"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2006-06-02
Hello All,

Seems we're swimming in threads about ATI problems.  I feel I have made the rounds through the vast majority of them to no avail.  I believe I have fglrx drivers installed properly and I believe that dri is loading correctly but after the splash screen, and before logging in my screen goes blank.  The computer seems frozen, CTRL-ALT-F1 and CTRL-ALT-BCKSPC do nothing.  I end up resetting the computer and booting in recovery mode, changing xorg.conf by hand to either "ati" or "vesa" to get back into X.  This is the end of the log file from a "frozen" boot:
> drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb71ef000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.25.18
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-23-k7
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): [agp] Mode=0x1f000a1a bridge: 0x1106/0x3188
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000b1a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xf0000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): front overlay:  0xe10a7000
(II) fglrx(0): back overlay:   0xe12b4000
(II) fglrx(0): video overlay:  0xe14c1000
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x00954000
(EE) fglrx(0): === [R200DALGetControllerInfo] === CWDDC ControllerGetConfig failed: 6
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,1528)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete

Does it look like fglrx and dri are loading properly?  Is there a way to prevent my login screen from freezing?

Thanks for your help!

---

### Post by Syirrus on 2006-06-02
I'm having the same problem

---

### Post by aniceyoungman on 2006-06-02
You guys are way ahead of me...

I just tried a fresh install (I had 5.10 installed on this very machine with NO issues).  Using an ATI 8500DV gfx card.  Install went great, then I try to boot and half way through the LCD just turns off and nothing happens.  This goes on every time I try to boot!  What's up?  The live cd (pre-install) worked perfectly.  I'm so confused...

J.

---

### Post by barney_1 on 2006-06-02
So I thought maybe a clean install would fix my problem.  I downloaded and burned the install CD, booted to it, chose install and guess what?  After the splash, the monitor went black and teh install was frozen.

I have seen a bug report for this, guess there's no work-around for it available.  I'll just have to sit on my hands and hope that a patch is developed for it.  Sigh.... that will teach me to buy ATI products.  They just lost another customer.

---

### Post by almahtar on 2006-06-03
I've been getting the same thing.  I've found several ways to work with the fglrx drivers in Breezy and in Dapper Betas to get 3D working, but none seem to work with Dapper official.  The best advice I can give right now is to use the "Option" "nodri" setting within the "device" section of your ATI card in xorg.conf.  At least you'll get 2D accel (and thus a nice responsive desktop) for the time being.

An actual solution is on the way.  Just takes patience and a bit of experimentation.

---

### Post by bjtuna on 2006-06-03
Yeah I'm pretty much getting the same thing.  'ati' driver works though.  I'll post if I find a solution though.

hey guys, check your dmesg|grep fglrx ... are you getting a message about the fglrx module tainting the kernel, but it loads anyway?

---

### Post by barney_1 on 2006-06-03
Agreed, the drivers will run with:
```
Option         "nodri"
```
in the xorg.conf.  I had discovered this before but since my goal is to enable 3d acceleration this didn't solve my problem.

To answer your question, yes i get the message about kernel taint (hehe):
```
[4294685.488000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies , Starnberg, GERMANY' taints kernel.
[4294685.489000] [fglrx] Maximum main memory to use for locked dma buffers: 927 MBytes.
[4294685.489000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0

```

So anyway, I've seen some stuff around the internet that says ATI driver version 8.26 will be out in June.  Let's hope ATI fixes this problem.  If not, feel free to by my ATI card on ebay. :)

---

### Post by AntX on 2006-08-07
I get a similar problem here.

Here are my system specs:

AMD Athlon 64 3200+ (Venice core) on socket 754.
MSI K8N Neo3-FSR board (nVidia nForce 4-4X)
ATI Radeon 9800 Pro 128M AGP8x (R350 Chip)

Kernel version is 2.6.15-26-386
fglrx xorg driver version is 8.25.18 (from dapper repositories)
fglrx kernel module matches (from restricted-modules)

Issue:

DRI hangs the system as soon as a 3D app is launched, or just plain randomly while working on the desktop. Mouse and keyboard are unreponsive, but I don't know about remote pings. It seems like the system is completely frozen, but I might be wrong.

Tried updating the drivers to 8.27.10 (bleeding edge version from ATI), didnt help.

DRI does seem to load, (glxinfo | grep render shows ATI) but it hangs as soon as OpenGL kicks in. (Games like ET, glxgears, etc)

Disabling DRI with "nodri" or "NoAccel" fixes the problem, but creates another: OpenGL doesnt work.

Is that a fglrx bug? kernel bug? drm? xorg? dri?

Heck, I'm no hacker, but I know it worked with the same card 2 years ago on other ditributions. What's the problem?

PS: Anyways, I can confirm that the latest ATI driver DOESNT FIX the issue.

---

### Post by barney_1 on 2006-08-09
I don't know if the problem is ATI or Ubuntu but I have also upgraded to 8.27.10 and no dice.  Sure would be nice to get this fixed and not have to buy new hardware.

Guess I'll just keep waiting for the magic update that fixes it.

---

### Post by barney_1 on 2006-08-21
Well, 8.28.8 has been released.  I have installed the update and still have a Blank Screen at login.

*sigh*

---

### Post by greg.smith.to on 2006-09-08
I have: 
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

This is in an AMD64 system, FT20 mobo (shuttle PC).

Well, most folks at least have something with the standard ATI driver.
Mine works for small resolutions only. I originally installed with a 1Kx768 monitor, no trouble. I later hooked up a DVI 1680x1050 monitor, ran dpkg-reconfigure xserver-xorg to enable this output mode. Everything seemed to go fine, but when I actually restarted the X server, the picture is all scrambled (long horizontal orange streaks, like the memory pitch is wrong or something) but the cursors looked great, so I know the actual video format is fine for the monitor. So, after poking around here, I installed the fglrx driver, hoping that would help, and it (a) has no improvement on the 1680x1050 output (b) actually KILLS the text consoles (I get a blank white screen on alt-ctrl-F1 etc-- how obnoxious is that ?? ), so in order just to switch back to the old xconf I had to boot the CD and use the text console there. grr. Any idea what this is? the monitor must be locking properly (or the cursors would be shredded too). If I had not happened to use that little KDS monitor for the install, I would not have been able to do the installation in the first place, the 1680x1050 output mode is auto-detected from the Viewsonic monitor but ATI driver does not work for that format.

I also tried killing off the two highest [*] boxes in the format list when running dpkg-reconfigure, (can't recall what the next highest format was) and the result was the same but different - same problem, a different look in the corrupted image - short orange lines on black instead of long orange lines on white.

It looks like this is going to be an XP-only machine rather than the dual-boot I was hoping to do...

---

### Post by ShinjiLeery on 2006-09-09
From what i read It's the same problem i have with the DVI connection. Watch here: [http://ati.cchtml.com/show_bug.cgi?id=491]("http://ati.cchtml.com/show_bug.cgi?id=491")

---

### Post by greg.smith.to on 2006-09-09
Guess what? the Win XP drivers (both the ones that came with the mobo and the 'fresh' catalyt drivers from ATI?) same problem!!
grr...  more detailed ranting here: [http://www.ubuntuforums.org/showthread.php?t=254300](http://www.ubuntuforums.org/showthread.php?t=254300)

---

### Post by greg.smith.to on 2006-09-09
Made some progress - if I select 16-bit mode, I get all modes up to   1680x1050! there's still some problem tho - screensavers are weird (aquarium has vertical black stripes, and GL pipes goes black and hangs machine). I'm still working with WinXP here - sorry if that's totally off-topic, but based on recent work I think I have a mobo issue; if I fix the XP setup the same fix will probably work for ubuntu too. Recap, this is Radeon XPRESS 200 integrated into shuttle FT20 mobo, AMD64 X2, Viewsonic monitor 1680x1050; modes above 1024x768 have scrambled output.

Doing a bit of math, it seems I may have a problem whenever the video frame buffer exceeds 4M bytes.

---

### Post by greg.smith.to on 2006-09-11
Got it working - I updated the BIOS to ft20s01e.bin (from shuttle web site) - a process involving several obsolete things, like a floppy drive, and a bootable dos disk. The bios doesn't seem to show its version on startup, so I wasn't even sure it would be different from what was already there, but it's definitely newer than what the unit arrived with.

All of the video seems to be fine now in XP - have 1680x1050 32-bit running, and all the 3d stuff seems to be working properly.

Next step, I need to figure out how to boot that ubuntu partition which was forced underground by the XP install. But I have reason to hope the video will be fine now.

Bottom line: got a shuttle ST20G5? upgrade the BIOS, esp if you have any trouble with video > 1Kx768

---

