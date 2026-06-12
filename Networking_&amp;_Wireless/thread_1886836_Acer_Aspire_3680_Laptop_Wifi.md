---
title: "Acer Aspire 3680 Laptop Wifi"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by 000sk7 on 2011-11-25
I have an acer aspire 3680 with Ubuntu 11.10 installed and the wireless has not worked since installation.  So far I've been using a wired connection but I'd like to use wifi.  The wifi chip in my laptop is a  Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01).  When I type rfkill list into the terminal nothing happens.  Any help at all would be appreciated.

---

### Post by praseodym on 2011-11-25
Hi,

install the packages **b43-fwcutter** and **firmware-b43-installer** via cable connection in the software-center. This firmware is proprietary and isnt shipped by default from Ubuntu.

---

