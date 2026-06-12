---
title: "Random Video Distortion"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by tristan_koen on 2006-12-20
Hi All

I am using an nVidia FX6200 video card with an Acer AL1914 flat screen monitor. Unfortunately, the monitor doesn't have a DVI input so I am forced to use an old analogue video cable.

I was running Edgy with the latest nVidia drivers. The problem is very weird. At random intervals, I will get a lot of random noise on my monitor, and sometimes some serious flickering and lines across the screen. The problem can be corrected 99% of the time by stitching the monitor off and then on again.

My first reaction was that there was something wrong with my monitor. The weird thing though, is that I don't have the same problem if I boot up into Windows. I also recently replaced my Ubuntu installation (temporarily) with Fedora Core 6 since it supported the Freebob audio drivers out-of-the-box (waiting for Feisty).

The problem also doesn't show up on FC6.

The other bit of weirdness is that my screen always jumped around a lot when switching resolutions and didn't seem to be able to keep the settings (vsync, hsync, etc) from the previous time. This problem also doesn't manifest itself in Windows or FC6.

I manually edited xorg.conf and inserted the correct refresh rates for my monitor. I also tried different monitor frequencies to no avail.

I plan to go back to Ubuntu when Feisty is released, but the screen problems are very annoying. Any suggestions on the cause, or any possible solutions out there?

Thanks

---

