---
title: "Strange keyboard/mouse issue"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VeeDubb on 2010-09-12
I'm having a really strange issue with my keyboard and mouse since upgrading to 10.10 64bit.

I'm using a Microsoft (don't hate, the sell great keyboards) Wireless Comfort Keyboard 5000.

This particular wireless keyboard comes with a matching wireless mouse, and they share a single USB transceiver. I have used it for some time without issue on 9.10 and 10.04.

What happens under 10.10 is that whenever I press any of the "extra" keys on my keyboard (volume, calculator, home, play, etc) Ububntu thinks that I am clicking an holding the left mouse button as well.  

The only way I can get my desktop to recognise that I'm NOT holding down the left mouse button once this happens is to unplug the transceiver and plug it back in.  Obviously, this makes all the media and special keys on my keyboard not only useless, but a real inconvenience to even have where I might hit one on accident.



ALREADY TRIED: changing keyboard profiles, changing keyboard batteries, changing mouse batteries, creating a new user with a clean profile in case it was a user setting, plugging the transceiver into a different USB port.

---

### Post by VeeDubb on 2010-09-14
Just a bump here.  I'm a little surprised that no other tester has experienced a similar issue.

---

### Post by Somatik on 2010-09-24
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311)

---

### Post by VeeDubb on 2010-10-08
The bug report feedback has certainly taken off like a rocket in the last couple days on this one.  Hopefully it will get fixed soon.

---

