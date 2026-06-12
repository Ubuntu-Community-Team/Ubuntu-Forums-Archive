---
title: "Problems with graphics"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by Caifan on 2007-08-09
Hi all the Ubuntu comunity!

I'm new on the formus. I'm here 'cause i'm also kinda new on Linux, and i got some issues that won't let me install Xubuntu Desktop 7.04 i38 on my computer.

When i boot from the disk and i choose the option "start or install Xubuntu ", the systems seems to start loading (with the Xubuntu logo and a progress bar filling), but after this, suddenly my monitor goes black with a message saying this:

out of range
H: 74.9KHZ
V: 59HZ

Then nothing happens, my monitor turns off and i have to reboot my computer pressing the restart button.

A friend told me that this happens 'cause my monitor is old (CRT), but right now i can't buy a new one.  Should i have to modify something on command-line mode before continuing? If so, what?

The info about my monitor: DAEWOO DE DCR-170RB
VIA/S3G UniChrome Pro IGP

Hope someone can help me 'cause i really want to install Xubuntu. 
Thank you.

---

### Post by bjarneh on 2007-08-09
your friend is right, your CRT probably doesn't support the refreshrates that X tries to start off with..

not sure if there is a "NO X"- option during install of Ubuntu?

if there is, this is what you want to try out, then modify your xorg.conf later

$ sudo dpkg-reconfigure xserver-xorg

try out a low refresh-rate and see what happens, if it is too low you'll probably get some sort of seizure from the flickering but atleast you'll have Ubuntu :-)

---

### Post by Caifan on 2007-08-09
Thank you.

Well, in the installation, or i mean, before, there's an option to change the resolution, but i already tried it and it didn't work.

---

