---
title: "help please rtl8102 network driver for Intel Atom board"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by paped on 2009-03-25
Help please I have bought a new Intel Atom motherboard and need to configure 8.04 LTS on it (actual version is 8.04.1 and after online upg this becomes 8.04.2). the NIC is a realtek rtl8102e

But in both versions I am having major problems get the network card to work never mind get it stable. This problem seems to be posted all over the internet including on the Ubuntu bugs page for 8.10 and I have tried various things over the past week to get this going but it just won't work properly.

Basically the card works fine during the install (anybody know which driver the install is using?) but as soon as the system is rebooted it does not pick up DHCP setting and even when statically configured just does not seem the have a connection.

Ubuntu seems to be loading the r8169 driver to use on the system, I have however tried to download the proper realtek 8102 driver but both the versions from intel and a newer realtek version refuses to compile and exists with error 2 on the make clean modules command.

So basically I have an expensive paperweight but there are a number of forum post that say they have got his working under Ubuntu but I just seem to be going around in circles and not getting anyway. So any help advice or pointers would be greatly appreciated.

---

### Post by paped on 2009-03-27
May have found a work around to this please see my post on this item - [http://ubuntuforums.org/showthread.php?t=1058002](http://ubuntuforums.org/showthread.php?t=1058002)

---

