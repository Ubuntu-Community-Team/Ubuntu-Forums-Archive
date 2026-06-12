---
title: "totem died when I reconfiged xorg.conf"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by grunge09 on 2007-08-19
I was happy go lucky with my xorg.conf and a 19" LCD.  I got a new 22" widescreen LCD and after some searching found the command: 

sudo dpkg-reconfigure -phigh xserver-xorg

I chose FGLRX and the resolutions I wanted and now I have them, but totem died.  it gives me (from the terminal) "Floating Point Exception".  I fixed that once before but I can not remember what I did to fix it.  

So I opened restricted drivers manager and unclicked the ATI Driver, and then re-clicked it and it reintalled FGLRX Drivers.  

I went to synaptic package manager and makred toitem and totem-xine for reinstallation, that did not help either.  

But the Totem player still gives F P E error.  

I am using 7.04 Ubuntu, AMD 4000+ X1 core, 1 GB DDR RAM, ATI Sapphire X850XT PCI Express Video Card, 250 GB SATA II HD.  

On'y thing that rings a bell is a l* something library was missing the last time, but I can not remember what.  Shoulda wrote it down I guess.

Anyone got an idea as to why Totem gives the FPE error?

---

### Post by RomeReactor on 2007-08-20
Hi. According to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xine-ui/+bug/82547"), the problem seems to come from the FGLRX drivers rather than from Xine. You might want to revert to the **ati** driver while you wait for someone to offer you a solution or a workaround.

---

### Post by grunge09 on 2007-08-20
I found a quick fix, not the right one mind you.  I edited the xorg.conf and changed where it says FGLRX to ATI.  and at least everything works for now.

---

### Post by grunge09 on 2007-08-20
Ok, I went back to FGLRX Drivers and used Synaptic Package manager to install VLC.  that works.  Totem does not.  

Kinda back where I started but at least I got my videos back.

---

