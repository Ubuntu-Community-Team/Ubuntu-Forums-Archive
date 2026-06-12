---
title: "[SOLVED] Cannot play videos"
date: 2008-09-27
forum: Multimedia Software
---

### Post by doubad on 2008-09-27
I'm currently running Intrepid Ibex Alpha
I've been quite happy with it, everything is very smooth.
There is, however, one exception and that is video.
This means my .avi and .mp4 files.
I've installed w64codecs and ubuntu-restricted-extras package
I have both of the latest Mplayer and VLC players installed
Either way I get the same result; upon opening the file with either
player, the player opens for a brief second, then closes again.
There are no error messages or anything like that, just open then close.

---

### Post by werries on 2008-09-27
have you opened it with terminal? what does that output?

---

### Post by doubad on 2008-09-27
VLC media player 0.9.2 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.2 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
ALSA lib pcm_pulse.c:696:(pulse_hw_params) PulseAudio: Unsupported format FLOAT_LE

QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

(process:25672): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:25672): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(process:25672): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:25672): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by doubad on 2008-09-27
any ideas?

---

### Post by doubad on 2008-09-28
??

---

### Post by doubad on 2008-09-28
Anyone?

---

### Post by doubad on 2008-09-29
Sweet Jesus this sucks.  It always happens to me.
It seems that everytime I install any version of Linux, I'm riddled with all kinds of unsolvable problems and yet everyone maintains that these OS's  "just work"
Either everyone is outright lying or I'm just one unlucky s.o.b.

---

### Post by gandaran on 2008-09-29
yes, things work and beautifully, and I can say I have never had some kind of problem that people post here, I have tried many linux distros and they all work in my computer.
I think you should start looking into your video and sound card drivers, maybe they are not fully supported yet, for sound you can change things around, pulseaudio, alsa or oss   
check the video settings in VLC, theres a lot you can do there.

install libdvdcss2 if you haven't, and what are those mp4 files, sound files?

---

### Post by Bablefish on 2008-09-29
I have one suggestion [http://en.wikipedia.org/wiki/Automatix_(software](http://en.wikipedia.org/wiki/Automatix_(software))

---

### Post by doubad on 2008-09-30
I spent most of my time trying to figure out what files I  was missing when the whole time I've neglected to check out the media player preferences.
In VLC I simply had to choose X11 as video output and that seems to be working for me.  It was previously set on "default" which I'm not sure what exactly that is.  Thanks for the input.

---

