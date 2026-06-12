---
title: "Installing D-Link DFE-538TX ethernet card manually."
date: 2005-03-05
forum: Networking &amp; Wireless
---

### Post by pin on 2005-03-05
Hello folks.  I am pretty new to Linux, though I have some ArchLinux experience, and I need help installing my card.  The installer didn't recognize my card, but everything else seemed to go smoothly with my Warty install on my AMD-K6 system.

Apparently all I need is to invoke the 8139too driver, yes?  Problem is, I don't know how to go about doing that.  I can't find a modprobe.conf or even an rc.conf.  Can someone walk me through the whole process of getting this card to work, step by step?

It would be appreciated.

Cheers.

---

### Post by pin on 2005-03-06
This is what I've tried:

I went into /etc/modutils/aliases and added the following line to the end,

alias eth0 8139too

and then ran update-modules; it didn't complain to me.

Just for kicks, I created /etc/modprobe.conf and put the same line in there, and then ran $ modprobe eth0, and got no information.

$ ifconfig -a

does not reveal eth0, so, none of this has worked.

---

### Post by pin on 2005-03-11
Okay...

I figured out why the card isn't read (probably).  It's a hardware failure on my box.  Nevertheless, I'd still appreciate it if someone could point me to a good tutorial on how to add modules manually in a Debian system.

Cheers.

---

