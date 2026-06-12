---
title: "1080 Videos don't play past half the movie"
date: 2009-03-02
forum: Multimedia Software
---

### Post by houseonfire on 2009-03-02
Every time I try to watch a 1080 quality video on VLC it does not play past the halfway mark of the movie. I've tried two different movies (Changeling and Step Brothers) and it just doesn't do it for me.
Although GNOME Player does play for me past half way, and it is a good player. I just like VLC a little more. Any solutions?

---

### Post by kutsyy on 2009-03-09
I've the same problem :(
From console:
~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000459] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
 m_el[mi_level] == NULL
[00000419] mkv demux error: This file has no cues, and we were unable to seek to the requested position by parsing.
 m_el[mi_level] == NULL
[00000419] mkv demux error: This file has no cues, and we were unable to seek to the requested position by parsing.
 m_el[mi_level] == NULL
[00000419] mkv demux error: This file has no cues, and we were unable to seek to the requested position by parsing.
 m_el[mi_level] == NULL

---

### Post by binbash on 2009-03-09
did you try svn build of x264? I am using gnome-mplayer + mplayer svn + x264 svn builds and 1080p works perfect at me

---

### Post by FakeOutdoorsman on 2009-03-09
Maybe your hardware isn't capable of playing such large and CPU intensive videos (assuming H.264 video streams).  Also, x264 is a video encoder and isn't used to decode video.

---

