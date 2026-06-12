---
title: "Cpletely remove MediaTomb"
date: 2011-12-29
forum: Multimedia Software
---

### Post by gmsalomao2 on 2011-12-29
Hi,

I'm trying really hard to uninstall MediaTomb, but I'm getting errors every time. I've tried *apt-get remove mediatomb, apt-get -f install mediatomb, apt-get --purge remove mediatomb,apt-get autoclean...*

I just can't do it! It's frustrating! I'm trying to install the pcap library, but it seems to have some trouble with MediaTomb.

---

### Post by LucidREM on 2012-03-09
> **gmsalomao2 said:**
> Hi,

I'm trying really hard to uninstall MediaTomb, but I'm getting errors every time. I've tried *apt-get remove mediatomb, apt-get -f install mediatomb, apt-get --purge remove mediatomb,apt-get autoclean...*

I just can't do it! It's frustrating! I'm trying to install the pcap library, but it seems to have some trouble with MediaTomb.

i did not have any issues myself .. i actually switched to MBL (My Book Live) for media and turned off MediaTomb

$ sudo stop mediatomb
$ sudo apt-get --purge remove mediatomb
$ sudo apt-get autoremove

i cannot say why these would not work for you

---

