---
title: "Hardware acceleration issues."
date: 2011-01-02
forum: Multimedia Software
---

### Post by droidzilla on 2011-01-02
Its been a while since I have used ubuntu but since I have built my HTMC almost a year ago i had been planning on installing Ubuntu with XBMX or Boxee. 

Hardware:
ZOTAC IONITX-F-E Intel Atom 330 (1.6GHz, dual-core) NVIDIA ION Mini ITX Motherboard

I started out by installing the drivers provided by the "Additional Drivers" program. Then installed libvdpau1. I cannot get video acceleration to work if my life depended on it. I have followed every tip i can muster in google and still nothing. I installed VLC and made sure all the acceleration options were on. About half of a second of video plays then freezes but I can still hear the sound. With xbmc it doesnt show anything on the screen or play audio, xbmx just gets really sluggish until i hit stop. boxee doesnt show anything on the screen or audio and eventually it crashes. 

Since I am still a noob I am chalking it up to that.

Anyone have any ideas?

Thanks in advance,
-Droidzilla

---

### Post by Yellow Pasque on 2011-01-03
VLC does not have direct vdpau output (I'm not sure about xbmc/boxee). You either need to use a video player that does (like Mplayer) or use this PPA: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks) and then install a vdpau backend for va-api: [http://www.splitted-desktop.com/~gbeauchesne/vdpau-video/pkgs/](http://www.splitted-desktop.com/~gbeauchesne/vdpau-video/pkgs/)

---

