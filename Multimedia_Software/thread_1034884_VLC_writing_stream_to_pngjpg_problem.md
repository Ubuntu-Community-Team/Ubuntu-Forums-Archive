---
title: "VLC writing stream to png/jpg problem"
date: 2009-01-09
forum: Multimedia Software
---

### Post by jakkuk on 2009-01-09
Hi!

I'm trying to get VLC to write a frame from my v4l video card every second to a png or jpg file. This is my commandline:

```
vlc v4l2:// :v4l2-vdev="/dev/video0" -V image --image-out-format=png --image-out-width=-1 --image-out-height=-1 --image-out-prefix=aaaaaaa --image-out-ratio=25
```

I get the following:

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000399] inhibit interface error: Failed to connect to the D-Bus session daemon: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

[00000399] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000405] qt4 interface error: Could not connect to X server
[00000405] skins2 interface error: Cannot open display
[00000405] skins2 interface error: cannot initialize OSFactory
Remote control interface initialized. Type `help' for help.
[00000499] avcodec encoder error: cannot open encoder
[00000499] main encoder error: no suitable encoder module for fourcc `png '.
VLC probably does not support this image format.
[00000506] avcodec encoder error: cannot open encoder
[00000506] main encoder error: no suitable encoder module for fourcc `png '.
VLC probably does not support this image format.
^C[00000403] signals interface error: Caught Interrupt signal, exiting...
status change: ( new input: v4l2:// )
status change: ( audio volume: 256 )
status change: ( stop state: 0 )
status change: ( quit )

```

Ubuntu 8.10, server edition, all packages installed nicely with apt-get. I guess that there are some dependancies missing. I've got libpng and libsdl-image installed. What info more can i give you all? I've also tried jpg with no luck.

The errors with dbus, X and stuff do not influence the vlc. Only this worries me (happens every second, when the frame writing takes place):

```
[00000506] avcodec encoder error: cannot open encoder
[00000506] main encoder error: no suitable encoder module for fourcc `png '.
VLC probably does not support this image format.
```

The vlc itself works quite ok. This:

```
vlc v4l2:// :v4l2-vdev="/dev/video0" --sout '#transcode{vcodec=mp1v,vb=4096,scale=1}:std{access=mmsh,mux=asfh,dst=:8080}
```

gives me a splendid encoded stream on my network interface...

Regards

---

### Post by jakkuk on 2009-01-09
nvm... i messed up the options.

Regards.

---

