---
title: "nvidia-settings and Gnome show different refresh rate"
date: 2008-06-18
forum: Multimedia Software
---

### Post by attercop on 2008-06-18
NVIDIA X Server Settings is showing my refresh @ 60Hz as it is written in my xorg.conf.

However Gnome is showing the refresh rate @ 50Hz in the Screen Resolution, with no other option.

Which one is telling the truth here?

Edit: I can use the DynamicTwinView 'False' option in xorg.conf to make Gnome Screen Resolution show 60Hz. But this then stops X Server Display Config working in nvidia-settings.

Info:
DVI to VGA connection.
Nvidia proprietary driver.
Hardy
1360x768@60 native display

---

### Post by kaibob on 2008-06-18
> **attercop said:**
> NVIDIA X Server Settings is showing my refresh @ 60Hz as it is written in my xorg.conf.

However Gnome is showing the refresh rate @ 50Hz in the Screen Resolution, with no other option.

Which one is telling the truth here?

My situation is the same, and it's been that way as long as I can remember. My monitor shows that it's operating at 60Hz, and everything looks fine, so I don't worry about it.

---

### Post by Pjotr123 on 2008-06-18
The restricted Nvidia driver uses fake Hz values, in order to uniquely identify a screen: 50 or 51 Hz. The real Hz value is different and can be checked in the BIOS of the monitor itself (if you have a separate monitor and not a laptop). Use the physical buttons on the monitor for this.

So indeed: don't worry, it's allright. But confusing it is: about a year ago, I've had an e-mail exchange with an Nvidia service employee about this. It appears that Nvidia blames Ubuntu. Whereas the Ubuntu developers blame Nvidia. Anyway, it's only a cosmetic issue and has no intrinsic importance.

Greeting, Pjotr.

---

### Post by ZarathustraDK on 2008-08-14
I have the same problem, and there is a visible difference.

If I apply 1440x900 resolution at 60 Hz in nvidia/settings movemoent of windows are visibly smoother than if I just stick with the 50-51 Hz gnomes screen/resolution app suggests.

---

