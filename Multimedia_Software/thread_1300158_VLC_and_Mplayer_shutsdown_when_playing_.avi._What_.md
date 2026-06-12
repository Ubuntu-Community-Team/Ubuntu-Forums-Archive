---
title: "VLC and Mplayer shutsdown when playing .avi. What can be done?"
date: 2009-10-24
forum: Multimedia Software
---

### Post by palm_ on 2009-10-24
Hey, I've been having problems with playing .avi files for quite some time now. I've tested alot of different guides, for example the sticky one in this forum. I've even gotten Ultamatix to try to apply the right codecs, but my .avi files won't play.
I've been trying with both mplayer and VLC. The video plays for like 0.2 sec, then the programs shutdown..

What should i do?

I'm running Ubuntu 9.04

---

### Post by vinutux on 2009-10-25
R u installed ubuntu restricted extras ?
```
sudo apt-get install ubuntu-restricted-extras
```

play it from terminal 

Application > Accessories > Terminal 

vlc [COLOR="Red"]/pathtoyourfile[/COLOR] or drag the file to terminal -
enter

post output here.............

---

### Post by palm_ on 2009-10-25
Okay, so I ran it through the terminal, VLC didn't shutdown, the audio worked but the screen was blue. I get the same results with Gnome Mplayer

william@william-laptop:~$ sudo apt-get install ubuntu-restricted-extrasReading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
william@william-laptop:~$ vlc /home/william/Desktop/heroes.0406.hdtv.xvid-notv.avi
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000404] main interface: creating httpd
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x3e00005

---

### Post by vinutux on 2009-10-25
plz post output of ```
mplayer /[COLOR="Red"]yourfile[/COLOR]
```

and check right click propertes > Audio/video tab infos ...means what video and audio codec is used....

---

### Post by palm_ on 2009-10-25
Properties:
Video codec: ISO MPEG-4 (XviD) (ffmpeg)
Audio Codec MPEG layer 2/3

Terminal:
william@william-laptop:~$ mplayer /home/william/Desktop/heroes.0406.hdtv.xvid-notv.avi
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) M processor          900MHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/william/Desktop/heroes.0406.hdtv.xvid-notv.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1022.6 kbps (124.8 kbyte/s)
Clip info:
 Software: transcode-1.0.2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 112.0 kbit/7.29% (ratio: 14000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation) 4.4% 2 0 
X11 error: BadAlloc (insufficient resources for operation)4.3% 2 0 
X11 error: BadAlloc (insufficient resources for operation)4.2% 2 0 
X11 error: BadAlloc (insufficient resources for operation)4.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)4.0% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.7% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.7% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.7% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.6% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.5% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.5% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.4% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.4% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.3% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.3% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.2% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.2% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.1% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.0% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.0% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.0% 2 0 
X11 error: BadAlloc (insufficient resources for operation)3.0% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.9% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.7% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.7% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.7% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.8% 2 0 
X11 error: BadAlloc (insufficient resources for operation)2.7% 2 0 
(and it goes on like that)

---

### Post by vinutux on 2009-10-25
[I][COLOR="Sienna"]"This usually happens when X doesn't have enough resources to
> allocate to direct viewing with the xv (XView) driver. This
> is very often related to DRM/DRI or memory problems.
> 
> As a work around, try playing the video with the x11 driver
> instead:
> "[/COLOR][/I]
 ```
mplayer -vo x11 somefile.avi
```

In vlc change to other output options in preferences menu....

---

### Post by palm_ on 2009-10-25
Thanks!
It works now!!

---

### Post by vinutux on 2009-10-25
pleasure... plz mark thread SOLVED under thread tools...

---

### Post by krivine on 2009-11-15
Thanks!

---

