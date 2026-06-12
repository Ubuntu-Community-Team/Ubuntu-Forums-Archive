---
title: "Is this possible?"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by DarkN00b on 2006-10-06
I'm running an HP laptop with the integrated i855GME chipset. My problem is that this chipset is supposed to run @ 200 Mhz [Reference here]("http://www.intel.com/support/graphics/intel852gm/sb/cs-009067.htm?iid=search&"). 

Mine is currently running @ 33 Mhz according to lshw.

[This page]("http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html#sect7") seems to say that I can correct this via xorg.conf. My problem is that I can't get my head around how.  Can anyone help?

---

### Post by Aikon- on 2006-10-06
If your computer is running at all then I suggest you reconsider what these numbers are telling you. 33MHz looks like a PCI bus (it is, in fact, what PCI and AGP run at), whereas 200MHz looks more like a memory speed or FSB speed (without multipliers). Furthermore, none of this should be affected by Linux; its all hardware controlled.

I suspect that there is a miscommunication somewhere as to which numbers are what and being returned from where.

---

### Post by DarkN00b on 2006-10-06
Gotcha. I was just wondering. I'm not going to change an otherwise well-working system unless I'm *sure* what I want to do is going to work.

Trying to install compiz/beryl taught me that. I also learned to keep a working backup of xorg.conf and gdm.conf-custom just in case I need to replace files I had screwed up. ](*,)  :)

---

