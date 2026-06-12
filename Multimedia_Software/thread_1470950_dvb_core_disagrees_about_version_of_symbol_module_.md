---
title: "dvb_core: disagrees about version of symbol module_layout"
date: 2010-05-03
forum: Multimedia Software
---

### Post by Galdrapiu on 2010-05-03
Hello ...

I upgraded my system from Ubuntu 9.10 to Ubuntu 10.04 (Lucid Lynx).
Since then my dvb-c (Terratec Cinergy C PCI HD) 
card is no longer running.

$ dmesg | grep dvb  
dvb_core: disagrees about version of symbol module_layout"

$ lspci | grep Multimedia 
03:04.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)

What I got out from different forums is that I need the dvb mantis driver,
and that this dvb mantis driver is **not yet** included in 2.6.32-21 (Ubuntu 10.04).
(Will be in 2.6.33)

So I had to build and install the **v4l-dvb** modules from here
[http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/)
(I used this explanation [http://wiki.ubuntuusers.de/v4l-dvb](http://wiki.ubuntuusers.de/v4l-dvb))

But the "dvb_core: disagrees" problem is still there.

Anybody has an idea?


Galdrapiu

---

### Post by byronmyth on 2011-01-07
Can you let us know "how" it was solved? I've had a similar problem since an upgrade over xmas that I'm struggling to get to the bottom of. Cheers.

---

### Post by guysoft on 2011-01-08
Same problem here - can you tell us how you solved it?

---

