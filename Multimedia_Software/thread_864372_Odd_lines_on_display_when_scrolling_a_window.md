---
title: "Odd lines on display when scrolling a window"
date: 2008-07-19
forum: Multimedia Software
---

### Post by rkent on 2008-07-19
When I scroll up or down within a window (e.g. Firefox or kpdf), I see horizontal lines appear within the window at the left and right edges.  If I cause the window to refresh somehow, such as by minimizing and restoring, they are gone.  Oddly, this only happens after a suspend and restore from suspend - just after I've hard-booted, it does not happen until after the first suspend.  I tried restarting kdm from a shell prompt, but it doesn't help, the problem still occurs.

My hardware: Lenovo T60, intel 945GM graphics with 1400x1050 TFT monitor

My software: Kubuntu 7.10 / intel graphics driver.  

Soon after upgrading from 7.4 to 7.10, I ran dpkg-reconfigure xserver-xorg-video-intel, because the default driver (i810?  I think) failed to support full resolution on my monitor and defaulted to 1280x1024.  

Prior to upgrading, on 7.4, video worked fine; I would suspend and restore the laptop all the time and no weird lines when I scrolled.  Please let me know what other details I should post, if any.

---

