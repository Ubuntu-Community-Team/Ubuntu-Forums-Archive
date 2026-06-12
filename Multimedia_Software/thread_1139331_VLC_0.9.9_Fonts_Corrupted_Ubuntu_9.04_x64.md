---
title: "VLC 0.9.9 Fonts Corrupted Ubuntu 9.04 x64"
date: 2009-04-26
forum: Multimedia Software
---

### Post by gamergod131 on 2009-04-26
Hello, whenever I started up VLC today, I noticed that all the fonts on the menus were unreadable and obviously messed up:

[[IMG]http://img518.imageshack.us/img518/3963/screenshotvlcmediaplaye.png[/IMG]](http://img518.imageshack.us/my.php?image=screenshotvlcmediaplaye.png)

This is the output when I open it using the terminal:

```
blabla@blabla-desktop:~$ vlc
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

```

Can anyone help to restore the fonts?

---

### Post by mc4man on 2009-04-27
The first thing you should try when vlc's behaviour changes is this and if no good then take it from there.

```
vlc --reset-config
```

............


Have you changed/installed new video drivers?

---

### Post by gamergod131 on 2009-04-27
> **mc4man said:**
> The first thing you should try when vlc's behaviour changes is this and if no good then take it from there.

```
vlc --reset-config
```

............


Have you changed/installed new video drivers?

No dice: 

[[IMG]http://img513.imageshack.us/img513/993/screenshotprivacyandnet.png[/IMG]](http://img513.imageshack.us/my.php?image=screenshotprivacyandnet.png)

I have checked my gtx 260's drivers in the driver manager and installed the drivers (although that was a couple days ago, this happened only recently).

---

### Post by schmolch on 2009-05-03
Same here with all qt apps on my default jaunty desktop.

---

### Post by schmolch on 2009-05-03
Found a workaround on another thread, you have to disable sub-pixel-rendering in gnome's fonts manager, just use something else like best shapes.

---

