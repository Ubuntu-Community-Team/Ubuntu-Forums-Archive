---
title: "vlc won't start"
date: 2008-12-24
forum: Multimedia Software
---

### Post by Dai777 on 2008-12-24
I'm having problems starting vlc getting the error message below.
I've tried un-installing and re-installing but no joy it still won't start.
Would appreciate some help sorting this out.


error message:
VLC media player 0.9.8a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.8a Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--mandir=/share/man' '--infodir=/share/info' '--host=i486-linux-gnu' '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-real' '--enable-realrtsp' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-faad' '--with-faad-tree=extras/faad2' '--enable-x264' '--with-x264-tree=extras/x264' '--enable-glide' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'host_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'PKG_CONFIG_PATH=:extras/x264:extras/faad2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000407] access_directory access error: /usr/share/vlc/skins2/Heaven.vlt: No such file or directory
[00000407] access_file access error: cannot open file /usr/share/vlc/skins2/Heaven.vlt (No such file or directory)
[00000403] main interface error: no suitable access module for `/usr/share/vlc/skins2/Heaven.vlt'
[00000403] skins2 interface error: failed to open /usr/share/vlc/skins2/Heaven.vlt for reading
[00000403] skins2 interface error: failed to parse /usr/share/vlc/skins2/Heaven.vlt
WARNING: QApplication was not created in the main() thread.
ASSERT failure in QCoreApplication: "there should be only one application object", file kernel/qcoreapplication.cpp, line 423
Aborted

---

### Post by mc4man on 2008-12-24
Did you try to change the skin? Vlc 0.9.x doesn't work well with custom skins.
You should see something more like this (red
> VLC media player 1.0.0-git Goldeneye
[0x8051168] main libvlc debug: VLC media player - version 1.0.0-git Goldeneye - (c) 1996-2008 the VideoLAN team
[0x8051168] main libvlc debug: libvlc was configured with ./configure  '--disable-zvbi' '--enable-flac' '--enable-libass' '--enable-caca' '--enable-faad' '--disable-dvb' '--disable-dvbpsi' '--disable-kate' '--disable-mpc' '--enable-x264' '--with-x264-tree=./extras/x264' '--enable-mp4'
[0x8051168] main libvlc debug: translation test: code is "C"
[0x8051168] main libvlc: [COLOR="Red"]Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[/COLOR]

If you did change the skin to reset go to home folder -> .config and delete the vlc folder. (.config is a 'hidden' folder

I see korn has released the 0.9.8a version, is the video still embedded in same window as controller?

---

### Post by Dai777 on 2008-12-24
> **mc4man said:**
> Did you try to change the skin? Vlc 0.9.x doesn't work well with custom skins.
You should see something more like this (red

If you did change the skin to reset go to home folder -> .config and delete the vlc folder. (.config is a 'hidden' folder

I see korn has released the 0.9.8a version, is the video still embedded in same window as controller?

Thanks for the help sorted

---

### Post by bsmith1051 on 2008-12-31
I was having a similar problem and deleting the /.config/VLC folder helped me, too!

I had been using the 'standard' version, 0.9.4, from the repositories but now I want to try using the latest Nightly Build from Videolan.org

---

### Post by mc4man on 2008-12-31
@bsmith1051
What may also work in that situation  or if vlc starts acting up is to start vlc from the terminal with this
```

vlc --reset-config
```

---

