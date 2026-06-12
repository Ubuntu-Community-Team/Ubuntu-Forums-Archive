---
title: "Graphics Driver Problems"
date: 2008-06-18
forum: Multimedia Software
---

### Post by hellaid on 2008-06-18
I'm currently getting problems with my graphics card, an Nvidia 7300gs, and i've had poor gaming graphics from it since installing ubuntu, I've tried searching these forums for people with similar problems and found about the Envy program which helped to a certain extent, but it is still not how it should be i feel.

I've attached 2 screenshots, 1 of the game in windows and the other in ubuntu, straight away you should be able to see that the colours on the ubuntu version doesn't look as they should, another thing i get is lines across the mouse cursor in game on ubuntu.

Any help solving these problems would be appreciated

---

### Post by Pjotr123 on 2008-06-18
Disable the 3D visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

---

### Post by hellaid on 2008-06-18
I've tried that, unfortunaly it doesn't make any difference, (trying to get whats displayed on the first thumbnail the same as the second)

---

### Post by Pjotr123 on 2008-06-18
Are you sure the card is running on the restricted driver? It should run on the restricted driver for best performance.

You mentioned the use of Envy. Envy provides the latest version of the restricted driver: the version in the Ubuntu repositories is usually an older version. However, if the card *can* run on the older version in the repo's, then that's always preferable. Tested for stability in Ubuntu.

You can try it like this:
- disable the restricted driver in the Envy version
- reboot
- System - Administration - Hardware Drivers
now you can install the repo version of the restricted driver.

---

### Post by hellaid on 2008-06-18
I believe i did that before i tried Envy, it was even worse, I am running cedega to use the program could it be that theres a problem with that?

[edit] Just went into the game and change the settings to performance seemed to fix the bug although i am still getting a Cursor with lines through it.

---

