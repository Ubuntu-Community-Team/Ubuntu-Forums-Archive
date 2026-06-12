---
title: "DVDs won't play."
date: 2009-11-07
forum: Multimedia Software
---

### Post by Valkiyr on 2009-11-07
I've been trying to get DVDs to play for a long time now. I've searched countless forums and found people with the same problems and solutions that worked for them, but not me. I've installed libdvdcss2 and all the other mumbo-jumbo that I'm told I need, but I cannot get it to work. Everytime I try playing a DVD with Movie Player, it says I don't have permission to play the file. The last thing I tried was running, in terminal:

```
vlc /media/cdrom0
```The output I get is:

```
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdread: Device /dev/sr0 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/dominic/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
```Is there anyone that can help me figure this out?

---

### Post by rbee on 2009-11-07
i am using 9.io...from synaptic package manager i installed vlc media player and libdvdread4... worked for me

---

### Post by Valkiyr on 2009-11-08
I already have both and it doesn't work.

---

### Post by brucehinrichs on 2009-11-08
I'm having the same problem.  I have libdvdcss2, libread4, libnav, and everything else I could find via google.  I have set the region code (1 for US), symlinked /dev/dvd and /dev/sr0.... Same message: 'Could not open location; you might not have permission to open the file (also checked user permission settings).  I'm out of ideas atm...

Anyone solved this?

---

### Post by 4Orbs on 2009-11-08
Take a look at [THIS POST]("http://ubuntuforums.org/showthread.php?t=1318919") and maybe it will appeal to you. I'm gonna try it later on today.

---

