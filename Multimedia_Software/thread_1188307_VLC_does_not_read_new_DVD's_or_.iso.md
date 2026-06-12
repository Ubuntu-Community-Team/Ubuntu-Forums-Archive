---
title: "VLC does not read new DVD's or .iso"
date: 2009-06-15
forum: Multimedia Software
---

### Post by wissemeier05 on 2009-06-15
Good afternoon,

Last week I picked up a copy of Enemy at the Gates tried to play it in my laptop (at the time Ubuntu 8.10, now 9.04).  I got nothing but static and a crash.  So I updated the system, still no dice.  I upgraded to 9.04, Still no dice.

[IMG]http://img39.imageshack.us/img39/1356/screenshotrly.png[/IMG]



Clues:
-there is a windows XP partition on the laptop, Enemy at the Gates works fine (god love Mosin Nagants)
-In ubuntu my old .iso images of my DVD's still play fine in VLC

Possibly related:
-my printing also stopped working at the same time. 'the cups server' seems to be at fault but I cant seem to find a problem


What did I break?
TIA
Dan

---

### Post by mc4man on 2009-06-15
It appears the dvd isn't being decrypted, is libdvdcss2 installed?

Start vlc from a terminal, then open the dvd and see what's reported.

---

### Post by wissemeier05 on 2009-06-15
dan@dan-laptop:~$ vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"


I do not see the "Libdvdcss2" is my fix just as easy as installing it?


I installed "ubuntu-restricted-extras".  still no dice.

---

### Post by wissemeier05 on 2009-06-15
dan@dan-laptop:~$ sudo apt-get install libdvdcss2 gxine libxine1-ffmpeg vlc mplayer mencoder 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
dan@dan-laptop:~$ 


do I need a new software source (I have all of them checked?)

---

### Post by mc4man on 2009-06-15
You can either get manually, add medibuntu to your sources or run this in a terminal

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

for direct go here, pick what your using (32 bit or amd_64, click on and let gdebi install (most likely 32 bit - i386

[http://packages.medibuntu.org/jaunty/libdvdcss2.html](http://packages.medibuntu.org/jaunty/libdvdcss2.html)

To add medibuntu go here and follow instr. for jaunty (run the sudo wget... and then do the 'add key' line

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

!what I meant by open vlc from a terminal and then the disc should of shown something like this (except without libdvdcss2 it would have said no decryption available> 

doug@doug-desktop:~$ vlc
VLC media player 1.0.0-rc3 Goldeneye
[0x8051140] main libvlc debug: libvlc was configured with ./configure  '--prefix=/usr' '--disable-zvbi' '--enable-flac' '--enable-libass' '--enable-caca' '--enable-faad' '--disable-kate' '--enable-twolame' '--enable-theora' '--with-x264-tree=/usr/include' '--enable-cddax' '--disable-fluidsynth' '--with-live555-tree=/usr/lib/live' '--enable-loader' '--with-tuning=native' '--disable-nls' '--disable-mozilla' '--disable-mod' '--enable-real' '--enable-realrtsp' '--disable-pulse'
[0x8051140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread:[COLOR="Blue"] Using libdvdcss version 1.2.10 for DVD access[/COLOR]
libdvdnav: DVD Title: THE_MONTEREY_POP_FESTIVAL
libdvdnav: DVD Serial Number: 2d41b774
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/doug/.dvdnav/THE_MONTEREY_POP_FESTIVAL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[0x825d498] main input error: ES_OUT_RESET_PCR called  [COLOR="Blue"]<- can be ignored
[/COLOR]
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000180
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000174dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00289b2a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002a2245
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002ab317
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
[0x82e15f0] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

---

### Post by wissemeier05 on 2009-06-15
Thanks a ton 
"sudo /usr/share/doc/libdvdread4/install-css.sh" worked perfectly

Dan

---

