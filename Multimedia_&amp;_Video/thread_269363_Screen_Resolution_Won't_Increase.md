---
title: "Screen Resolution Won't Increase"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by posey on 2006-10-01
I have an IBM desktop with S3 Trio 64 3D graphics (onboard) that I'm fairly sure is capable of 1024x768. I want it to use 1024x768.
It boots up at 800x600 and stays there. If I try to use the menu to change it, my options are 640x480 and 800x600.
I edited the xorg.conf to try to get it to change and it would seem the changes were ignored, even after reboot.
I ran the dpkg-reconfigure xserver-xorg twice. The first time broke the xserver, and the second made it work again but didn't get me the 1024x768. 
I removed the 640x480 from the xserver config, but it still shows up in the graphical menu.

Help, please.

---

### Post by Josh1 on 2006-10-01
> **posey said:**
> I have an IBM desktop with S3 Trio 64 3D graphics (onboard) that I'm fairly sure is capable of 1024x768. I want it to use 1024x768.
It boots up at 800x600 and stays there. If I try to use the menu to change it, my options are 640x480 and 800x600.
I edited the xorg.conf to try to get it to change and it would seem the changes were ignored, even after reboot.
I ran the dpkg-reconfigure xserver-xorg twice. The first time broke the xserver, and the second made it work again but didn't get me the 1024x768. 
I removed the 640x480 from the xserver config, but it still shows up in the graphical menu.

Help, please.

Hi,
It's probably caused from your drivers, maybe the graphic card isn't totally supported? That could be causing it to not raise past 800x600...
- Josh

---

### Post by posey on 2006-10-01
It's using the s3virge driver, which I found elsewhere on this forum that it is the correct one to use; the xserver won't work with the s3 driver. It's supposed to be a well supported card.

---

### Post by Josh1 on 2006-10-01
> **posey said:**
> It's using the s3virge driver, which I found elsewhere on this forum that it is the correct one to use; the xserver won't work with the s3 driver. It's supposed to be a well supported card.

Hi again,
I've never used this card, so I was just guessing that you haven't raised it past 1024x768.
- Josh

---

### Post by posey on 2006-10-01
Is there a way to check the video ram from the operating system?

I bought the box from some shady guy and the case and the guts are not the original combination.

---

