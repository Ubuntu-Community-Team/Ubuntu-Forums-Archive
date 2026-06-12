---
title: "ubuntu 8.04/.10 freezes on boot/modprobe ath_pci with wireless card inserted"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by ushevade on 2008-12-05
Hi,

We have the following setup:
Card: Netgear WMP55AG
Chipset: Atheros AR5212/5213
Machine: Dell Inspiron 530s

Linux fails to boot (even during install, when it is booting as a live cd) if the card is present in the pci slot.
The precise point at which it freezes is at the loading of madwifi driver kernel modules. 

Same behavior is seen if we boot the machine (with ath_pci and newer versions like ath5k and ath9k blacklisted from the boot-time loaded modules) and run modprobe ath_pci from the command line.This command internally does three things:
insmod /lib/modules/<kernel version>/ath_hal.ko
insmod /lib/modules/<kernel version>/wlan.ko
insmod /lib/modules/<kernel version>/ath_pci.ko

The first two go through (verified via modprobe -v as well as manually running the first two commands), but the third one freezes up (hangs) the machine. 

We have tried installing available madwifi and madwifi-ng drivers from the website. The exact same problem occurs in Ubuntu 8.04, 8.10 and Fedora 9.

Can someone please help?

---

