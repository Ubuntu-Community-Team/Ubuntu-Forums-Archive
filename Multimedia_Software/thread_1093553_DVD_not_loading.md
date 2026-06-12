---
title: "DVD not loading"
date: 2009-03-11
forum: Multimedia Software
---

### Post by Bofur on 2009-03-11
Hi, I'm having trouble playing a dvd with vlc. I've gotten it to work in previous versions of Ubuntu just fine before but with the current release it doesn't seem to want to work. Here's the output: ```
justin@ubuntu:~$ vlc /media/cdrom0/
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/justin/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6
*** Zero check failed in ifo_read.c:1888
    for pgci_ut->zero_1 = 0xfab7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1890 ***
*** for pgci_ut->nr_of_lus < 100 ***

*** Zero check failed in ifo_read.c:1760
    for pgcit->zero_1 = 0xfab7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1764 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1787 ***
*** for pgcit->pgci_srp[i].unknown1 == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1787 ***
*** for pgcit->pgci_srp[i].unknown1 == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***

libdvdnav: ifoRead_PGCI_UT failed
vlc: /build/buildd/libdvdnav-4.1.2/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted

```

---

### Post by Bofur on 2009-03-11
Fixed it. Just needed libdvdcss2.

---

