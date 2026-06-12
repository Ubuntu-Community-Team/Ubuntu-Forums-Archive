---
title: "Switched motherboard, broke X"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by kommisar on 2007-09-27
I swapped my motherboard and tried to reboot using my old feisty install.  Seemed to boot fine but x windows failed to load.  Looking at error logs looks like the old pci coordinates of the video card have changed.  Is there a command where i can force a redetection of the video card pci coordinates and reconfigure of the x windows system?  I am a ubuntu noob.

TIA

---

### Post by handydan918 on 2007-09-27
> **kommisar said:**
> I swapped my motherboard and tried to reboot using my old feisty install.  Seemed to boot fine but x windows failed to load.  Looking at error logs looks like the old pci coordinates of the video card have changed.  Is there a command where i can force a redetection of the video card pci coordinates and reconfigure of the x windows system?  I am a ubuntu noob.

TIA

Yup. Try 
```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you some questions, but usually has the defaults filled in. They usually work.

---

### Post by kommisar on 2007-09-27
Hey that worked.  Thanks.   Motherboard transplant was successful!

---

