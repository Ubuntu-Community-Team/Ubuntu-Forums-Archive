---
title: "Atheros / Acer Asprire 5720z - nothing works"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by koskos on 2009-01-21
I'm trying to get my Atheros WLAN card to work with a fresh install of 8.10, naturally the default settings donn't work. I've tried a few other things that have worked for others: [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros), [https://help.ubuntu.com/community/AspireOne110L#WLan](https://help.ubuntu.com/community/AspireOne110L#WLan). No help.

Basically I can't connect using the default network manager (no error message, just nothing) and the wicd network manager says "no wireless networks found".

lspci:

```
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

lsmod | grep ath  gives nothing

sudo lshw -C network says that Atheros is UNCLAIMED

---

### Post by koskos on 2009-01-22
Bump. No clues? :(

---

### Post by ibutho on 2009-01-22
Hi. Try the suggestions in this [thread]("http://ubuntuforums.org/showthread.php?t=1026770").

---

