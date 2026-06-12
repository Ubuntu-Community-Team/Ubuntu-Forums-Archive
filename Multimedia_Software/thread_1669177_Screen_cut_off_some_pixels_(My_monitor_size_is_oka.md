---
title: "Screen cut off some pixels (My monitor size is okay)"
date: 2011-01-17
forum: Multimedia Software
---

### Post by PedroHLC on 2011-01-17
Hi. I recently installed ubuntu 10.10, and I like it alot, but the problem is that a little right part of the screen not beeing displayed, I clicked a lot of times in the auto-adjust button on my monitor and the problem is still here.

Monitor: Acer Technologies 19" (Maximum resolution: 1360x768 60Hz)
Videoboard: ATI Radeon 9600

In windows i used the resolution 1360x768 and on ubuntu it is 1366x768

A demostration of exaclty what I'm seeing:
[IMG]http://img211.imageshack.us/img211/7998/capturadetelaeditada.png[/IMG]


Other observation:
I'm using dual-boot (Ubuntu and Windows Seven)
My monitor don't have manual size values

Sorry about my english :S
:D I'm glad with your attention!

---

### Post by PedroHLC on 2011-01-17
I solved this using this tutorial:
[http://www.uluga.ubuntuforums.org/showpost.php?p=9418202&postcount=5](http://www.uluga.ubuntuforums.org/showpost.php?p=9418202&postcount=5)

I only changed this line:
HRES=1024;VRES=768
by this line:
HRES=1360;VRES=768

---

