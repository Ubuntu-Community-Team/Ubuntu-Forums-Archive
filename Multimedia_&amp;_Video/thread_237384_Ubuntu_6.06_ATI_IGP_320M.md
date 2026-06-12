---
title: "Ubuntu 6.06 ATI IGP 320M"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by satellitepazzo on 2006-08-16
Dear all,
I just installed Ubuntu 6.06, but at the first boot I got black screen, the same situation using live-cd version when KDE start. The only way to run ubuntu is by selecting  "safe graphic mode". It seems graphic card driver problem, in safe mode Vesa drivers are used...

My laptop is AMILO A and video card is ATI IGP 320M. 
How can I use "vesa" drivers by default or how can I install the right drivers for IGP320M?

---

### Post by encompass on 2006-08-16
run this at the console:
```
sudo dpkg-reconfigure xserver-xorg
```
press enter for defaults until you reach the driver for your card.  Pick the vesa.
After you have that working... you may want to try the ati howtos to get your card to work with 3d graphics support.
If you can't get to a console... when your computer starts your going to see a countdown... press escape during that count down and then select fail safe.
Hope this helps.

---

