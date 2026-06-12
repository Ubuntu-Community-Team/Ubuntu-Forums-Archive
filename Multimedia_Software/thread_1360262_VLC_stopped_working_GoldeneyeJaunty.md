---
title: "VLC stopped working Goldeneye/Jaunty"
date: 2009-12-20
forum: Multimedia Software
---

### Post by dmu on 2009-12-20
Hi,

Have had vlc 0.99 working from original jaunty install then upgraded to Goldeneye
from Goldeneye ppa also working for a long time until now see error below
(btw: Mplayer still ok)

No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.

vlc debug output indicates problem with libraries...

vlc -v
VLC media player 1.0.2 Goldeneye
[0x9695140] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so'
  (libavutil.so.49: cannot open shared object file: No such file or directory)
[0x9695140] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' 
  (libavutil.so.49: cannot open shared object file: No such file or directory)

dpkg -S libavcodec_plugin
vlc-nox: /usr/lib/vlc/codec/libavcodec_plugin.so

dpkg -S libavformat_plugin
vlc-nox: /usr/lib/vlc/demux/libavformat_plugin.so

dpkg -p vlc-nox | grep Version
Version: 1.0.2-1~ppa1


ls -l /usr/lib/vlc/codec/libavcodec_plugin.so
-rw-r--r-- 1 root root 75384 2009-09-22 14:37 /usr/lib/vlc/codec/libavcodec_plugin.so
ls -l /usr/lib/vlc/demux/libavformat_plugin.so
-rw-r--r-- 1 root root 46592 2009-09-22 14:37 /usr/lib/vlc/demux/libavformat_plugin.so



Mplayer still working, ffmpeg version is
dpkg -p ffmpeg | grep Version
Version: 4:0.5+svn20090924-0ubuntu0~ppa2


Just two questions,

1) Why does vlc think it cannot load the libraries
2) What have I got to do to fix it? (presumably answering the previous question will get it to work again)

Cheers.

---

### Post by mc4man on 2009-12-20
Pretty simple - you are using shared ffmpeg libs that are incompatible with the build of vlc you have ( appears you're using M. Marleys ppa.

While you can use updated shared ffmpeg libs they need to be built so you don't break repo apps, plugins that depend on them, otherwise why bother having them.(obviously not the case here.

Solutions are -  to disable the ppa, remove the shared ffmpeg libs, reinstall the ubuntu or for karmic the medibuntu ffmpeg libs and re-install vlc.

Build your own updated shared ffmpeg lib packages.

Build your vlc, either off of the current -devs from MM ppa or preferably off of a static ffmpeg you build first. ( that way ffmpeg support is built-in to vlc, what ffmpeg version/packages you have installed become irrelevant and don't affect vlc

---

### Post by dmu on 2009-12-21
Hi,

>Solutions are - to disable the ppa, remove the shared ffmpeg libs, reinstall the ubuntu or >for karmic the medibuntu ffmpeg libs and re-install vlc.

That fixed it.

I had used the marley PPA to install nvidia 190 drivers (also a bad idea - much
better to download the bin package from NVIDIAs website)

Cheers.

---

