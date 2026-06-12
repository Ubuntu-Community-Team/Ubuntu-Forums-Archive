---
title: "Jerky graphics card - Nvidia NV28 Geforce4 Ti 4200"
date: 2010-12-05
forum: Multimedia Software
---

### Post by rdh on 2010-12-05
Hi - I'm a newbie, just installed ubuntu 10.10 on my son's pc (Athlon 1.6Ghz, 2Gb RAM, 80 Gb HD). Everything works so much quicker except graphics.The graphics is very jerky. When playing games on net, they are almost unplayable, as takes ages for graphics to refresh on screen. I've tried looking for better driver, as I understand ubuntu uses legacy drivers for this card, but all advice seems to point me to System  Admin  Additional drivers to look for open soursce drivers, but there are no drivers at all displayed in the window.

The card is a WinFast A280, AGPx8. 128RAM


joel@joel-KT600-8237:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
joel@joel-KT600-8237:~$ 

Any help would be much appreciated. Many thanks

---

### Post by rdh on 2010-12-05
Hi all I have just downloaded the following file from the Nvidia website: 

NVIDIA-Linux-x86-96.43.19-pkg1.run

Can anyone advise me how to install this driver? It says that this should work with the card in Linux.  It seems that I have generic drivers installed - I cannot use the Visual Effects, in appearance for example. I am reluctant to buy a new card, but as a newbie to Linux - (apart from successfully installing a version on a friends pc a few years ago),I am a little out of my depth! Surely there should be a solution? Thank you

---

### Post by Haydnlenz on 2010-12-05
I am having the same exact problem, with the same graphics card. I was running on linux mint when it was all jerky. Now that I upgraded to ubuntu 10.10 I am wondering since I saw this post if I will have the same problem I did on linux mint. Another post I read said that on 10.04 his nvidia video card was fine, but on 10.10 it was terrible. Is there a way to make it less jerky on 10.10? And does 10.04 run nvidia cards better? Thanks in advance:)

---

### Post by rdh on 2010-12-10
Hi there I have just wiped 10.10 and installed 10.4, which does have a proprietary driver listed for the card. This seems to be much better, although still not as smooth as windows driver. However, it will have to do!

---

