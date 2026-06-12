---
title: "Power DVD for ubuntu?"
date: 2009-01-19
forum: Multimedia Software
---

### Post by diwas on 2009-01-19
Well it has often occurred to me that a dvd won't play in any of the dvd playing software other than Power DVD. For instance yesterday I was about to watch a korean movie in ubuntu, but the dvd won't mount. No matter how much i try, it wont mount. Then i boot up Windows and insert the dvd and with Power DVD the movie played just fine. This is not the first time I was having such type of problem. 

So I would like to know, if there is Power DVD available for ubuntu or there's any equivalent software for that? 

Thank you.

---

### Post by stefangr1 on 2009-01-19
Even if you can't successfully mount a dvd, you can usually use vlc and mplayer directly to play the disk. From the command line you can do:

vlc dvd://
mplayer dvd://

---

### Post by mdewet on 2009-01-19
The vlc option also worked for me, but I saw this article :

[http://www.dvd-recordable.org/Article1087.phtml](http://www.dvd-recordable.org/Article1087.phtml)

so a few clicks and googles should point you to PowerDVD-linux

Edit: It is available from the canonical online store

[http://shop.canonical.com/product_info.php?products_id=243](http://shop.canonical.com/product_info.php?products_id=243)

---

### Post by diwas on 2009-01-19
> **stefangr1 said:**
> Even if you can't successfully mount a dvd, you can usually use vlc and mplayer directly to play the disk. From the command line you can do:

vlc dvd://
mplayer dvd://

Well even with these commands it won't work:

```

diwas@diwas-desktop:~$ vlc dvd://
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: vm: failed to open/read the DVD
[00000409] dvdread demux error: DVDRead cannot open source: /dev/scd0
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd://' failed: could not create access: no access module matched "dvd"

```

```

diwas@diwas-desktop:~$ mplayer dvd://
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 1.80GHz (Family: 15, Model: 2, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
Couldn't open DVD device: /dev/dvd
No stream found to handle url dvd://


Exiting... (End of file)

```


And thank you for the link for power dvd-linux. But hmm its costly hehe...honestly, i use a cracked version in windows. LOL..anyways i will try to buy it :s...

---

