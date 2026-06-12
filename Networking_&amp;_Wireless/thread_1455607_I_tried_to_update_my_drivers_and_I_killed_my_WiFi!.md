---
title: "I tried to update my drivers and I killed my WiFi!"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by ninjaaron on 2010-04-16
I've been having some problems with my Atheros AR9285 wireless card, so I asked some questions, did some searching, etc.

Anyway, I found this page:[https://help.ubuntu.com/community/Wi...Atheros/AR928]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285")

In Step #1 it says something about downloading the latest stable version from [http://linuxwireless.org/en/users/Download/stable/]("http://linuxwireless.org/en/users/Download/stable/")

I did. It's compat-wireless-2.6.34-rc4.tar.bz2, or so I believe. I was a little suspicious about this, since I have only have the 2.6.31-20 generic kernel or something like that, but I figured if the tutorial said I should get the latest, who am I to question it? I don't understand the deep ways of the Linux.

So I built, installed, and unloaded the packages, then rebooted. No WiFi anymore. I restarted again. Same thing. Now I'm in Windows trying to get it sorted. Just give me my internet back!!

Thanks,
Aaron

---

### Post by bkratz on 2010-04-16
> **ninjaaron said:**
> I've been having some problems with my Atheros AR9285 wireless card, so I asked some questions, did some searching, etc.

Anyway, I found this page:[https://help.ubuntu.com/community/Wi...Atheros/AR928]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285")

In Step #1 it says something about downloading the latest stable version from [http://linuxwireless.org/en/users/Download/stable/]("http://linuxwireless.org/en/users/Download/stable/")

I did. It's compat-wireless-2.6.34-rc4.tar.bz2, or so I believe. I was a little suspicious about this, since I have only have the 2.6.31-20 generic kernel or something like that, but I figured if the tutorial said I should get the latest, who am I to question it? I don't understand the deep ways of the Linux.

So I built, installed, and unloaded the packages, then rebooted. No WiFi anymore. I restarted again. Same thing. Now I'm in Windows trying to get it sorted. Just give me my internet back!!

Thanks,
Aaron

Not an expert, by any means, but did you update your kernel when you did this? It seems to specify that you have a newer one than the 2.6.31-20 you seem to be using. See this listing for information about updating, ( it worked for me).

[http://unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint](http://unixmen.com/linux-tutorials/780-upgrade-your-kernel-the-safe-way-in-ubuntu-linuxmint)

---

