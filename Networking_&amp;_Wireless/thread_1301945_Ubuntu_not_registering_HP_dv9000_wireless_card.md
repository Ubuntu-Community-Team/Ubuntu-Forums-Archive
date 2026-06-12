---
title: "Ubuntu not registering HP dv9000 wireless card"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by parati570 on 2009-10-26
OK, so I downloaded Ubuntu 9.04 with the wubi application and everything is working great except for wireless. As far as I can tell my wireless card won't even turn on when I boot into Ubuntu, yet it works fine when I boot into windows. I can't tell if this is a problem with Windows restricting Ubuntu's access, a fault with HP, or a problem with Ubuntu itself. If it's a driver issue I might be out of luck because I don't have a wire to plug into to get the drivers. I used a terminal to try and find the problem, but the only thing it tells me is that it's disabled, and iv'e checked to make sure it's switched on multiple times. Any wisdom will help.

---

### Post by Ayuthia on 2009-10-26
> **parati570 said:**
> OK, so I downloaded Ubuntu 9.04 with the wubi application and everything is working great except for wireless. As far as I can tell my wireless card won't even turn on when I boot into Ubuntu, yet it works fine when I boot into windows. I can't tell if this is a problem with Windows restricting Ubuntu's access, a fault with HP, or a problem with Ubuntu itself. If it's a driver issue I might be out of luck because I don't have a wire to plug into to get the drivers. I used a terminal to try and find the problem, but the only thing it tells me is that it's disabled, and iv'e checked to make sure it's switched on multiple times. Any wisdom will help.

Do you know which wireless card you have?  You can check in lshw -C network for the one that is Disabled and let us know the make, model, and revision number.  Some Broadcom cards can be activated without an internet connection but I am not for sure if you have a Broadcom card.

---

### Post by parati570 on 2009-10-26
It's describes it as a Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter

---

### Post by darthfruitloop on 2009-11-23
I have the same laptop, it was the only thing that was an issue with ubuntu 9.04. Its actually an easy fix, 1:hook it to a wired connection 2:updates, 3: Restricted drivers icon should appear in the top right side, 4: enable the wireless drivers (I would also recommend installing the Nvidea graphics card drivers as well)   :)   5: reboot and you should have it working 

From there simply setup your wireless connection and MAKE SURE YOUR WiFi swich is ON..lol

Hope this helps ;)

---

### Post by cbclark4 on 2009-12-17
So I don't have access to a wired network I use the local library for wireless.

Is there a way to install the wireless driver offline?

---

