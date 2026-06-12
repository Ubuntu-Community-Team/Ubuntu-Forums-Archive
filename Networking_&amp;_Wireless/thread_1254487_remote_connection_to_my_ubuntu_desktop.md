---
title: "remote connection to my ubuntu desktop"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by masterchief1995 on 2009-08-31
I am using VNC viewer to connect to my Ubuntu desktop from school. I can connect, but it just shows me the image of the desktop. I can control the dekstop, but it does not show it on the screen.

Any help would be greatly appreciated!

EDIT: My goal is to have VNC viewer on my flash drive so i can plug it in and connect to my desktop. It works but it's not showing what i'm doing on the screen

---

### Post by jonandrews on 2009-09-02
Mmm.  This problem rings a bell with me, but I cannot remember the details.  I use vnc around my multi-os network. I have found some cryptic notes I made at the time which may be of a little help to you.  They say:

Implementing VNC on Ubuntu  904. 
A bug means that in System > Preferences > Appearance  > Visual Effects, VNC will only display properly if None is selected.

NB – No change to the default Ubuntu firewall was needed 
Vinagre is the default VNC server in Ubuntu to share your existing desktop. Works fine in 8.10.
To configure Vinagre from within GNOME, go to System > Preferences > Remote Desktop 
  

Good luck....

---

