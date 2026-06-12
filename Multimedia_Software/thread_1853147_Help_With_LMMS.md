---
title: "Help With LMMS"
date: 2011-10-01
forum: Multimedia Software
---

### Post by Benjotter on 2011-10-01
Can anyone help me with LMMS install in ubuntu? I can install via software center but when installed there is no icon can anyone guide me in the right direction.

Also how do I use VST/VSTI with the software.

Thanks in advance

Ben

:D

---

### Post by Benjotter on 2011-10-02
Hi Just incase anyone else is in the same position and wants LMMS latest version with icon in sound and video folder.

Open terminal

sudo apt-add-repository ppa:dns/sound

sudo apt-get update

sudo apt-get install lmms

Thats all i did now it works perfect.

:P

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-08
the lmms.desktop file is missing from the package.

I made a file for it, though they may have fixed it by now...

open a terminal (or push Alt+F2) and type    lmms

or add this file by using the terminal and typing

cd Downloads (or where ever you save it too)

gksu gedit lmms.txt

then save it as

lmms.desktop 

in this folder

/usr/share/applications

---

