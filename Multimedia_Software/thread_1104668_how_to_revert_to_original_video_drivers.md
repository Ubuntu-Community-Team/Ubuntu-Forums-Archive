---
title: "how to revert to original video drivers?"
date: 2009-03-23
forum: Multimedia Software
---

### Post by supdewds on 2009-03-23
I have a t41 thinkpad with ati radeon 250 mobility firegl 9000 rev 02 video card.  The original install of Intrepid left the video settings automatically detected and working fine, except no 3D support.  I stupidly tried to upgrade to 3D this afternoon with no success, which I think is because the drivers have not been developed, or maybe because my version of Xorg is too recent.  Either way, I have grown tired of ******* with it, because nothing seems to work, and would like to revert to the original settings.  Specifically, I would like my screen to display at more than 800X600.  Right now it is using the vesa drivers, and these are pretty lackluster.  Is there a way to revert to the original settings without reinstalling?

---

### Post by supdewds on 2009-03-25
bump

---

### Post by overdrank on 2009-03-25
You may try the xfix option when boot into recovery mode. Recovery mode is usually the second choice from the grub when booting. Then you should be given 4 options and the last is xfix. When xfix is complete you should be given the options again and you can choose to boot normally.

---

