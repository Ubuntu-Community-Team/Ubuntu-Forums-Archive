---
title: "Video playback skips"
date: 2008-12-02
forum: Multimedia Software
---

### Post by (-NINJ4-) on 2008-12-02
I've had this problem for a while, and found a workaround for a while, which involved setting the video output to X11 output and then killing compiz.  However, with the most recent updates to compiz, it seems this no longer works.  I would really like to get video playback that doesn't skip in compiz, as video playback is the primary purpose of the PC I have ubuntu installed on presently.  Messing with many other settings seems to have little to no effect on the skipping.  I ran VLC in a terminal, the output is below:

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000396] main interface: creating httpd
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000422] mkv demux error: cannot load some cues/chapters/tags etc. (broken seekhead or file)
[00000458] dts decoder: DTS channels:6 samplerate:48000 bitrate:1536000
Stream with high frequencies VQ coding
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
```
This line about QPainter seems to appear every time the video skips.  Before this updating to Ubuntu 8.10, I never had any video playback issues, even with HD content, and only since the most recent updates to compiz have I had any issues with playback in metacity (as opposed to compiz).  All the other threads that include this line (that I've been able to find) seem to involve a wide variety of issues, but I can't seem to find any that relate directly to video skipping.

Are there any solutions to this?  Video skipping might not bother my roommate, but it's beginning to really grate on me.
Also, since I realize this is a problem that doesn't affect Linux or VLC individually, I'm posting this thread on both the Ubuntu forums and the VLC support forums.  The other thread is here: [http://forum.videolan.org/viewtopic.php?f=13&t=53415](http://forum.videolan.org/viewtopic.php?f=13&t=53415)

---

### Post by (-NINJ4-) on 2008-12-04
Is there any more information I could provide, a general direction for more specific support, maybe?  I'm really at a loss for how to solve this issue and I would greatly appreciate any help you can give me.

---

### Post by brian mcgee on 2008-12-07
Similar trouble here.

Ubuntu 8.10 32-bit
2.6.27-9-generic
VLC media player 0.9.4 Grishenko
Openbox
No GNOME 
No Compiz

Maybe you can confirm this, but the skipping doesn't seem to recur if I manually move the slider to jump to another point in the video, even if I eventually jump back to where I started. **Update**: hmm, this might only be with one video...

Also, the hiccups don't always happen with the same video.

---

### Post by ab5tract on 2008-12-11
This is happening to me too.

Brand new install of 8.10, upgraded as soon as I booted the OS.

I had similar issues with Sabayon 3.5.

Brand new computer, no way it can't handle AVI's _or_ HD x264. The CPU is not spiking, the video is just skipping :/

AMD 780G mobo w/ ATI HD 3200 IGP (Catalyst driver; broken w/o Catalyst driver as well)

Maybe we should try downgrading to previous versions?

[update] @Brian - Skipping ahead doesn't work for me.

---

### Post by (-NINJ4-) on 2008-12-11
There seems to be better results when I run VLC without any other programs that use audio.  It seems like anything, even pidgin noises can steal the audio output and cause VLC to hiccup in video playback.  Even when I had Amarok open but paused, I would get video skips.  On a clean boot, with no programs running except VLC I had significantly less skipping (but it was not entirely solved).

---

### Post by ab5tract on 2008-12-11
I have zero audio related programs running. I was able to reduce the skipping by opening it first thing after a reboot. Still unwatchable though.

Is anyone from Canonical paying attention? The first hit on google should be from their bug reporting system.

---

### Post by Colt45 on 2008-12-26
Let's try to center our efforts in these two threads..

See links below

[http://ubuntuforums.org/showthread.php?t=972696](http://ubuntuforums.org/showthread.php?t=972696)

[http://forum.videolan.org/viewtopic.php?f=13&t=53160](http://forum.videolan.org/viewtopic.php?f=13&t=53160)

---

