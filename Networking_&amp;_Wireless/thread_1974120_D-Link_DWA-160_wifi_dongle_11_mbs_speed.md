---
title: "D-Link DWA-160 wifi dongle 11 mbs speed"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by maciej234 on 2012-05-05
Is there a reason that the wifi speeds on my wireless usb adapter are only 11 Mbs?  Its a wireless N and I am getting download speeds of : ~3 mbs, Up: ~2 mbs. I was expected downloads speeds of greater than 10mbs.  I installed non-free firmware, and compact wireless via synaptic. I also:

I blacklisted a driver following these steps:

[https://www.thinkpenguin.com/gnu-linux/penguin-80211n-usb-upgrading-carl9170-ubuntu-lts-lucid-1004-and-maverick-1010](https://www.thinkpenguin.com/gnu-linux/penguin-80211n-usb-upgrading-carl9170-ubuntu-lts-lucid-1004-and-maverick-1010)

- Device: wlan1  [linksys] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            carl9170
  State:             connected
  Default:           yes
  HW Address:        CC:B2:55:00:58:D7

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

---

### Post by gordintoronto on 2012-05-05
What other devices are on your network? It will fall back to the lowest common denomintator.

---

