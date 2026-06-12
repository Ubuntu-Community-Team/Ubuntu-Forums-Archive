---
title: "Help me set up my Netgear wireless N router &amp; dongle - I'm totally clueless"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by PsychedelicWonders on 2009-10-10
Ok guys I need to set up Ubuntu with my Netgear wireless n router & dongle. 

I'm totally clueless. What's my first step?

---

### Post by ajgreeny on 2009-10-10
For the router, you probably need to open Firefox and in the addressbar enter [http://192.168.0.1](http://192.168.0.1) and then just follow the instructions in the manual that came with the router, or that will probably be in pdf form or html file on the CD for it.

For the dongle it will depend on which dongle it is, but it could need ndiswrapper, which will need you to get the windows driver .inf file from the driver CD.

Let's have more details and we may be able to give you more help.

---

### Post by PsychedelicWonders on 2009-10-11
Ok hopefully this will help:

Router: WNR2000
Dongle: WN111

I think I do need that ndiswrapper dont I?  It kinda looks familar as if I've read about it recently with the router.

How do I get that driver off the cd & into Ubuntu to use & activate the dongle?

---

### Post by ajgreeny on 2009-10-11
The dongle CD, not the router CD, will probably have a number of folders for various windows versions somewhere in its file system.  Use the XP version and look inside.  There will probably be about 4 or 5 files including a .inf, .sys and .cat.  Copy those, in fact all the folder to your ubuntu and then in the ndis-gtk window navigate to the .inf file and use that.

You may need to install ndis-gtk to do all this, but it is easy once you have it.

---

