---
title: "How do I install a proprietary video driver?"
date: 2010-01-23
forum: Multimedia Software
---

### Post by idkwtf on 2010-01-23
I'm running a slightly upgraded Dell Inspiron B120 with 2 Gig RAM, 200 Gig HD.  I recently switched this laptop from XP to Ubuntu 9.10.  After many a long hour, I was able to get World of Warcraft running under wine but its slow to the point of being unplayable.  I was used to slow gameplay on this laptop under XP, but 0 fps is a new low.  Dalaran (the notoriously laggiest place in the game) is a joke.  Theres a 5-10 sec lag between hitting the button to move and actually going anywhere.  I took all the video settings down to the minimum and did a regedit to add a key for wine.  Basically I tried all the tips and tricks I could find (including creating an xorg.conf file since I didn't have one).  Nothing I did worked.  I can be in the most remote, unpopulated spot in the game and I can't get more than 3fps.  Somewhere I read that I should install a proprietary driver for my video card (intel GMA 900).  So I went out and downloaded xf86-video-intel-2.10.0 and ran the configure script that came with it.  It came back and said 
```
No package 'xorg-server' found
No package 'xproto' found
No package 'fontsproto' found

```so I went out and found Xorg-Server-1.7.1 and ran its configure script which gave me
```
No package 'x11' found
```I tried setting $PKG_CONFIG_PATH to /etc/X11/ with no joy.
Now I am new to linux but in poking around the file system I did see /etc/X11/ which had some stuff in it.  To me that says that I've got X11 installed but then again I've been using linux since breakfast so what do I know?  

The bottom line:  what do I need to do to install a proprietary video driver -OR- what can I do to get the game running well enough to be playable (short of walking over to my windows desktop computer)?

Thanks very much!  :D:confused::D

---

### Post by tgeer43 on 2010-01-24
Not to oversimplify but have you checked in System->Administration->Hardware Drivers to see if there is a proprietary video driver for your card listed there? If so, then this is the easiest and safest method to get it installed correctly.

tgeer

---

### Post by idkwtf on 2010-01-24
> **tgeer43 said:**
> Not to oversimplify but have you checked in System->Administration->Hardware Drivers to see if there is a proprietary video driver for your card listed there? If so, then this is the easiest and safest method to get it installed correctly.
 tgeer
 
Yes I did.  Nothing in there.  Where would I go to view the driver that is currently in use?

---

### Post by idkwtf on 2010-01-24
should this thread be in another category?  It kinda fits Hardware/Laptop and Installation/Upgrade...  Wasn't sure where it should go.  Thanks

---

### Post by SmarterThanMyPhone on 2010-03-08
same problem trying to install drivers for my intel945... booo
missing the x11 package.


installed libx11-dev from synaptic and that got it running.

---

### Post by wobin77 on 2010-04-03
I m finding it hard to understand how to do this whole new install for my intel graphics driver. If someone could explain this in 'human' language? 
I read [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html) , but it leaves me with more questions than answers.

---

### Post by lidex on 2010-04-03
With video drivers it's best to uninstall old drivers and remove xorg.conf and reboot, then install new drivers. You may get good results using one of the xorg PPAs to update rather than manual install anyway.

Open a terminal ("Applications>Accessories>Terminal) and enter this command:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```
Now this:
```
sudo apt-get update
sudo apt-get upgrade
```
Reboot.

---

### Post by wobin77 on 2010-04-04
Hi, after doing this Ubuntu boots, but after the ubuntu logo my screen gets filled with strange colors and lines. 
Looks like some kind of problem with the video driver? 

Thanks in advance for your help!

---

### Post by lidex on 2010-04-04
Try this in a terminal:
```
sudo mv /etc/X11/xorg.conf xorg.old
```
and reboot

---

### Post by wobin77 on 2010-04-04
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory


this is the output.

---

### Post by thdn on 2010-06-11
Any solution i have the same problem : 

[B]
checking for XORG... configure: error: Package requirements (xorg-server >= 1.6 xproto fontsproto  randrproto renderproto xextproto x11 xextproto) were not met:

No package 'x11' found
[/B]

---

