---
title: "VLC only crashes, nothing else ;P"
date: 2009-11-25
forum: Multimedia Software
---

### Post by tom957 on 2009-11-25
I've always been a fan of VLC, but now it does this:

```
vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
/home/tom/.gtkrc-2.0:1: error: unexpected character `\342', expected keyword - e.g. `style'
Aborted
```

Any ideas? I also get the ```
/home/tom/.gtkrc-2.0:1: error: unexpected character `\342', expected keyword - e.g. `style'
``` message when using gmount-iso, but it works fine. Could that be the main culprit?

---

### Post by JBAlaska on 2009-11-25
2 things you can try, 1-change your Ubuntu theme and 2- uninstall VLC through synaptic then re-install.

---

### Post by tom957 on 2009-11-25
Thanks for the reply. I'll try messing with my theme, etc. 

I did solve the problem with the crash by removing the ~/.config/vlc folder then reinstalling. Even an apt purge wasn't removing the full configuration, so I had to go Viking-style.

---

### Post by Arup on 2009-11-25
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

Add the PPA to your repo and you will have latest vlc 1.03 which works quite good.

---

### Post by tom957 on 2009-11-25
Doin' it right now. Thanks!

---

### Post by JBAlaska on 2009-11-25
Cool, If you get the ```
/home/tom/.gtkrc-2.0:1: error: unexpected character `\342', expected keyword - e.g. `style'
``` error again you need to clear out your gtkrc-2.0 file.

---

### Post by tom957 on 2009-11-25
Problem fixed. Thanks again.

---

