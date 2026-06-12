---
title: "X Server won't load..."
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by Saponsky09 on 2007-08-18
I have Ubuntu installed on an external usb hard drive and when it boot it just loads until the X server's dotted screen appears and nothing more happens.  I've compared my xorg.conf file with the one at the LiveCD (from which I installed) and it's identical so I don't get what's the problem.  Why does it loads pretty well from the LiveCD and crashes from the external Hard Drive???

---

### Post by Harlequin on 2007-08-19
Try modifying your Xorg.conf to use the vesa driver.  Any system should be able to post on this.  

Section "Device"
        Identifier      "generic"
        Driver          "vesa"

---

