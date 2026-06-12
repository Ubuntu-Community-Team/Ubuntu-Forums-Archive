---
title: "Videolan can't read from (DVD) resource"
date: 2009-05-05
forum: Multimedia Software
---

### Post by Extol11 on 2009-05-05
I'm using the Ubuntu 9.04 (Jaunty) 64 bit version. I made sure that I had libdvdcss2 installed and everything necessary but VLC still cannot read dvds. When I choose open disc it has this Disc Device set as default: /dev/sr0 and I don't know if that's what it should be set to. It only opens up for less than a second and then goes back again to the regular menu and doesn't let me play the DVD. It some times gives me an error that says : "could not read block 0" and Movie Player displays the message of the thread: "Can't read from resource". Anyone knows what could be the cause for this problem? It seems it's somewhat common, but I had never had to troubleshoot videolan before, it always worked out of the box. Thanks in advanced.

---

### Post by cariboo on 2009-05-05
Open an Applications-->Accessories-->Terminal and start vlc. Note what error messages you are getting.

---

### Post by Extol11 on 2009-05-06
> vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
That's what I get.

---

### Post by Extol11 on 2009-05-06
> libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 43BF2A32 (GEAR):
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/blix/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.

This is what happens when I try to run it.

This is weird. I do have libdvdcss2 installed says synnaptic. Maybe I don't have a repository that's needed for it? Music files and videos are playing nice. It's only the dvd not working.

---

### Post by xc3RnbFO8P on 2009-05-06
Did try this:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by Extol11 on 2009-05-06
Thanks a whole lot!!! I really appreciate it, man. I'm going to try it in a moment. I'm on windows right now.

---

### Post by Extol11 on 2009-05-06
I just tried it and it worked perfectly. Thanks!

---

