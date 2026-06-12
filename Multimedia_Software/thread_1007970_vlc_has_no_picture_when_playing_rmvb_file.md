---
title: "vlc has no picture when playing rmvb file"
date: 2008-12-11
forum: Multimedia Software
---

### Post by EnterTheDarkSide on 2008-12-11
hi,

i was trying to play a rmvb file with vlc but it only has sound and no picture. does anyone know how to fix this problem?

tnx

---

### Post by status001 on 2008-12-13
OK, first of all I wanted to say that, I've just manged to play an rmvb file successfully. Me too didn't managed to play an rmvb file with Totem, VLC or Mplayer. I've downloaded Real Player from their official site. Here is the link,
[http://www.real.com/linux]("http://www.real.com/linux")
At the bottom of this page, you will find a link to download the deb package for it. It is around 8.5 mb in size. Download it and open it by double clicking. Now you will see in the package manager it needs some dependent package. Install them first and then again try to install the real player deb file.
The way I installed them is, I didn't install the depencies first. Just installed the main real playe deb packages. This make an error in the package manager system. So, I wrote in the terminal this command,
```
sudo apt-get install -f
```
and the package manger installed the dependencies currectly. Then I found the real player option in "Applications>Sound and Video>RealPlayer 11" menu. And that's the way it worked. No problem at all. Thanks.

---

### Post by EnterTheDarkSide on 2009-01-11
> **status001 said:**
> OK, first of all I wanted to say that, I've just manged to play an rmvb file successfully. Me too didn't managed to play an rmvb file with Totem, VLC or Mplayer. I've downloaded Real Player from their official site. Here is the link,
[http://www.real.com/linux]("http://www.real.com/linux")
At the bottom of this page, you will find a link to download the deb package for it. It is around 8.5 mb in size. Download it and open it by double clicking. Now you will see in the package manager it needs some dependent package. Install them first and then again try to install the real player deb file.
The way I installed them is, I didn't install the depencies first. Just installed the main real playe deb packages. This make an error in the package manager system. So, I wrote in the terminal this command,
```
sudo apt-get install -f
```
and the package manger installed the dependencies currectly. Then I found the real player option in "Applications>Sound and Video>RealPlayer 11" menu. And that's the way it worked. No problem at all. Thanks.

wow thanks, i didn't expect to get an answer after so long. I downloaded the deb package from the real site. However it said "wrong architecture i386". i assume it said that because i have a x86_64 cpu. do you know of 64 bit deb package for realplayer?

---

### Post by Memes11 on 2009-01-26
it is in Medibuntu repos. but I have a strange stuff happening, I just installed it and when I play a rmvb with it, colors are reversed (sky is yellow, sun is blue...)

I'll try to reboot

---

### Post by EnterTheDarkSide on 2009-03-12
thru an mplayer update i am now able to play rmvb files. however the sound and video sometimes don't match each other (the voice is faster than the pictures). but i never had the problem of colors being reversed. weird! anyways i'm installing the 32-bit kubuntu and will install the 32-bit real player. hopefully everything will be fine.

---

