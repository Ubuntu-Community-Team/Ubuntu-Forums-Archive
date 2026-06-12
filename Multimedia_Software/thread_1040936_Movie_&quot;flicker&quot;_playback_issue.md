---
title: "Movie &quot;flicker&quot; playback issue"
date: 2009-01-16
forum: Multimedia Software
---

### Post by xjas05 on 2009-01-16
When I'm watching any type of movie with VLC or mplayer, there's a slight "flicker" when theres a lot of movement, it is kinda subtle, but it is noticable, and after a few minutes you really start to look for it and its annoying, its almost as if the screen refresh rate isn't high enough, although nvidia-xconfig does report I'm running @ 59.95hz ('Screen Resolution' under System->Preferences can either report 51hz, or 112hz, depending on which refresh rate I choose in nvidia-xconfig, even though they're '60hz(1)', and '60hz(2)')

Was using the 177 driver that ubuntu can automatically install, until now, thought first thing I'd try is maybe updating the gfx, even with 180.22 its the same thing... specs in signature, this is nowhere near a low end machine... I don't know where the problem is
(Playback is fine under Windows)

---

### Post by zika on 2009-01-16
for **vlc** try this as a command to start it:```
vlc --vout x11 %U
```for **mplayer** try this as a command to start it:```
mplayer -vo x11 %U
```(%U is if You are making a launcher, otherwise substitute it with the name of Your file) 
for all other```
System->Preferences->Multimedia_Systems_Selector->Video->X...(no xv)
```

---

### Post by xjas05 on 2009-01-16
This is the output:

```

VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[00000430] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:384000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1

```

---

### Post by listerthrawn on 2009-01-16
Try disabling compiz or whatever 3d effects you have and use metacity and see if the flicker is still there.

---

### Post by zika on 2009-01-16
> **listerthrawn said:**
> Try disabling compiz or whatever 3d effects you have and use metacity and see if the flicker is still there.
tips that I gave in my previous post (#2) work **with compiz on** (at least on my machine, ATI HD 3650, ATI 8.561 driver (8.12 Catalyst)).

---

### Post by listerthrawn on 2009-01-16
It's been a while since I had this problem (as I normally turn the effects off), but when I tried it with the x11 switch, the flicker was better but not gone.  The only way I found to get rid of it completely was to switch off the effects.

The flicker seemed to affect all movie players and not just vlc and I think it would help if this issue was resolved for all.  Do we know what actually causes the flicker?

---

### Post by xjas05 on 2009-01-16
sweeeeeeet, that was it, I set 3d effects to 'none' and no more subtle flickers

---

### Post by theadmira1 on 2009-01-16
where do you turn them off?

---

### Post by mikeftl on 2009-01-17
> **theadmira1 said:**
> where do you turn them off?
rightclick desktop>change background>effects>none

---

