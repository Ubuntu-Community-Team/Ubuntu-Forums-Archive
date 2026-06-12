---
title: "Cant play videos smoothly"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by rajitsrinivas on 2007-07-07
Hi,
I've Ubuntu 7.04 on a Dell laptop with integrated video and ubuntu is using i810 drivers. The problem is, I cant play videos smoothly.. meaning the video plays but cant see anything..if i continuously keep resizing the player window then I can see the picture :D ..this has been the problem since an upgrade to 7.04. Video was all fine in 6.10. So I boot to windows to watch any video :(

This is what I have in the xorg.conf

Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection


Any help is greatly appreciated.

Regards & thanks,
Rajit

---

