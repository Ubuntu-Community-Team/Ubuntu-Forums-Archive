---
title: "WLAN card won't turn on - dual boot Vista &amp; 9.10"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by aa4bb on 2009-12-14
Upgraded two machines, in which WLAN was working in 9.04 prior to upgrade:
Dell Inspiron 1525 / Broadcom 4312
HP TX2500 / Broadcom 4328

On both, the wireless card light is off when booting into Ubuntu, and the switch has no effect. The card comes on in Vista, but goes off when shutting down from Vista and restarting in Ubuntu. 

I saw in WiFiDocs/WirelessCardsSupport page for Broadcom that you must turn the card on in Vista in order for the described methods to work. I did, but can't figure how to keep it turned on.

---

### Post by aa4bb on 2009-12-15
After researching, I did the following:

System>Administration>Synaptics Package Manager
Searched for bcmwl-kernel-source
Package>Mark for Installation
Apply

After that installed, I restarted the computer.

The WiFi light came on, and wireless now shows up and connects as it did in 9.04.

I probably went through a similar procedure when I installed 9.04 but forgot to write it down so I'd remember how to do it.

This works with both the Dell and the HP notebooks.

---

