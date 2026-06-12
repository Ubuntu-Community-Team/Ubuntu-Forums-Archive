---
title: "[SOLVED] Radeon driver, full screen video, mplayer and xvidix - possible??"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by zanadou on 2007-08-06
Been using Ubuntu constantly for a few months now after trying it on a off for a few years.

I have a laptop with a ATI Radeon Mobility 9000/9100 (RS300M). I'm running Fesity Fawn 7.04, which, of course, installed the nice open source radeon drive for me. All is good with that. :)

lspci says:

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]

```

glxinfo says:

```

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
(...)
direct rendering: Yes

```

Anyway, what's ***really*** annoying me now is the fact that the accelerated overlay video output in mplayer and other video apps - system wide - is not working. All I seem to be able to do is get mplayer to play in X11 ( XImage/Shm ) full screen with the software zoom option - which looks like crap, loses sync and overloads my cpu. Without the zoom option, I get just the video at 1:1 resolution with black borders.

So, I'm trying to get the xvidix output on mplayer (at the very least), to work. No luck so far. It's mystifying, as apparently, my system is capable of playing video though VIDIX:

```
$ mplayer -vo help
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Available video output drivers:
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

```

```
$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon Video Overlay"
    number of ports: 1
    port base: 73
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
    number of attributes: 22
      "XV_DEVICE_ID" (range 0 to -1)
              client gettable attribute (current value is 108)
      "XV_LOCATION_ID" (range 0 to -1)
              client gettable attribute (current value is 109)
      "XV_INSTANCE_ID" (range 0 to -1)
              client gettable attribute (current value is 110)
      "XV_DUMP_STATUS" (range 0 to 1)
              client settable attribute
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLORKEY" (range 0 to -1)
              client settable attribute
              client gettable attribute (current value is 30)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_OVERLAY_ALPHA" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 255)
      "XV_GRAPHICS_ALPHA" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 255)
      "XV_ALPHA_MODE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SWITCHCRT" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GAMMA" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_COLORSPACE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 8
      id: 0x41424752 (RGBA)
        guid: 52474241-0000-0010-8000-00aa00389b71
        bits per pixel: 32
        number of planes: 1
        type: RGB (packed)
        depth: 32
        red, green, blue masks: 0xff0000, 0xff00, 0xff
      id: 0x0
        guid: 52474200-0000-0010-8000-00aa00389b71
        bits per pixel: 24
        number of planes: 1
        type: RGB (packed)
        depth: 24
        red, green, blue masks: 0xff0000, 0xff00, 0xff
      id: 0x54424752 (RGBT)
        guid: 52474254-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 16
        red, green, blue masks: 0x7c00, 0x3e0, 0x1f
      id: 0x32424752 (RGB2)
        guid: 52474200-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: RGB (packed)
        depth: 16
        red, green, blue masks: 0xf800, 0x7e0, 0x1f
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)

```

But:

```
$ mplayer -vo xvidix al.wmv
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing al.wmv.
ASF file format detected.
VIDEO:  [MP43]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)

No vidix driver name provided, probing available ones (-v option for details)!
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
Error opening/initializing the selected video_out (-vo) device.


Exiting... (End of file)

