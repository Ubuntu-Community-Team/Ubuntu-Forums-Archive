---
title: "Vlc problems"
date: 2009-02-18
forum: Multimedia Software
---

### Post by ahsun on 2009-02-18
HI, 

I'm new to UBUBNTU.. I tried to change the vlc skin to WMP11.vlt, Once i changed it, I couldn't revert back to old one.. I've removed vlc and reinsatlled it.. yet i keep getting this same error:


VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000414] access_directory access error: /home/ahsun/WMP11.vlt: No such file or directory
[00000414] access_file access error: cannot open file /home/ahsun/WMP11.vlt (No such file or directory)
[00000405] main interface error: no suitable access module for `/home/ahsun/WMP11.vlt'
[00000405] skins2 interface error: failed to open /home/ahsun/WMP11.vlt for reading
[00000405] skins2 interface error: failed to parse /home/ahsun/WMP11.vlt
[00000419] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000419] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000405] skins2 interface error: failed to parse /tmp/vlt22ip7Y/default/theme.xml
[00000405] skins2 interface error: error while parsing /tmp/vlt22ip7Y/default/theme.xml
[00000422] xml xml error: XML parser error (line 1) : Document is empty

[00000405] skins2 interface error: failed to parse /usr/share/vlc/skins2/default.vlt
[00000409] main generic error: object is not attached


Any help will be greatly appreciated.. 

PS.. I've searched and searched and have found nothing about this issue..

---

### Post by ahsun on 2009-02-18
I don't even want the stupid WMP11.vlt. skin.. I just wanna go back to old.. I was just testing things out trying to learn how you do different things in ubuntu..and now I'm stuck..

---

### Post by justsomedude on 2009-02-18
You can delete ~/.config/vlc, and everything will be back to normal. Your other configuration of VLC will be gone though, too. The folder is hidden, so check View --> Show Hidden Files in Nautilus.

---

### Post by ahsun on 2009-02-18
Thanks alot my friend.  IT worked.. was just wondering.. I downloaded a whole bunch of skins, all are vlt, but there is only one that i can switch to, and that was wmp11.. the rest it storing an .fr.....something rather.. How do get there and above all how do delete those.. I can't even seem to get to that page.. 

Thanks for your help though

---

### Post by rmlrml on 2009-03-06
the folder for the skins is usr/share/vlc/skins2

---

