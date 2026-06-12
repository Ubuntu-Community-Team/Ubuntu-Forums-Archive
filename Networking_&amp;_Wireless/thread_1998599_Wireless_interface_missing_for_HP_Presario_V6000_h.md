---
title: "Wireless interface missing for HP Presario V6000 having Intel(R) PRO/Wireless 3945ABG"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by mohdbehzad on 2012-06-07
I've recently Installed Ubuntu 11.04 on my HP Compaq Presario V6307 TU. Everythings seems fine except that I can't use my wireless card. The network manager doesn't show any Wireless networks. My system data is as follows:[INDENT]tejaswini@tejaswini-PC:~$ dmesg | grep iwl
[   13.136311] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   13.136317] iwl3945: Copyright(c) 2003-2010 Intel Corporation
tejaswini@tejaswini-PC:~$ lspci -nn | grep WLAN
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
[/INDENT]Also note that i've installed Addition Driver for wifi card, details are in image attached:

Also note:[INDENT]tejaswini@tejaswini-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[/INDENT]Please help. Thanx in advance.

---

### Post by mohdbehzad on 2012-07-11
Sorry, to post this so late...
The issue posted above was solved by installing wifi interface, which was mising.

---

