---
title: "VLC, Mplayer, SMPlayer libQtGui.so.4"
date: 2008-11-10
forum: Multimedia Software
---

### Post by DriftShin on 2008-11-10
I recently updated my laptop to Ubuntu 8.10. I then installed the media player and codecs via the 'Add/Remove' option. Now everytime i try to use either VLC, Mplayer or SMplayer, i get more or less the same response; 

VLC: 

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000405] main generic error: no dialogs provider module matched "any"
[00000401] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[00000401] skins2 interface: skin: VLC 0.8.5 Default Skin  author: aLtgLasS
```

Mplayer
```
mplayer: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory
```

SMplayer
```
smplayer: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory
```

I've tried using getlibs
[http://ubuntuforums.org/showthread.php?t=474790&highlight=libQtGui.so.4](http://ubuntuforums.org/showthread.php?t=474790&highlight=libQtGui.so.4) but  nothing seems to help. What is the problem?

---

### Post by rvm4000 on 2008-11-14
I don't know what happened but it seems some libraries are missing.

libQtGui.so.4 is included in the package libqtgui4, while libaudio.so.2 seems to be in the package libaudio2. Try to reinstall those packages.

---

