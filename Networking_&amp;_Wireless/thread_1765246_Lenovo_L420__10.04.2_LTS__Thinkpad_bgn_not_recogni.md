---
title: "Lenovo L420 / 10.04.2 LTS / Thinkpad bgn not recognized"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by rokob on 2011-05-22
I recently purchased a Lenovo Thinkpad L420 with the integrated Thinkpad bgn wireless controller. I installed 10.04.2 today and pretty much everything seems to work except the wireless card. It does not appear to be recognized as existing at all. Below is the output of the usual commands. Any help would be appreciated.

$ lspci
 ...
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
04:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

$ ifconfig
eth0 Link encap:Ethernet ...

lo Link encap:Local Loopback
...

$ iwconfig
lo  no wireless extensions.

eth0  no wireless extensions.

$ lsb_release -d
Description: Ubuntu 10.04.2 LTS

$ uname -mr
2.6.32-28-generic i686

---

### Post by chili555 on 2011-05-22
> Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)I believe this is your wireless device. Please run:```
lspci -nn
```If you pci.id is 10ec:8176, then please check here, especially the last three posts: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

Please post back if you get stuck.

---

### Post by rokob on 2011-05-23
$ lspci -nn | grep 'Realtek'

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
...

This confirms what you said. I ran the three apt commands at the end of the linked post, restarted, and the wireless works perfectly. Awesome. Thank you very much. :P This is my first time crossing over to the linux community from FreeBSD; I chose ubuntu partially because of the reputation of the community and I couldn't be happier.

---

### Post by chili555 on 2011-05-23
> I chose ubuntu partially because of the reputation of the community and I couldn't be happier.Thank you for your kind comments and please post back if we can help you further.

---

### Post by Betonius on 2012-03-14
:) also worked for me:
Thinkpad E520
Lucid 10.04.4

Now i have wireless

Thanks everyone.

---

