---
title: "problem while watching video with fglrx"
date: 2012-06-07
forum: Multimedia Software
---

### Post by bosha on 2012-06-07
For a long time have a strange problem while watching movies: if open video, stop\play them somewhere around 20 times - the video is dissappear. Sound working, but no video output. 
Video appears only after restarting X server. 

> 
&#9492;&#9472;[% >cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

&#9492;&#9472;[% >apt-cache show fglrx-updates | i Version
Version: 2:8.960-0ubuntu1

&#9492;&#9472;[% >X -version 
X.Org X Server 1.11.3
Release Date: 2011-12-16
...

&#9492;&#9472;[% >uname -a
Linux bosha-pc 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 athlon i386 GNU/Linux

In dmesg with fglrx only - [http://pastebin.com/Cejfymr0](http://pastebin.com/Cejfymr0)
If run mplayer from terminal, to stdout goes - [http://pastebin.com/c3pbEnbt](http://pastebin.com/c3pbEnbt)
Xorg.0.log - [http://pastebin.com/hG3y1hZD](http://pastebin.com/hG3y1hZD)

DE - Xfce 4.10 (problem appears on KDE, Unity, Gnome3 too)

---

### Post by bosha on 2012-06-08
Changing from "Autodetect" to "No Xv" in gstreamer-properties solved my problem. 

Interesting, why with open source driver all works fine..

---

