---
title: "Connecting a TV and Monitor"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by lilaundgelb on 2007-08-23
I'm trying to connect a LCD monitor (via VGA) and a TV (via S-Video) simultaneously. The native resolution of the monitor is 1024x768, and when the TV isn't connected everything works. When I connect the TV the only resolution becomes available is 800x600 running at 50Hz. This seems strange to me in particular because the monitor's range of refresh rates is 56-75Hz and I think the refresh rate of the TV should be roughly 60Hz.

I've tried various configurations with my xorg.conf file - creating separate screen/device/monitor sections for the TV, specifying the refresh rates, trying to run two screens in the serverlayout, creating a custom modeline - and I have the 1024x768 mode listed in all of my Screen/Display sections.

I'm running ubuntu/xubuntu 7.04 on a Via SP-8000E using the integrated graphics.

Has anybody gotten this working?

---

### Post by lilaundgelb on 2007-08-25
I tried compiling and installing Via's unichrome drivers. While this installed a spiffy application that let me check a "TV" box, I couldn't get my monitor to display at 1024x768 even without the TV attached.

Has anybody had any luck with Via's driver?

---

