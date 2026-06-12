---
title: "Choppy video in VLC, not in Totem"
date: 2009-05-24
forum: Multimedia Software
---

### Post by Cubytus on 2009-05-24
Hi to all, 

Among the new problems that alwys come with new OSes, I noticed that the same video (encoded in XviD) read in Totem was fluid (after having accepted automated codec install)

However, VLC usually is the "ultimate player", reading when others crash, video is incomplete, etc., I installed it from Synaptic.

Same video launched in VLC, it first asks to repair AVI index, and when it starts playing, video is choppy, and sometimes freezes for many minutes, despite sound being fluid.

On each XviD-encoded video I tried, VLC asked to repair AVI index, which itself is a problem since none of these videos are corrupted. More, trying to play the same video after still triggers the "Repair index?" dialog, even when the video has already been "repaired".

On the same computer, playing video worked flawlessly with VLC in Ubuntu 8.04.

What is the cause of this problem, and how to solve it?

---

### Post by xc3RnbFO8P on 2009-05-24
Try this:
> Start VLC and click on Settings, then Preferences.Expand Video and then expand Output modules. You will notice several options for output device.
Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
Pick X11 video output
Click on Save and you are set

---

### Post by Cubytus on 2009-05-24
I did that. Now it's a bit more fluid, but it's still visibly dropping frames.

Same video sequence in Totem is completely fluid.

So, it's not solved.

---

### Post by xc3RnbFO8P on 2009-05-24
Start VLC in Terminal:
> vlc
show the output here.

Check if you got 
libavcodec-unstripped-52 3.0 svn20090303
libxvidcore4
ffmpeg 3.0 svn20090303

---

### Post by Cubytus on 2009-05-25
These libs were not installed. I manually installed them through Synaptic, and relaunched the video. However,it'S still as choppy as before.

her is the output running **vlc** in a Terminal:
```
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "FR"
```

---

