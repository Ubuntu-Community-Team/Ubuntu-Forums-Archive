---
title: "Broadcom BCM4312 LP-PHY"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by noisysoul on 2013-04-11
Hi everyone,

I have installed **Ubuntu 12.10** on a (netbook) **HP Mini 210** 1028LA, and everything works out of the box except for the wireless connection. I have tried to install some drivers but I haven't been able to fix it. It is a *Broadcom Corporation BCM4312 LP-PHY* (network controller). Please, if you know how to make it work, I would thank you a lot if you could help me (offline installation if possible). Here you have the lspci info:

00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
[B]01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)[/B]

---

### Post by Hadaka on 2013-04-11
Hi, please copy and paste the following
into a terminal.
```
lspci -nn | grep 0280
lsmod
cat /etc/modules
rfkill list all
```
post the results.
thanks.

---

### Post by noisysoul on 2013-04-11
I fixed it!!! just following:

[https://andym3.wordpress.com/projects/the-broadcom-wireless-card-guide/](https://andym3.wordpress.com/projects/the-broadcom-wireless-card-guide/)

---

