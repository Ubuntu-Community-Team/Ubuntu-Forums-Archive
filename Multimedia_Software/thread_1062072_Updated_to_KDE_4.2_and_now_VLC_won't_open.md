---
title: "Updated to KDE 4.2 and now VLC won't open"
date: 2009-02-06
forum: Multimedia Software
---

### Post by jbrown96 on 2009-02-06
I have Kubuntu 8.10 running on an htpc. I added the kubuntu ppa from their website and imported the signing key, and then ran updates. I have kde 4.2 and vlc even worked for a while, but then I ran some more updates later that day or the next, and now VLC won't open. I would really like to get this fixed because it seems to be the only player that works; Dragon player is a disaster and mplayer is bad (FF or RR in a video is awful, and I can't double click to make it full screen???). If I launch it from a terminal, I get all kinds of errors (below) that seem to relate to the QT API.

I've attached the errors below. Any help would be greatly appreciated. 


$ vlc 
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team                                
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'  
[00000001] main libvlc debug: translation test: code is "C"          
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.                                  
WARNING: QApplication was not created in the main() thread.          
QObject::setParent: Cannot set parent, new parent is in a different thread                                                                
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QObject::setParent: Cannot set parent, new parent is in a different thread                                                                
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPainter::begin: Cannot paint on a null pixmap                       
QPainter::end: Painter not active, aborted                           
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPainter::begin: Cannot paint on a null pixmap                       
QPainter::end: Painter not active, aborted                           
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QPixmap: It is not safe to use pixmaps outside the GUI thread        
QObject: Cannot create children for a parent that is in a different thread.                                                               
(Parent is QSignalMapper(0x1491280), parent's thread is QThread(0x148db80), current thread is QThread(0x13d54d0)                          
QObject: Cannot create children for a parent that is in a different thread.                                                               
(Parent is QSignalMapper(0x1491280), parent's thread is QThread(0x148db80), current thread is QThread(0x13d54d0)                          
QObject: Cannot create children for a parent that is in a different thread.                                                               
(Parent is QSignalMapper(0x1491280), parent's thread is QThread(0x148db80), current thread is QThread(0x13d54d0)                          
QObject: Cannot create children for a parent that is in a different thread.                                                               
(Parent is QSignalMapper(0x1491280), parent's thread is QThread(0x148db80), current thread is QThread(0x13d54d0)                          
QObject: Cannot create children for a parent that is in a different thread.
(Parent is QSignalMapper(0x1491280), parent's thread is QThread(0x148db80), current thread is QThread(0x13d54d0)
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QPixmap: It is not safe to use pixmaps outside the GUI thread
QApplication::exec: Must be called from the main thread
Segmentation fault

---

