---
title: "Second monitor not detected through KVM switch."
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by mcgirvanmedia on 2007-06-21
I am running Ubuntu 7.04 and am using the binary nvidia driver with two screens in twinview mode.

I have recently installed a KVM switch, and ever since the second monitor is not detected at startup. If i connect the monitor directly to the machine and startup, then route it through the KVM switch, it works fine.

If there any options for the binary driver where i can force it to use two monitors so the KVM switch will not effect things?


Regards

Glen

---

### Post by Disstress on 2007-06-21
Thats the thing about a KVM switch, its not really connected until you flip the switch.
So there is no way to install it without manually doing it or having it "switched on" at startup.

You don't use a KVM switch for dual monitors, use the DVI port on your video card or use two video cards (IE mainboard IGP or a second apg//pci/pcie card).

---

### Post by mcgirvanmedia on 2007-06-21
> **Disstress said:**
> Thats the thing about a KVM switch, its not really connected until you flip the switch.
So there is no way to install it without manually doing it or having it "switched on" at startup.This problem occurs even when it is switched to that current port. I suspect that the KVM switch is allowing all the video lines through but not connecting the DDC DAT line.

> You don't use a KVM switch for dual monitors, use the DVI port on your video card or use two video cards (IE mainboard IGP or a second apg//pci/pcie card).I am aware of this. I have two monitors connected to my machine, the DVI is connected perminantly and the VGA monitor is router through the KVM switch, so i can access my other machines using the second monitor and the keyboard and mouse.

---

