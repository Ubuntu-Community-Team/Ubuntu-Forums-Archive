---
title: "tweeked my x1300 to a black screen"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by mistermax on 2007-06-21
hi-

I finally got the nice driver to work and noticed the effect immediately in terms of my desktop (fonts better, edges smoother etc). However, the fglrxinfo command still returned the mesa driver as the renderer.

So I followed the instructions here:

[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

interetingly the command 

sudo echo fglrx >> /etc/modules

didn't work, complaining about permission although I had sudo'ed.

and then tried disabling AIGLX as listed here:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Anyway, now it is a black screen on restarting X... I've tried repaling my old trusted xorg.conf and restarting (and even rebooting), but so far, no luck...


Any suggestions are most welcome!

---

### Post by mistermax on 2007-06-22
Another thing that strikes me - I have two back up xorg.conf files. One has composites disabled (definitely worked) and the other enabled (worked until I started tweaking...)

I'm not at my machine currently, but I'll get my bash history and post it up also.

---

### Post by Kubunteando on 2007-06-22
Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

------------------

It seems you have to graphic cards?
If not, you have 2 entries as "Device", and in the second one the BusID is missing.
I would delete the second "Device" entry, and I would replace in the first one the Driver "vesa" with Driver "fglrx",

If that does not solve the issue, post your /var/log/Xorg.0.log

---

### Post by mistermax on 2007-06-23
That didn't do it... here are my logs.

(quick edit, just remembered I have to rename to txt files...)

---

### Post by aznranndydraman on 2007-07-01
same issue here with a x1300 128MB. right now I'm trying to uninstall restricted modulos, fglrx and any mesa packages. will update you with results.

---

### Post by applefreakpeeps on 2007-07-02
Try with the latest ATi driver.. solves a large number of such blacking out problems..

---

