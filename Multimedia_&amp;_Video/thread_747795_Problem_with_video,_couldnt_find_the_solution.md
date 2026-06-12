---
title: "Problem with video, couldnt find the solution"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by magusxp on 2008-04-06
Hi, im new to linux. My computer is a hp pavilion a820n it has an intel chipset for video, but I dont want to use it, instead i have a nvidia geforce FX5200 and I want to use that. When I enable in the BIOS primary video PCI when ubuntu is starting it stops it doesnt continues loading, when i was using windows, I had the primary video to onboard but when windows started It automatically changed to the video card output. I want to do the same thing here but, I cant find how, I already used ENVY to install the correct driver , but I cant find how to tell linux to change the video output to the card instead of the chipset.

Thanks for everything

---

### Post by renzokuken on 2008-04-07
you need to get to a terminal (Ctrl+Alt+F1) and run

```
sudo dpkg-reconfigure xserver-xorg
``` and select the "nvidia" driver from the drivers section.

if nvidia doesnt work or wasnt installed correctly via Envy...use the "vesa" or "nv" driver. these should get X working properly, then you can go about installing the official nvidia driver properly (preferably with the Restricted Drivers Manager and NOT Envy)

---

