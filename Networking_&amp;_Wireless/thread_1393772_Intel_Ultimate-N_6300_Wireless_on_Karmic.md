---
title: "Intel Ultimate-N 6300 Wireless on Karmic"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by tehfade on 2010-01-29
Thought I'd make a thread to get some info out there, since I spent all day searching for how to get this card to work on Karmic.

This card does not work automatically in Karmic. The problem, as I understand it, is that the iwlagn driver seems to expect there to be ucode of version 3 or lower in /lib/firmware/. There is a ucode file supplied, iwlwifi-6000-4.ucode, but it is not looked for (you can see in dmesg) or supported. Installing linux-backports-modules-karmic fixes this.

---

### Post by chrisjuel on 2010-03-19
Yay, thanks for the info. 

This worked great on my new Lenovo T510!!

---

### Post by garymlewis on 2010-03-22
This also worked fine on my Thinkpad W510, 64bit 9.10 desktop.

Thanks very much!

---