```

It's driving me crazy; all of the video players on my system are playing though x11 (XImage/Shm) and software zoom now.

I watch a lot of videos on the net (via mplayer plug-in), and on my system's media apps, and this is a ***real ***show stopper for me - enough to make me want to go back to windows. Hopefully someone can help me get overlay/accelerated video working.

Oh, of course, here's my xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"kr"
	Option		"XkbVariant"	"kr104"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option 		"VideoOverlay" "on"
	Option 		"OpenGLOverlay" "off"
#	Option          "XAANoOffscreenPixmaps"
	Option          "AGPMode"        "4"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	DisplaySize     338 211
	Option		"DPMS"
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

I've been playing around with compiz as you can see. However, the xvidix hasn't been working ever since I installed feisty - a far as I remember.

Also, I downloaded and complied mplayer myself from source to try and fix this problem, but it still happens. Like I wrote, I (think) the other apps on my system (totem et. al.) also output just to basic x11.

Thanks in advance...

---

### Post by zanadou on 2007-08-09
Bump --- anyone?

My question might have been a bit hard to find in all of the above - I just thought I'd jump the gun and post all my logs and output before someone asks me.

:KS **My question is**: How can I get VIDIX/overlay video working on my (the above), system??????

---

### Post by DanPT on 2007-08-13
Hi, I finally figured out why it doesn't work (in my case at lease)

If you go to the MPlayer Doc under vidix

[http://www.mplayerhq.hu/DOCS/HTML/en/vidix.html](http://www.mplayerhq.hu/DOCS/HTML/en/vidix.html)

They say 

> Since VIDIX requires direct hardware access you can either run it as root or set the SUID bit on the MPlayer binary (Warning: This is a security risk!). Alternatively, you can use a special kernel module, like this:[...]

Since I'm such a newb the only  way that I can get it to work is to run: sudo gmplayer (for me mplayer don't have the play/pause control, gmplayer is the command used in the menu so has all the normal control)
Then I can select xvidix in the preference or use the -vo xvidix from the terminal

If you don't run it as root (i.e. the normal way) it will try to detect your video card and failed on

[radeon] Error occurred during pci scan: Operation not permitted
(that the Error I see if gmplayer/mplayer  from the terminal)

It cannot do a hardware scan unless it's root.

Maybe someone else can figured out a better way to start vidix now that they know what the problem is. (I've only been using ubuntu for 3 days previously on winXP so I wouldn't know where to begin;-))

---

### Post by DanPT on 2007-08-20
Hi I made a howto article to solve this problem

[http://ubuntuforums.org/showthread.php?t=528943](http://ubuntuforums.org/showthread.php?t=528943)

---

### Post by zanadou on 2007-08-26
:KS**SOLVED (in my case). Summary of reason: bug in the RC1 version of mplayer.**

Actually, not having root access, wasn't it. I forgot to mention before that even running mplaery under root with sudo *still *didn't give me xv or xvidix output.

But, I finally worked it out. It's due to the most frustrating thing that a user could ever come across; it's because of a bug in mplayer.

What I did was to download and compile the *laterst* subversion version of mplayer. Problem (seemly) solved.

(The following summarised from [here]("http://ubuntuforums.org/showthread.php?t=187709").)

Details; first type/paste this into the terminal:

```
sudo apt-get install build-essential debhelper libx11-dev libxv-dev libpng12-dev checkinstall libavcodec-dev libaa1-dev caca-utils libcaca-dev libavcodec-dev libavifile-0.7-dev libsdl1.2debian-all libsdl1.2-dev libesd0-dev libfaac-dev libfaad2-dev libgtk2.0-dev liblame-dev libice-dev libjpeg62-dev libmatroska-dev libmad0-dev libmpcdec-dev libmp4v2-dev libmikmod2-dev libogg-dev libtheora-dev libvorbis-dev libxinerama-dev libxv-dev xlibs-dev x-dev cvs libquicktime0 libquicktime-dev fakeroot gnome-core-devel libpostproc-dev libx11-dev libxv-dev libavcodec-dev libgtk1.2-dev msttcorefonts nasm subversion
```

Then:

```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd mplayer
```

Then configure this version and install. I used:

```
./configure  --enable-gui --enable-largefiles --enable-menu  --enable-gl --enable-xv --enable-x11
```

...but your mileage may vary; open the configure file yourself in a text editor and have a look at the options. There are **lots** of posts on this forum about how to do this.

Then just compile, install and you're done!

```
make
sudo make install
```

This version of mplayer for me plays in xv and, if I use sudo, plays in xvidix as well. Actually, I noticed that xvidix plays a bit slower for me, and xv works well, so I'm not going to bother installing svgalib.

Thanks all!

---

### Post by Nameless_one on 2007-09-30
This makes me wonder. I had the same problem and after looking around a bit, I found out I didn't have xv support (xvinfo returned "no adaptors present") and after days of googling and reading and stuff, I found that the fglrx driver that came with Edgy didn't have support for xv. But you say you're using the radeon driver. 

After all that, it's a bug in the mplayer code? :-\ What is the bug exactly?

EDIT: Oh, and I noticed on your output, as I did in mine, that mplayer claims it was 'compiled for x86 with...'. I wonder why that is.

---

