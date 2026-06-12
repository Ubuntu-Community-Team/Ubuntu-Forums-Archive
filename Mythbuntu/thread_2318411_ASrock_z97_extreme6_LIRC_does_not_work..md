---
title: "ASrock z97 extreme6 LIRC does not work."
date: 2016-03-25
forum: Mythbuntu
---

### Post by Ram_Ramesh on 2016-03-25
Hi, 

I changed the motherboard on my mythbuntu backend/frontend combined server and everything went smooth except that my LIRC does not work anymore. I have mceusb remote with usb ir receiver. It worked fine with my old motherboard and simply does not work in asrock z97 extreme6. I have mythbuntu 14.04 LTS. KB/mouse and wireless KB work fine with this motherboard. Also, usb stick (I only tried usb 3.0) works fine. I am pretty sure that remote works as I see red dot on the dongle light up when I press buttons.

As far as I can see, no code is received by lirc daemon. When I run irw, it prints nothing when I press buttons. Any help or possible debug steps is greatly appreciated. I tried removing legacy remote support in BIOS and even my KB/mouse stopped working and system hung randomly. So, that is unlikely to be the path, but I am willing to try experimenting there also, if you know something that might work.

Are there any tricks I can try with /dev/lirc0? I cannot dd as it says invalid argument.

Regards
Ramesh

---

### Post by Ram_Ramesh on 2016-03-26
This is no longer an issue as I changed the IR receiver and it works now. While the original receiver still works in other system, it does not work in asrock exreme6 (z97). In researching, I found several others complaining about usb ports. So, it could be usb compatibility issue with this particular ir receiver. In any case, I am not sure if I should mark this solved. I will leave it as is for a little while and decide.

Ramesh

---

