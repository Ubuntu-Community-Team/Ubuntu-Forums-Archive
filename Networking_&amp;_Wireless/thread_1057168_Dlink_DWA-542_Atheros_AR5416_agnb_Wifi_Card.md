---
title: "Dlink DWA-542 Atheros AR5416/ a/g/n/b Wifi Card"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by rediron on 2009-02-01
Hi All,

I have the D Link DWA 542 and I was wondering if it works in Linux yet ?  I've tried the numerous posts about restricted drivers, madwifi, lspci -v, etc, etc.., but now wifi0 or ath0 devices yet.

lcpci -nn |grep Ath
01:01.0 Network controller [0280]: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter [168c:0023] (rev 01)

red@desktop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

red@desktop:~$ lsmod |grep ath
ath_pci               107824  0 
wlan                  227104  1 ath_pci
ath_hal               219888  1 ath_pci


red@desktop:~$ dmesg |tail

 [ 1252.001239] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1252.012135] wlan: 0.9.4
[ 1252.016564] ath_pci: 0.9.4

red@desktop:~$ lsb_release -d
Description:	Ubuntu 8.04.1

red@desktop:~$ uname -mr
2.6.24-22-generic x86_64



Thanks,
 Red

---

### Post by nixscripter on 2009-02-03
I don't have much experience with madwifi, but this guide suggests compiling your own copy of madwifi, because apperently repository ones don't always work: [http://www.linuxmint.com/forum/viewtopic.php?f=53&t=10209](http://www.linuxmint.com/forum/viewtopic.php?f=53&t=10209)

---

### Post by ajmetalhed on 2009-05-26
I'm not sure about Ubuntu, but it works with version 7 of linux mint.  I booted up the live cd and I was immediately able to view wireless networks and connect to mine.  Pretty soon I'll be dual-booting Vista and Mint. :popcorn:

Edit://
It probably works with the latest version of Ubuntu, considering Mint is based on Ubuntu.  I tried to get it to work with version 7 of Ubuntu and failed.  You can probably get it to work easily in version 8.  But as for Linux Mint, I have now confirmed that the dwa-542 is out-of-the-box compatible.

---

