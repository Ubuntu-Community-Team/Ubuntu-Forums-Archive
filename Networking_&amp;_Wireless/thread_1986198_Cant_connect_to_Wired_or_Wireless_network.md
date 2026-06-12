---
title: "Cant connect to Wired or Wireless network"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by Newbatthis on 2012-05-24
Hey there, I recently stumbled upon and installed an old version of Ubuntu 7.10 on an old laptop and am having trouble connecting to the internet.

In the terminal while using ifconfig only lo comes up.

Any help would be greatly appreciated.

---

### Post by wildmanne39 on 2012-05-24
Hi, 7.10 is very outdated you can not install any software for it including security updates, you should go to [http://www.ubuntu.com/](http://www.ubuntu.com/)
and download and install an updated version of ubuntu and your ethernet connection will most likely work by default.
Thanks

---

### Post by praseodym on 2012-05-24
Hi,

wildmanne39 is right. For "old" laptops I recommend Xubuntu 12.04, its a fast and light Desktop environment suitable for old hardware.

But the main reason is, that Xubuntu (in contrast to K/Ubuntu) 12.04 LTS ships the regular 32bit generic kernel, without -pae modules. This may work (better) on an old machine depending on the mainboard chipsets. You are always free to co-install the other desktops afterwards with the corresponding packages "ubuntu-desktop", kubuntu-desktop", etc.

---

