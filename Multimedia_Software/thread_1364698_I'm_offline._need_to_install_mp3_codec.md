---
title: "I'm offline. need to install mp3 codec"
date: 2009-12-26
forum: Multimedia Software
---

### Post by tuumi on 2009-12-26
I'm pretty new to Linux. I made a media center computer for my brother who lives in the boonies without internet. He can listen to the mp3 files on VLC but since I forgot the install the MP3 codecs he can't use Rythmbox to create a library of his music.
 
I need a self installing program that I can put a thumb drive and take to his computer so I can install the mp3 codecs. Is there a simple program (linux equivalent of an .exe) that will do what I need. Or is there another simple way to get what I need on his computer?
Thanks for your help.

---

### Post by ron999 on 2009-12-26
Hi
For Rhythmbox the codec you need is called:-
**gstreamer0.10-fluendo-mp3 0.10.7.debian-1ubuntu1**
(For Karmic Koala that is).

You can download a deb package from here:-
[https://launchpad.net/ubuntu/+source/gst-fluendo-mp3/0.10.7.debian-1ubuntu1]("https://launchpad.net/ubuntu/+source/gst-fluendo-mp3/0.10.7.debian-1ubuntu1")
:guitar:

Then you will install it using the program **GDebi Package Installer**.
Or right-click and install with... GDebi

---

### Post by tuumi on 2009-12-26
OK thanks. I've got those three files on a thumb drive and I'll try it out later today and get back.
You guys are great.
:guitar:

---

### Post by ron999 on 2009-12-26
> **tuumi said:**
> OK thanks. I've got those three files on a thumb drive and I'll try it out later today and get back.
You guys are great.
:guitar:
NO NO NO
I've given you the wrong link.
It's this one that you need:-
[http://packages.ubuntu.com/karmic/gstreamer0.10-fluendo-mp3]("http://packages.ubuntu.com/karmic/gstreamer0.10-fluendo-mp3")
It's just one file. The one that says **i386**. At the bottom of the page.
Sorry.
:confused:

---

### Post by tuumi on 2009-12-26
Yeah. I couldn't get those to work. I'm back and I'll give those a shot.
Should the gdebi installer already be installed?

---

### Post by ron999 on 2009-12-26
OK, 1000 apologies.

Yes, Gdebi comes with Ubuntu, if it's not already installed you can get it from
System > Administration > Synaptic Package Manager.

---

### Post by mac9416 on 2009-12-28
Hey, tuumi,

The best way to get .debs to install on offline computers is to use [Keryx]("http://keryxproject.org"). It acts much like Synaptic except you can carry it on a flash drive.

For your brother, you will want to download ubuntu-restricted-extras using Keryx. When you get ubuntu-restricted-extras and its dependencies to your brother's, you can install them by simply double-clicking each file.

Hope that helps!

---

