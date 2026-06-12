---
title: "ubuntu doesn't load X, only command line"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by vugh on 2007-08-11
my ubuntu feisty's GUI doesn't load. i get the command line.

it's probably because i removed my video card (nvidia) and switched to the on-board video. my nvidia card needs to be replaced but i don't have the money yet.

i have important files in ubuntu and i don't know command line. im new to ubuntu.

any help with being able to start X again? im using windows now. dual boot.. help??

---

### Post by regomodo on 2007-08-11
in the command line (either you are there already or press ctrl+alt+f1), log in and type 

$ sudo dpkg-reconfigure xserver-xorg 

and go through the screens

If that doesn't work

$ sudo dpkg-reconfigure -phigh xserver-xorg

which i believe is the safe graphics setup

(don't actually type the $ signs)

---

### Post by vugh on 2007-08-11
amazing! thank you!!!!!

too bad i can't use beryl anymore hehe... thanks again!!!

---

### Post by jon80 on 2008-04-02
I've had a similar problem, when I typed:

sudo dpkg-reconfigure -phigh xserver-xorg, I got:

/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed.

Any idea how to get the GUI up?

:confused:

---

