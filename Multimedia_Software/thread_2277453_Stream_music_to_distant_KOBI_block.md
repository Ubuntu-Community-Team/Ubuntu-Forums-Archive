---
title: "Stream music to distant KOBI block"
date: 2015-05-09
forum: Multimedia Software
---

### Post by chris_wafer_2001 on 2015-05-09
Hello,

I try to stream music played on my PC to " Kodi " available on a distant raspberryPi (in OpenELEC ) .
But the sound stops abruptly when I ask diffusion.

When I listen to music on a browser :
[[img]http://img11.hostingpics.net/pics/155705son1.jpg[/img]](http://www.hostingpics.net/viewer.php?id=155705son1.jpg)

[[img]http://img11.hostingpics.net/pics/580737son2.jpg[/img]](http://www.hostingpics.net/viewer.php?id=580737son2.jpg)


When I ask to stream :
[[img]http://img11.hostingpics.net/pics/933048son3.jpg[/img]](http://www.hostingpics.net/viewer.php?id=933048son3.jpg)

[[img]http://img11.hostingpics.net/pics/711100son4.jpg[/img]](http://www.hostingpics.net/viewer.php?id=711100son4.jpg)

Where is the problem?

---

### Post by Bucky Ball on 2015-05-09
MUCH easier to go to Kodi>Music>Files>Add Files and create a network connection to the music directory on your computer. Best if you have a static IP on the computer when doing this (and the RPi should already have a static IP set up). Then you can see the music on your machine from Kodi and stream it directly from your machine to Kodi. Kodi is set up to do it this way already as it is a media server app. You should link to the multimedia on other computers in the network from Kodi rather than the other way around (messy). You shouldn't need to change anything on your local machines, only create connections to the correct directories on the RPi. 

Apologies if you are attempting to do it by setting up streaming from the computer ON the computer for some specific reason or other that prevents you from doing it the way I've outlined.

PS: You give no indication of which Ubuntu release/flavour you are using. Please enlighten us. ;)

---

### Post by chris_wafer_2001 on 2015-05-09
Thanks for your answer.

My environment is :
 - PC with Xubuntu 14.04.2 LTS
 - Rapberry PI with OpenElec and KOBI

I already play files with your method.
But, now, I would like to stream deezer/spotify from PC to distant KOBI, and it is blocked (see screenshot).

What is the problem?

---

