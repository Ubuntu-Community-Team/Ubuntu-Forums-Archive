---
title: "Mplayer problem"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by diskace on 2007-09-26
Hi, i installed mplayer, mozilla-mplayer and w32codecs and evetyhing seems to be fine when i run mplayer from /usr/bin/mplayer

The videos play, sounds work but i don't have the task/progression bar. When i try to run the same video file via gmplayer or gmplayer2 (symbolic link to mplayer) i get this error:

```

/usr/bin/gmplayer 1.avi

MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Playing /home/fixit/InvoiceNet40/1.avi.
AVI file format detected.
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  699.7 kbps (85.4 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
open: Aucun fichier ou répertoire de ce type
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)


```

Error opening/initilizing the selected video_out (-vo) device


But when i run if from the shell with mplayer directly i get this:

```

/usr/bin/mplayer 1.avi
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 1.avi.
AVI file format detected.
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  699.7 kbps (85.4 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [x11] 624x352 => 624x352 Planar YV12
SwScaler: using unscaled yuv420p -> rgb32 special converter
A:  17.5 V:  17.6 A-V: -0.017 ct: -0.001 422/422 10% 57%  3.6% 31 0
Exiting... (Quit)

```

I tryed running gmplayer -vo with different option but i can't make it work. Only mplayer and mplayer don't have any status bar just the movie window...

Thanks for helping.

---

### Post by pay on 2007-09-26
I normally change it to the x11 driver and then it works. You can edit .mplayer in your home folder so then it always uses this driver.

---

### Post by diskace on 2007-09-26
vo=x11
ao=oss


Thats what it is...

---

### Post by dyackal on 2007-09-26
is there a way to install the multimedia packages or to play my mp3 and .avi movies and my dvd player, VCD player with out internet?.. i mean install some packages fro ubuntu 7.04. I been tryin to install it manually but.. i get error like dipendency and stuff... is there a web site to download the mutimedia packages all in one package..    .deb os just double click it then install?.... need some reply on this is it that damm hard to install codecs and files and stuff? on ubuntu 7.04 this is my first linux...... post some replys pls...

you can email me @ [email]dyackal@gmail.com[/email] -----> ty

---

### Post by pay on 2007-09-26
@dyackal
This guide explains how to install codecs and other things [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

@diskace
maybe experiment with different drivers to see what works
> **Supported Video Output Devices**

  **general:**

 [LIST]
[*]*x11:* X11 with SHM extension
[*]*xv:* X11 using overlays with the Xvideo extension (hardware YUV & scaling)
[*]*xvmc:* Xvideo Motion Compensation
[*]*vidix:* VIDeo Interface for *niX
[*]*xvidix:* VIDIX in an X11 window
[*]*cvidix:* VIDIX on the console
[*]*winvidix:* VIDIX under Windows
[*]*dga:* X11 DGA extension (both v1.0 and v2.0)
[*]*gl:* OpenGL renderer
[*]*gl2:* alternative OpenGL renderer (with multiple textures)
[*]*fbdev:* framebuffer output
[*]*svga:* SVGAlib output (supports EGA displays)
[*]*sdl:* SDL >= v1.1.7 driver
[*]*ggi:* [GGI]("http://ggi-project.org/") graphics output
[*]*aalib:* text mode rendering
[*]*caca:* text mode rendering in color
[*]*vesa:* display through the VESA BIOS (also needed for Radeon TV-out)
[*]*directfb:* DirectFB support
[*]*directx:* native Windows DirectX output driver
[*]*quartz:* native Mac OS X output driver[/LIST]  **card specific:**

 [LIST]
[*]*mga:* Matrox G200/G400/G450/G550 hardware YUV overlay via the 		mga_vid device
[*]*xmga:* Matrox G200/G400/G450/G550 overlay (mga_vid) in X11 window 		(Xv emulation on X 3.3.x!)
[*]*syncfb:* Matrox G400 YUV support on framebuffer
[*]*3dfx:* Voodoo 3/Banshee hardware YUV support (/dev/3dfx)
[*]*tdfxfb:* Voodoo 3/Banshee hardware YUV support on tdfx framebuffer
[*]*mpegpes:* support for Siemens DVB hardware MPEG-1/2 decoder 		boards (or MPEG-PES file output)
[*]*dxr2:* support for DXR2 hardware MPEG-1/2 decoder boards
[*]*dxr3:* support for DXR3/Hollywood+ hardware MPEG-1/2 decoder boards
[*]*zr:* support for Zoran360[56]7 based hardware MJPEG cards[/LIST]

---

### Post by andrew.46 on 2007-09-28
Hi,

 Glad you worked it out:

> **diskace said:**
> vo=x11
ao=oss
Thats what it is...

 You are obviously using the repository version which limits your choices a little but to see your available -vo and -ao try running these commands:

```
mplayer -vo help
```
```
mplayer -ao help
```

 If you ever compile your own you will get rid of those crazy remote control and joystick warnings :-)

            Andrew

---

### Post by shirilover on 2007-09-28
To change the video output device in gmplayer, run gmplayer without a file(assumes you have a skin).
Right-click on the skin and select Preferences.
Click on the Video tab.
Choose the output device from the list, I use xv (X11,Xv).
You may need to close and re-open gmplayer.

---

