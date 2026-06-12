---
title: "Getting Xorg back"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by Wolf359T on 2007-03-27
I've installed beryl following the guide from their website. Later, I've decided to remove it, so I did, but xgl still was used instead of xorg. I did a apt-get remove xserver-xgl but now, when I boot, GDM tries to find Xgl server and not xorg, so it crashes. I did a dpkg-reconfigure xserver-xorg, nothing. With startx as root, the X starts, but I want GDM to search and find xserver and start as it should be.
It's very frustrating that we have a beryl install guide, but not a proper uninstall one.

---

### Post by tseliot on 2007-03-28
can you provide me with the link to that guide so that I can see what you did?

---

### Post by Wolf359T on 2007-03-29
Well, it's done. After startx as root, I selected in the Xorg server in the GDM settings window, not the Xgl, now it works fine :)

---

