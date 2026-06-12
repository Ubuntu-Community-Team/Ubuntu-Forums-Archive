---
title: "A fix for some of the xserver-xorg-video-intel crashes"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Captain Goatse on 2011-04-13
The latest commit[1] disables something for some cards, applying the change[2] allows me to use the intel driver without constant crashing.  It also fixes the graphical corruptions.

[1] [http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=686018f283f1d131073ef5917213e6a8ac013f26](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=686018f283f1d131073ef5917213e6a8ac013f26)
[2] I set intel->has_relaxed_fencing to 0.

---

