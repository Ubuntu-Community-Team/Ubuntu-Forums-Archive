---
title: "Yikes!  Moved my video card to a new slot and...no X!"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by phillywize on 2007-11-22
Ok, so I was doing some work inside my PC, and it included moving the graphics card (nvidia geforce 8500 gt) from one PCI-e slot to another.  Little did I know that this would cause linux to boot to a TTY login!

After a little head scratching, I realized that moving from one slot to another was probably the culprit.  lspci gave me the new PCI bus ID, and I changed it in xorg.conf:  under

Section "Device"

Busid      "PCI:3:0:0"               became...
Busid      "PCI:1:0:0"

...and no more tears.  Easy enough, but an unexpected trip-up.

So, not to be a troll, but I think this might be an area where our camp could stand to play a little catch-up with Windows.  Complain all you want.  I'd bet dollars to donuts that Windows would almost certainly have scanned the PCI bus when it didn't find the adapter in the usual slot, and made the change itself -- without so much as a hiccup.  Well, ok, maybe it would hiccup...  But I'm not the most sophisticated linux person, and it was just a matter of dumb luck that I knew to use lspci and to edit xorg.conf.

---

