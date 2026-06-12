---
title: "Dual monitor setup: Landscape + Portrait"
date: 2011-06-18
forum: Multimedia Software
---

### Post by dayzman on 2011-06-18
Hi,

I have a dual monitor setup with a nvidia card (8400GS). Can one of the monitors be set to landscape mode, while the other be set to portrait? According to the (rather old) posts I've read, it seems that this was possible only with xrandr, which doesn't support compiz. Is the situation any different now? Are ATI cards better in this regard? I just want 1 in landscape and 1 in portrait with compiz working.

Thanks

---

### Post by dayzman on 2011-06-21
Is the ATI driver supposed to be stable? If so, and that it supports 1x landscape 1x portrait, I'd be willing to get myself a Radeon card.

Thanks

---

### Post by BicyclerBoy on 2011-06-21
There are some warnings that using rotate may impact performance..don't know for sure.
Need to add this to the server section of xorg.conf file..(the exact section is not critical)[B]

Option             "RandRRotation" "on"
[/B]this enables the xrandr extensions& the options in nvidia-settings GUI[B].

[/B]Quoted from nvidia275 driver readme. chapter 17.
"Workstation RGB or CI overlay visuals will function at lower performance and the video overlay will not be available when RandRRotation is enabled.
You can query the available rotations using the 'xrandr' command line interface to the RandR extension by running:
     xrandr -q
You can set the rotation orientation of the screen by running any of:
     xrandr -o left
xrandr -o right
xrandr -o inverted
xrandr -o normal

Rotation may also be set through the nvidia-settings configuration utility in the "Rotation Settings" panel."

---

