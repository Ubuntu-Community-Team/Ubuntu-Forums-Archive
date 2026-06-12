---
title: "No video only audio."
date: 2008-10-31
forum: Multimedia Software
---

### Post by onlyliberty on 2008-10-31
I just installed Kubuntu 8.10 (64 bit) final and I am trying to get everything working.  I installed VLC and gstreamer codecs but when i try to open a divx or xvid avi video the VLC program closes.  When i try Dragon or Kaffeine only audio is playing but no video.  Does anyone have any answers?

---

### Post by gandaran on 2008-10-31
try running VLC from the terminal and post the errors here
you do have the gstreamer plugin installed for divx or xvid play?

---

### Post by onlyliberty on 2008-10-31
LC media player 0.9.4 Grishenko                                                
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team                                                      
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac''--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype''--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::setClipRegion: Painter not active
QPainter::setClipping: Painter not active, state will be reset by begin
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::setClipRegion: Painter not active
QPainter::setClipping: Painter not active, state will be reset by begin
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83

Here is what happened

---

### Post by gandaran on 2008-10-31
try changing the video driver to xv or any other in vlc preferences, maybe it'll work|

---

### Post by onlyliberty on 2008-10-31
Thank You!  I got it working using the X11 output module in video preferences.

---

### Post by lexen on 2008-11-01
So how did you fix it?  I have the same problem, so could you walk me through it in lamends terms?



Thanks,
Lexen

---

### Post by Maqz447 on 2008-11-01
> **lexen said:**
> So how did you fix it?  I have the same problem, so could you walk me through it in lamends terms?



Thanks,
Lexen
Follow the instructions in this link:

[http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html)

The problem is related to compiz. After a fresh install of intrepid RC I couldn't play any video at all unless I turned off desktop effects. The instructions in the above link fixed it. Beware if you've got an older/slower machine though, you might get reduced performance as you're effectively turning off 2D acceleration by the GPU, leaving it to the CPU instead. However, I have a C2D 1.86 MHz and haven't noticed anything.

---

