---
title: "How to scale (down) the display"
date: 2011-01-08
forum: Multimedia Software
---

### Post by nakednous on 2011-01-08
Hi,

I have an Asus N53JQ running kubuntu 10.10 (amd-64) with nvidia propietary driver and with a 1366x768 screen resolution and want to connect an external full-hd monitor (1920x1080 resolution) in twinview clone mode using an hdmi cable.

I can easily configure the external monitor at any resolution (including 1920x1080) using nvidia-settings, but I have two issues:

1. I cannot configure separately the two resolutions even though the nvidia-settings allow to do it. It seems that the monitor with higher resolution takes precedence on the other. Ideally, I'd like to have both displays at is maximum resolutions. However, I can live without it, but then it comes the other issue.

2. I cannot make the external monitor to display a correct image. It just scales badly at any resolution: the displayed image is larger (say 5%-10%) than the physical display size.

I'd be very happy if I just can scale (down) the display so that it fits correctly on the external monitor. If that is possible I'd want to know how to do it.

Any hint is appreciated. Cheers,

Jean Pierre

---

### Post by efflandt on 2011-01-08
In **NVIDIA X Server Settings** for your DFP or CRT under your GPU there should be an **Overscan Compensation** setting.

Although, my LG HDTV has a setting called "just scan" that perfectly sizes 1080p, 1360x768, or 720p to match the screen, so I do not have to use that nvidia setting.

---

### Post by BicyclerBoy on 2011-01-08
Don't use twinview & the problem will go away.
Use separate X screens. Better video mode independence etc.

Do not use overscan control if high PQ is required.
No overscan & configure the TV display to use the modes just-scan/direct pixel mapping/PC input.

PC mode may change the colour-space to PC RGB.

Twinview may work if you allow the meta-display to be (1366+1920) x 1080 and have panning on small display.

---

### Post by nakednous on 2011-01-09
Overscan compensation using twinview (clone) did the trick. Thanks!

I wasn't able to make both resolutions properly work at the same time. Would it be possible with separate x screens? How? I didn't understand. I also want to clone the external monitor which seems not possible using separate x screens.

Cheers,

Jean Pierre

---

### Post by BicyclerBoy on 2011-01-09
Sorry.
Did not see the clone requirement..
Don't know how to clone  without using twinview.

Separate X screens let you do anything except put icons on the 2nd desktop.
(I swear it did with 8.04)

Should not be any need for overscan adjustment with DVI/HDMI.
Usually points to incorrect TV setup (IMHO).

---

