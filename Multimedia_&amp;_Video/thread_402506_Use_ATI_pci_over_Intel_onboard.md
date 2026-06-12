---
title: "Use ATI pci over Intel onboard?"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by Mochtroid-X on 2007-04-05
I'm currently tying to use my ATI Rage 128 PCI card over my Intel 82810 built-in card and having no success. I have tried using dpkg-reconfigure -phigh xserver-xorg but when I boot up it only gives me the blue screen saying X could not be started. Changing the video settings in bios does nothing to help this. I have also tried modifying my xorg.conf but without success. Anyone have ideas?

---

### Post by DougieFresh4U on 2007-04-05
> **Mochtroid-X said:**
> I'm currently tying to use my ATI Rage 128 PCI card over my Intel 82810 built-in card and having no success. I have tried using dpkg-reconfigure -phigh xserver-xorg but when I boot up it only gives me the blue screen saying X could not be started. Changing the video settings in bios does nothing to help this. I have also tried modifying my xorg.conf but without success. Anyone have ideas?

Hello. I feel your pain with the Intel i810 as I am stuck with it  :(  Maybe this is way off topic, but I was having no luck getting Direct Rendering to work until I changed color depth from 24 to 16 and now I have 3D and Direct rendering and I didn't have to change graphics card, but you may want to do more with your machine thus the ATI Rage

---

### Post by Mochtroid-X on 2007-04-05
Yes, my i810 is already set to 16-bit and I cannot play any games that require 3D acceleration. I was planning on installing the card earlier and playing Tremulous online with a friend but it seems Intel doesn't want that...

---

### Post by Mochtroid-X on 2007-04-06
-bump-

I think I found a guide that can help me, but I need to know is what busID I need to enter in xorg for my card. Entering lspci in Edgy shows this for the Intel i810 and Rage 128:

```

00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)

01:0e.0 VGA compatible controller: ATI Technologies Inc Rage 128 PP/PRO TMDS [Xpert 128]

```
I notice the 01:0e.0 for the Rage but I'm not sure what to enter for the busID. I noticed the i810 hows up as 00:1.0 in lspci and as "PCI:0:1:0" in xorg. For the Rage's 01:0e.0 could I put "PCI:1:1:0" for the busID?

-edit-
I got it working. Didn't have to worry about the busID at all since commenting it out made it work. Thanks for the help anyhow.

---

