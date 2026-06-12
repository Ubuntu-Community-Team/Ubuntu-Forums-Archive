---
title: "HD3000 colour space over HDMI"
date: 2013-04-27
forum: Multimedia Software
---

### Post by d!ck-t on 2013-04-27
Specs:

Asus N53SV
Core i7-2630QM (w/HD 3000 integrated)
Nvidia GT540M 1GB (Optimus switching enabled via Bumblebee)

Connected to:
Samsung S24B350 24" 1920*1080 with HDMI

I have Bumblebee working and the Intel graphics pick up the Samsung monitor fine, and select the correct resolution. However, it appears that the Intel card is outputting a signal in YCbCr colour space instead of RGB, which means I have to adjust the monitor's HDMI black level to 'Normal' (16-235) instead of 'Low' (0-255) to avoid washed-out colour (which, incidentally, looks similar to the colours on my HP dm1 with the AMD Vari-Bright feature switched on - not sure if there is any connection here). In windows, there is a settings applet I can use to switch between YCbCr and RGB colour spaces, and the default is RGB. However, I can't find anything similar in Ubuntu, and I'd prefer to utilise the full 0-255 black levels.

Is there something I can change in some settings file somewhere to make the Intel graphics output RGB?

---

