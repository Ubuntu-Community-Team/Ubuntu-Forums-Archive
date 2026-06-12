---
title: "Which wifi card works out of the box with 64 bit ubuntu?"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by kramer2718 on 2009-02-23
Hi.  I'm putty together a new desktop which will live from from any ethernet wiring.  Thus I need a wifi card for it.  I'll probably go for a pci card (must be faster than usb right?).

I'd like one that works right out of the box and saw that there were several pages that detailed compatibility for various cards.  Unfortunately, most of those pages neglect to mention which cards work with 64 bit Ubuntu and which cards support WPA under Ubuntu (and let's be serious--if a card doesn't do WPA under Ubuntu, then it doesn't work with Ubuntu).  Cheaper is better, but I'd also be willing to pay to not have headaches trying to set it up.

Any help would be much appreciated guys.
Oh, and not that it matters, but I'll probably be installing Ubuntu server and then kde on top of it.

---

### Post by Reiger on 2009-02-24
Atheros (ath5k) cards, Intel (iwlxxxx) cards, Ralink (rtxxxx) cards. But there are always exceptions... Of course if you consider it good enough for a temporary (or permanent) solution you can  use ndiswrapper with an XP driver. That should work with a very large range of trickier cards 'out of the box' since Ubuntu Intrepid comes with built in ndiswrapper IIRC.

---

### Post by kramer2718 on 2009-02-24
What do you mean by always exceptions?  That some Intel or Atheros card won't work?

---

### Post by Reiger on 2009-02-24
Well, Intrepid+ath5k should work for an ar5007eg card 'out of the box'; but it turned out that it didn't for me (which was after an upgrade from Hardy, though). (Required removing certain backports and installing packages from compat.wireless.org.)

---

### Post by kramer2718 on 2009-02-25
Okay.  Thanks.

I sure wish device manufacturer would start writing more native Linux drivers.  Even unsupported ones...

---

### Post by MockY on 2009-02-25
The more people starting to use Linux, the greater the interest gets for writing native Linux drivers. Unfortunately, currently most vendors don't give a flying bat about Linux, but I sure hope that trend soon changes.

---

