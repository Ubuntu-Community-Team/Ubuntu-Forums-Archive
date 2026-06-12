---
title: "using all of a Sony KDS-R50XBR1 1080i display"
date: 2008-06-30
forum: Multimedia Software
---

### Post by wo_shi_big_stomach on 2008-06-30
Using the latest Nvidia 173.14.09 driver on Mythbuntu 8.04, the default screen resolution is only 1216x684, and the maximum shown in the Nvidia X utility is 1600x1024.

Neither setting fills a 50-inch Sony rear projection 1080i HD screen, which is supposedly 1920x1080. Instead there are big black borders around the image.

I've searched the Nvidia Linux and Mythbuntu forums but didn't see anything directly about this setup. Thanks in advance for clues on getting this card and driver to use the entire screen.

/wsbs


NVIDIA driver 173.14.09

Mythbuntu 8.04 x86 (32-bit)

Gigabyte GeForce 7200 GS video card:

# lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
# lspci -n | grep 0300
01:00.0 0300: 10de:01d3 (rev a1)

Asus M2A-VM HDMI motherboard

Sony KDS-R50XBR1 50" SXRD TV, 1920x1080 resolution (now connected to video card via VGA cable; DVI (card)-to-HDMI (TV) cable yields same results)

AMD Athlon 64 AM2 Dual Core 4800 CPU

---

### Post by wo_shi_big_stomach on 2008-08-24
bump

I would be eager to hear from anyone with a working xorg.conf for a Sony kds-r50xbr1. 

thanks

---

