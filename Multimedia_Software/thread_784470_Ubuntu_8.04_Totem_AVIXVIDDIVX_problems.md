---
title: "Ubuntu 8.04 Totem AVI/XVID/DIVX problems"
date: 2008-05-06
forum: Multimedia Software
---

### Post by omi on 2008-05-06
Hi people,

I'd installed Ubuntu 8.04 but still have problems with video playback of *.avi files with Totem.

I'd installed:
- ATI driver from System -> Administration -> Hardware Drivers

* Advanced Video Effects are disabled

Also I'd done this (according to ubuntuguide.org->media codecs):

```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3
```

Also I'd done this (after adding mediabuntu repository):

```
sudo ubuntu-restricted-extras
sudo apt-get install w32codecs
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
```

I've downloaded and played [http://ed.plonkmedia.org/Elephants_Dream_HD.avi](http://ed.plonkmedia.org/Elephants_Dream_HD.avi) 

..and here everything is okay, there is no pixelization and the playback is great.

**But still has choppy video while playing *.AVI (DIVX/XVID - DVD Rips) files with Totem and VLC. There is some pixelization of the movies (check attached file).**

I was searching for a solution in the forum but didn't find it so I'm starting this thread. Have no problems with anything else in Ubuntu 8.04. I'm using HP Compaq 6820s Laptop with ATI video card.

Hope someone can help.

---

### Post by cor2y on 2008-05-06
Gstreamer took two steps forward and one step back in this version of ubuntu.
As far as i know there is noway to solve the pixelation.
You may have to use totem-xine or mplayer for avi and dvd playback, in this version of ubuntu gstreamer can play dvds again but it still cannot navigate dvd menus.

---

### Post by rine238 on 2008-05-10
I really don't know what could be a problem. I have Ubuntu 8.04 and for the first time everything is working well on my laptop acer extensa 5210, it's so fast, so good, I have tried Kubuntu too and Fedora, but I have to say that to me Ubuntu is working at best way. :)

I use totem movie player, and all AVI files play normally, my music videos are codec by XviD (I did that so encoded), and movies often by DivX, and everthing is working well. I have normally subtitles, character encoded east/central european ISO-8859-2, totem play them well and I can see all signs well!

---

