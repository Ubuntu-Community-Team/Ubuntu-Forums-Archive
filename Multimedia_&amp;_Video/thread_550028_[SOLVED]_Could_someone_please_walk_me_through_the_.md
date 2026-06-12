---
title: "[SOLVED] Could someone please walk me through the RealPlayer 10 installation process?"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by Ubuntu Joe on 2007-09-13
I know this is probably a stupid question, but Ubuntu is so easy, I rarely have to install programs manually!  I'm CLULESS about where applications live in my Linux file system . . . so I need your help!!

---

### Post by reckless2k2 on 2007-09-13
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29)

/usr/local/

it'll ask about a symlink to /usr...say yes....BANG..done


mark it as SOLVED. hahaha

---

### Post by wolfen69 on 2007-09-13
another way to get commercial software:
in terminal:
```
gksudo gedit /etc/apt/sources.list
```
add the following line:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
save file.
in terminal:
```
sudo apt-get update
```
all available commercial software will now be in synaptic package manager.

---

### Post by Ubuntu Joe on 2007-09-19
Sweet guys, thatnks!

:guitar:

---

