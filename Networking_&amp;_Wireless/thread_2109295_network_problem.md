---
title: "network problem"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by erinadel on 2013-01-27
Hello;
I need help with my new installed ubuntu12.10 , during  installation it could not recognize the Ethernet card (and could not open the wired connection) so I asked it to complete using the wireless connectivity, after the installation done I couldn't open the wired connection totally refuse to connect, can I get any answer :(

---

### Post by kc1di on 2013-01-27
Hello erinadel and welcome to Ubuntu,

It would be helpful to know what Lan card your machine is using
could you post the output of the following command in a terminal

```
lspci
```

---

### Post by erinadel on 2013-01-28
thanks for your help offer that I really need :)

this is the output

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:01.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI

---

### Post by kc1di on 2013-01-28
Sorry took so long getting back to you.

your LAN card is a Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller.

This particular card has been a problem card for most distros.

[here is a page ]("https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/")that may offer you some help in getting it going though.
this page is a bit old but think it will still work.
Good luck
P.S. here are a couple more pages that may be of help also. 
[page 1]("http://askubuntu.com/questions/169457/realtek-rtl8111-8168b-pci-express-gigabit-rev03-keep-losing-driver-no-link-wi")
[Page 2]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/524454")

---

### Post by erinadel on 2013-02-02
Hi [kc1di]("http://ubuntuforums.org/member.php?u=1839")
Thanks allot, now it works and the thanks to you and [this]("https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/") article writer

Many thanks

---

