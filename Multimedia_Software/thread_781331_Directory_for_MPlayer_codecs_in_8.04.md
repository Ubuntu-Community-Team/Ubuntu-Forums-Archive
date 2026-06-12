---
title: "Directory for MPlayer codecs in 8.04?"
date: 2008-05-04
forum: Multimedia Software
---

### Post by dowoshek on 2008-05-04
Hi,

Just like in subject - where should i put codecs downloaded from the official MPlayer site? I use Mplayer repository package.
In previous versions of Ubuntu i used /usr/lib/win32 and now it doesn't work :( I already tried /usr/lib/codecs, /usr/local/lib/codecs and /usr/local/lib/win32. And it still doesn't work. I.e. i can't play rmvb files.

Anybody...? :)

---

### Post by andrew.46 on 2008-05-08
Hi,

 I could be terribly wrong but my impression was that you need to compile mplayer with these codecs already in place so the compiler can find them and allow mplayer to use them.

 Have you considered compiling your own mplayer?

          Andrew

---

### Post by dowoshek on 2008-05-08
Yes, i know i can compile it, but there's no need to... It'd be enough to know what was the '--codecsdir' value for the MPlayer package in 8.04 repository. It was /usr/lib/win32 before and now it doesn't work...

Is here really nobody using MPlayer and its original codecs in 8.04...?

---

### Post by mc4man on 2008-05-08
> It'd be enough to know what was the '--codecsdir' value for the MPlayer package in 8.04 repository. It was /usr/lib/win32 before
Here' configs for hardy repo version. It uses --win32codecsdir
```
CONFIGURE_PATH := --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32
CONFIGURE_COMMON := --enable-runtime-cpudetection --enable-largefiles
CONFIGURE_INPUT :=  --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio
CONFIGURE_CONTROL := --enable-lirc --enable-joystick --enable-xf86keysym 
CONFIGURE_AUDIO_CODECS := --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib
CONFIGURE_VIDEO_CODECS := --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2
CONFIGURE_AUDIO_OUT := --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas
CONFIGURE_VIDEO_OUT := --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev
CONFIGURE_MISC := --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa
``` As mentioned it's better to build your own but if i was using the repo version I'd install w32codecs from medibuntu which will install to /usr/lib/codecs with a link<win32> in /usr/lib. Then if you want to append or replace codecs from the mplayer binary just copy them to /usr/lib/codecs

---

### Post by dowoshek on 2008-05-09
Oh... then that's stange it doesn't work... i mean doesn't play .rmvb like it used to in 7.10 and before, hmm...

BTW, where did you find this configuration? Source repositories?

---

### Post by mc4man on 2008-05-09
> BTW, where did you find this configuration? Source repositories?
that's from the rules file in /debian. I delete it and modify the rules file in debian_upstream then paste that into debian, everything works fine. 
The last couple of svn checkouts show some error about mv's so atm i 'm liking the repo source best.

---

### Post by dowoshek on 2008-05-09
It works after w32codecs installation and now i wonder if i had it installed before... :) But i think i had, so my mistake - i thought that the codecs pack from MPlayer website should be enough for rmvb... and it looks like it's not ;)
Thanks for your help

---

### Post by robertyou on 2008-10-10
In ubuntu, you just need to create a directory for mplayer codecs..

sudo mkdir /usr/lib/win32

and put all the codec files in there. Not sure if mplayer plays rmvb tho.

---

