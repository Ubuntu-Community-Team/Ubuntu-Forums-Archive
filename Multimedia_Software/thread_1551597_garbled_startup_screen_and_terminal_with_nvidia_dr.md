---
title: "garbled startup screen and terminal with nvidia driver"
date: 2010-08-12
forum: Multimedia Software
---

### Post by ajschaeffer on 2010-08-12
Hi,

A number of months ago, I upgraded from 9.10 to 10.04. Immediately after installing, I ran into problems with a blank display after starting Ubuntu from the grub menu. I have an NVidia Quadro card. Following a few forums, I was able to fix this by removing nouveau and removing nomodeset from the boot menu. Now, once the computer reaches the GDM login, there is no problem with the display. I can log in and use 3D effects with no problem. However, during boot up, the text splash screen is now garbled. In addition, once logged in and in gnome, if I change to a terminal (ie ctl-alt-f#), the display is garbled in the same way as at boot up (The garbled part is just white dots in the top 1/8 of the screen). When I go back to X (ctl-alt-f7), the gnome session carries on just fine.

I would really like to try to fix this so the terminals work again (I did not have this problem in 9.10). Please let me know what additional system information I should provide. I have an Nvidia Quadro NVS 160M on a dell Latitude E6400, with NVidia drivers 195.36.24.

thanks in advance

---

