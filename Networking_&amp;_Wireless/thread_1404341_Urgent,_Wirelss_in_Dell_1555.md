---
title: "Urgent, Wirelss in Dell 1555"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by sushilsc on 2010-02-11
Hi,
  
 I recently purchased a DELL 1555 and intalled Ubunut 9.10 (32 bit )on it. Now when I run ifconfig -a command then I do not see the configuration for wireless likeMac id ect..

  Also in the network connection it does not show the wireless connections. It shows only the wired connetion.

It has window 7 and there the wireless works fine.

 Someone can help?

with best regards,
sushil

---

### Post by chili555 on 2010-02-11
Please open a terminal and run:```
lspci -nn | grep Network
```Does it tell you that you have an Intel WiFi Link 5100-Mini 802.11 a/b/g/n? If so, please run:```
dmesg | grep iwlagn
```Let's see why it's not loading.

If not, please tell us what *lspci* says about your wireless.

---

### Post by sushilsc on 2010-02-11
Hi,

  Thanks for your reply.

running the lspci -nn | grep Network I get the following,


sushil@sushil-laptop:~$ lspci -nn | grep Network
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
sushil@sushil-laptop:~$ 



I have the following wirelsess card

Wireless card:

Dell Wireless 1397 802.11g Half Mini Card


with best regards,
sushil

---

### Post by sushilsc on 2010-02-11
ok I installed the driver for Broadcom STA and now the wireless works fine. Thanks for your quick reply.

with best regards,
sushil

---

### Post by chili555 on 2010-02-11
Glad to almost help you!

---

