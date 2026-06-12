---
title: "Auto Detect VGA and switch Monitors."
date: 2010-07-31
forum: Multimedia Software
---

### Post by mazki516 on 2010-07-31
Hi All!
I've HP DV 2000 laptop.
I'm trying to find out how to make my ubuntu to auto switch monitors when I connect my lcd into the vga plug and also switch the desktop bars into the new monitor and also use the laptop screen as a side screen.
In setting I can turn off my laptop screen and i'll see only on the lcd screen, but I need to configure it first, I want it to be automatically and when i plugged out the lcd it's back to normal.
any body have an idea?
where i can find the source code that trigger the auto-detect vga plug and make it do my wishes...
Thank you all in advance guys!
Amit.

---

### Post by nocnokneo on 2011-06-11
Also interested in this. So far, all I've found is [bug #306735]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/306735") which was marked invalid - the rational being that it is a known problem but fairly complex and far-reaching and therefore would be better tracked using the blueprint mechanism. But marking that bug as "affects me" can't hurt.

---

### Post by nocnokneo on 2011-06-11
Actually, looks like [autorandr]("https://github.com/wertarbyte/autorandr") may be the answer according to the comments from this askubuntu question:

[http://askubuntu.com/questions/7292/...s-disconnected](http://askubuntu.com/questions/7292/...s-disconnected)

---

