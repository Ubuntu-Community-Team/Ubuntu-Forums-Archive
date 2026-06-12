---
title: "Dual Monitors Lock up, Nvidia Drivers"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by darknight2183 on 2007-12-20
Hello Everyone,
    I've been using Ubuntu for about a year now and love it. Recently I bought an Nvidia 7200 chipset video card because I wanted dual monitors.  I installed the restricted nvidia driver, than enabled it, and than opened up "nvidia-settings" and configured it, initially, for Twinview. Everything seemed to have worked great except for: if the computer is on for approx 3-4 hrs the screen locks up, if the computer goes into it's screen saver it locks up.  I may still be a noob, but I've been a quick learner.  I backed up the orginal xorg.conf file in addition to the one using the dual monitor settings. Than I began editing the xorg,conf file to see if I could resolve the issue. Basically, all that I did was make sure that there was a section in there for "Composite 0" and set the default resolution and refresh rates to something I know that each monitor can handle. There is no parity between the monitors for resolution. And the monitors will lock out keyboard and mouse control whether xorg,conf is set to Twinview or separate X sessions. It does not lock the screen up when cloned. Any help would be greatly appreciated. If you need more info let me know and I'll post what you need.

---

### Post by darknight2183 on 2007-12-20
Just thought of something else that might be useful. The restrictive drivers that I am using are the nvidia-glx-new, but it does the same stuff as previously mentioned using the nvidia-glx-legacy driver too.

---

