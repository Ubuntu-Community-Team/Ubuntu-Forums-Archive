---
title: "Vlc always open in a new window"
date: 2009-06-18
forum: Multimedia Software
---

### Post by rushikesh988 on 2009-06-18
Hello friends I got a new problem now  ....
Whenever I open any media file, it  open In a new window of VLC player ...


I want to turn it Off it should open in a one window only (just like VLC acts as in windows)



do any cool body have any solution ;)

---

### Post by mynameinc on 2009-06-18
What is VLC player, and is it downloaded or pre-installed with Ubuntu?  If pre-installed, where can I find it?

---

### Post by rushikesh988 on 2009-06-18
> **mynameinc said:**
> What is VLC player, and is it downloaded or pre-installed with Ubuntu?  If pre-installed, where can I find it?


VLC Player is my favorite player to play audio and video media..

I installed it manually by myself ...

You can find it at 

videolan.org

---

### Post by lovinglinux on 2009-06-18
> **rushikesh988 said:**
> Hello friends I got a new problem now  ....
Whenever I open any media file, it  open In a new window of VLC player ...

I want to turn it Off it should open in a one window only (just like VLC acts as in windows)

do any cool body have any solution ;)

It's a known bug. There is a PPA repository somewhere that fixes this issue, but I don't remember the address. 

> **mynameinc said:**
> What is VLC player, and is it downloaded or pre-installed with Ubuntu?  If pre-installed, where can I find it?

[Click here](apt:vlc) [apt-get] to install it.

BTW, I prefer [smplayer](apt:smplayer) [apt-get]

---

### Post by Arup on 2009-06-18
[https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)

Before installing from this do a sudo apt-get --purge remove vlc in case its installed.

---

### Post by HappyFeet on 2009-06-18
This is an easy fix. Just go to Tools>Preferences>Check off "Allow only one instance". Then click save button.

---

### Post by Tamara Perera on 2009-06-18
have you tried with the latest version of ubuntu named jaunty jacklop. You must try it because here the latest version of VLC is included. I also hated the old version of VLC once but I think now VLC is more cool than anyothers multimedia software.

---

### Post by taylorsmithereens on 2009-06-18
Thanks, this problem was really bugging me and I'm glad to have fixed it so easily.

---

### Post by lovinglinux on 2009-06-18
Never mind.

---

