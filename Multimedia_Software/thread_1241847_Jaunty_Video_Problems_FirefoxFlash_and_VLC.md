---
title: "Jaunty Video Problems Firefox/Flash and VLC"
date: 2009-08-16
forum: Multimedia Software
---

### Post by ShutterAce on 2009-08-16
After a fresh install of Jaunty my youtube and other videos are quite sluggish.

I tried downloading the vid as an MP4 and opening it with Movie Player but it just crashes.

I have removed Flash and installed "Flash 9r48" from a tar ball with no change.

Next I installed VLC from "Applications>Add/Remove" and it won even run.

It worked just fine under Hardy. Heres my output.

Tail of dmesg after trying to open mp4 video with VLC
```
vlc[8038]: segfault at 0 ip b4eb5e60 sp af23cf00 error 4 in libQtCore.so.4.5.0[b4d7d000+238000]
```

...running vlc- v from terminal
```
jadeck@gracie-desktop-ub:~$ vlc -v
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc warning: could not open plugins cache file /home/jadeck/.cache/vlc/plugins-04041e.dat for reading
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

```

Any ideas anyone?

Thanks
-Jim

---

### Post by ShutterAce on 2009-08-29
Fixed it here...
[http://ubuntuforums.org/showthread.php?t=766683&highlight=avi+plugin](http://ubuntuforums.org/showthread.php?t=766683&highlight=avi+plugin)

---

