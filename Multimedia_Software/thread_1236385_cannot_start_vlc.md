---
title: "cannot start vlc"
date: 2009-08-10
forum: Multimedia Software
---

### Post by ruddyrum on 2009-08-10
so i installed vlc using apt-get and now i cant start it!?

Using the terminal results in the following

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000399] inhibit interface error: Failed to connect to the D-Bus session daemon: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

[00000399] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000405] qt4 interface error: Could not connect to X server
[00000405] skins2 interface error: Cannot open display
[00000405] skins2 interface error: cannot initialize OSFactory
Remote control interface initialized. Type `help' for help.

```No idea what this means so any help is much appreciated!

I also see that i do not have the latest release of vlc... again any help on how to get the latest release would be fantastic!

---

### Post by swong on 2009-08-10
Latest VLC can be found here
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by ruddyrum on 2009-08-10
thanks... but i have added the multiverse repo and apt-get install vlc always downloads this version!

Cant seem to get vlc 1.0.0 to download via PPA! being new, this is a little over my head!

any info on the errors?

---

