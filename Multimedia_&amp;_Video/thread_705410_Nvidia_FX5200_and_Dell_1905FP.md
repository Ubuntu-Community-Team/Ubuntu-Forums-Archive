---
title: "Nvidia FX5200 and Dell 1905FP"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by HHelsinger on 2008-02-23
Does anyone have an xorg.conf file that enables a Dell 1905FP on an Nvidia FX5200 card?  
The driver and card work fine on my Mag CRT, but on the Dell the screen stays black.
When I try to run the nvidia driver on the Dell, the log file says 
"Unable to get display device CRT-0's EDID; cannot compute DPI '

---

### Post by leg on 2008-02-23
Which driver are you using. I have a NVidia fx5200 and have to restrict the driver to nvidia-drivers-1.0.9631 as I believe support for this card was dropped from later versions.

---

### Post by HHelsinger on 2008-02-23
The driver is the latest:  1:169.09.   It works fine with the Mag CRT monitor.   
And the Nvidia site seems to indicate that the latest drivers support the  FX5200.  I don't find anything that says otherwise.

The problem seems to be with the xorg configuration for the monitor

---

### Post by sanddgroper on 2008-02-23
Hi
I use the FX5200 card and always use the nvidia-glx driver on every version of
Ubuntu including 8.04 Alpha4 without any problems.
I may be wrong but I don't think you should be using the 169.09 for the FX5200 card.
From what I understand it is only for the latest cards from nvidia.

Cheers
Sandy

---

