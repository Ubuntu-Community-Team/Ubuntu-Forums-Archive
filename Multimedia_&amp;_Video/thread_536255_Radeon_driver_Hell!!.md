---
title: "Radeon driver Hell!!"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by ghstzr0 on 2007-08-27
Hello!

I am having trouble getting the open-source radeon drivers working with my X1250...

Simply stated, my system specs are:
ASUS M2A-VM HDMI mobo with integrated Radeon Xpress 1250 chipset
AMD 6000+
2GB RAM
... blah blah

The point is, XORG will not detect my card as a valid device when I try to use the radeon driver.  XORG crashes with a "No screens found" error.

Just FYI:  my card's pci bus id is 1:05:0, not 1:00:0 like usual...

Can I force the card to be used with the driver even if it doesn't detect it???

This is really frustrating, please help!!!

---

### Post by ghstzr0 on 2007-08-27
Bump

---

### Post by ajgreeny on 2007-08-27
Try **sudo dpkg-reconfigure xserver-xorg** and when you get to the graphic driver part select ati instead of radeon.  If you've already tried all of this my apologies, but you don't give any clue as to what you have already tried.

---

### Post by ghstzr0 on 2007-08-27
Sorry for not being clear.

I have tried all manner of getting the driver to work.  I am most positive that it is not a matter of me not correctly specifing the driver in xorg.conf (I am NOT a n00b to Linux or Ubuntu, and am infact a senior in computer science -- just so you know where i'm coming from).

The problem appears that the damn X1200 series cards are a mystery.  NO ONE seems to have a clue what kind of chip they actually are (R500?) or what driver works with them (radeon? avivo? fglrx only?).  I can't believe I am the only one having this problem... (I have been posting in this forum for weeks; no solutions at all!)

FYI: I CAN get fglrx to work fine, but I HATE XGL with a burning passion!

---

