---
title: "the invisible vlc.. issues with the skins and gridlock"
date: 2008-11-04
forum: Multimedia Software
---

### Post by algunos on 2008-11-04
Hi guys

I'm running ubuntu 8.10 since this weekend, but i'm a unix noob. i approach it by learning.
the version of vlc that was upgraded (with the upgrade to intrepid) is 0.9.4-1ubuntu3 (intrepid)

yesterday I tried loading in the /etc/share/vlc/skins2 directory the skins files available in the vlc website. Everything went well for a couple of them until I loaded the "Presume" skin. :confused:

When I tried to load vlc I got this error:

> File reading failed: VLC could not open the file "/tmp/vltDR9Sdu/img\playlistWindow.png".



that msg seems to change everytime I try to run vlc. Vlc actually starts, I can see it in the side panel, it plays files, it even plays video BUT there is no graphic interface at all and I dont know how to get to the setting to asx it to choose another skin or just the default one. I tried deleting the skins from the directory but didnt work.

When I run vlc from the command konsole I get this lot: 

```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000406] skins2 interface: skin: Presume author: Tobias Englund
[00000419] access_directory access error: /tmp/vlteu1c7b/img\mainWindow.png: No such file or directory
[00000419] access_file access error: cannot open file /tmp/vlteu1c7b/img\mainWindow.png (No such file or directory)
[00000406] main interface error: no suitable access module for `/tmp/vlteu1c7b/img\mainWindow.png'
[00000422] access_directory access error: /tmp/vlteu1c7b/img\playlistWindow.png: No such file or directory
[00000422] access_file access error: cannot open file /tmp/vlteu1c7b/img\playlistWindow.png (No such file or directory)
[00000406] main interface error: no suitable access module for `/tmp/vlteu1c7b/img\playlistWindow.png'
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: mainWindow
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: playlistWindowImage
[00000406] skins2 interface error: unknown bitmap id: controlPrev1
[00000406] skins2 interface error: unknown bitmap id: controlSlow1
[00000406] skins2 interface error: unknown bitmap id: controlPlay1
[00000406] skins2 interface error: unknown bitmap id: controlPause1
[00000406] skins2 interface error: unknown bitmap id: controlFast1
[00000406] skins2 interface error: unknown bitmap id: controlNext1
[00000406] skins2 interface error: unknown bitmap id: controlClose1
[00000406] skins2 interface error: unknown bitmap id: controlMinimize1
[00000406] skins2 interface error: unknown bitmap id: controlSettings1
[00000406] skins2 interface error: unknown bitmap id: controlOpen1
[00000406] skins2 interface error: unknown bitmap id: controlMute
[00000406] skins2 interface error: unknown bitmap id: controlMute2
[00000406] skins2 interface error: unknown bitmap id: pcontrolClose1
[00000406] skins2 interface error: unknown bitmap id: pcontrolAdd1
[00000406] skins2 interface error: unknown bitmap id: pcontrolRemove1
[00000406] skins2 interface error: unknown bitmap id: pcontrolABC1
[00000406] skins2 interface error: unknown bitmap id: controlPlaylist1
[00000406] skins2 interface error: unknown bitmap id: pcontrolReplay1
[00000406] skins2 interface error: unknown bitmap id: pcontrolReplayOne1
[00000406] skins2 interface error: unknown bitmap id: pcontrolShuffle1
[00000406] skins2 interface error: unknown bitmap id: topLeft
[00000406] skins2 interface error: unknown bitmap id: topCenter
[00000406] skins2 interface error: unknown bitmap id: topRight
[00000406] skins2 interface error: unknown bitmap id: bottomLeft
[00000406] skins2 interface error: unknown bitmap id: bottomCenter
[00000406] skins2 interface error: unknown bitmap id: bottomRight
[00000406] skins2 interface error: unknown bitmap id: frameLeft
[00000406] skins2 interface error: unknown bitmap id: frameRight
[00000406] skins2 interface error: unknown bitmap id: resizeSE
[00000406] skins2 interface error: unknown bitmap id: ptopLeft
[00000406] skins2 interface error: unknown bitmap id: ptopRight
[00000406] skins2 interface error: unknown bitmap id: ptopCenter
[00000406] skins2 interface error: unknown bitmap id: pframeLeft
[00000406] skins2 interface error: unknown bitmap id: pbottomLeft
[00000406] skins2 interface error: unknown bitmap id: pbottomRight
[00000406] skins2 interface error: unknown bitmap id: pbottomCenter
[00000406] skins2 interface error: unknown bitmap id: pframeRight
[00000406] skins2 interface error: unknown bitmap id: presizeSE
[00000406] skins2 interface error: unknown font id: Liberation
[00000406] skins2 interface error: unknown font id: Liberation
[00000406] skins2 interface error: unknown font id: Liberation
[00000406] skins2 interface error: unknown font id: Liberation
[00000406] skins2 interface error: unknown bitmap id: sliderProgress
[00000406] skins2 interface error: unknown bitmap id: sliderVolumeBackground
[00000406] skins2 interface error: unknown bitmap id: pslider
[00000406] skins2 interface error: unknown font id: Liberation
: Fatal IO error: client killed
Segmentation fault
```

I aslo tried to remove and install vlc again, no results...

I would really appreciate any help. :?: Thanks in advance!

---

### Post by mc4man on 2008-11-04
If you want to return vlc to it's orig. settings then go into home folder -> .config and delete the vlc folder inside. (.config is a hidden folder

I'd be careful applying skins with the 0.9.x versions of vlc

---

