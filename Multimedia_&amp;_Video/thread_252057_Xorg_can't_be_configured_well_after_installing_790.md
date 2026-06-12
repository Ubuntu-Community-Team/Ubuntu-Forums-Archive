---
title: "Xorg can't be configured well after installing 7900GT"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by Malta Soron on 2006-09-06
Hi everyone,

I just installed a new videocard, a Leadtek 7900GT. On Windows (I dualboot WinXP and Breezy) it runs fine (I tested it), so I booted Breezy and started reconfiguring X.org. However, X doesn't want to start. This is the last part of the error message:

```
(II) VGA: Generic VGA driver (version 4.0) for chipsets: generic
(II) Primary Device is: PCI 05:00:0
(WW) VGA: No matching Device section for instance (BusID PCI:5:0:0) found
(EE) No devices detected
```

The device section of xorg.conf reads:

```
Section "Device"
     Identifier   "Generic Video Card"
     Driver       "vga"
     BusID        "PCI:1:7:0"
EndSection
```

I tried the vga, vesa and nv driver, but none worked.
As you can see it tries PCI:5:0:0, while it's configured to PCI:1:7:0 (which is the address the reconfiguring wizard gave me when I started it the first time). I tried setting it to 5:0:0, but that didn't help either.
I also tried different settings for the framebuffer and the DRI entry.

Do you have an idea how I could get this working? Please react quickly, for I'm in a bit of a hurry.

---

### Post by Malta Soron on 2006-09-06
I now think that the BusID just isn't right. Do you know a way to detect the right one?

EDIT: From what I gather from Everest it should be 5:0:0. I'm going to try and set that.

---

### Post by Malta Soron on 2006-09-06
I managed to fix it by editing /etc/X11/xorg.conf with vi and changing the BusID to 5:0:0.

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:5:0:0"
EndSection
```

---

