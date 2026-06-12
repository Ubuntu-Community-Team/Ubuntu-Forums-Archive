---
title: "Realtek RTL8192CU or TP-LINK TL-WN821N ( Atheros various chipsets)"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by deckoff on 2013-01-13
So after extensive search for usb dongles that support N 300 MB/s AND are available in my country I came down choosing between:
TP-LINK TL-WN821N (most probably I will be able to find v 3 - Chip 1: Atheros AR7010 Chip 2: Atheros AR9287) or TP-LINK TL-WN821N  Realtek RTL8192CU?
I want to connect to my NAS wirelessly and be able to watch HD movies. The NAS is connected via cable to the router, and the PC that is connected to the PC will use the new dongle?

---

### Post by praseodym on 2013-01-13
Hi,

the driver ath9k_htc for the TP-Link device is not present in 10.04, so you have to compile the compat-wireless driver for it.

The rtl8192cu, too, but the Realtek drivers often s**k. Personally, I have the TP-Link in use with 12.04, no problems at all.

---

### Post by deckoff on 2013-01-13
Thank you. I use 12.04, I am too lazy to  check my avatar, it seems. Care to check the version of your TP-link?

---

### Post by praseodym on 2013-01-13
```
Bus 002 Device 003: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 802.11n [Atheros AR7010+AR9287]
```

---

### Post by Andrew F in Australia on 2013-01-13
The ASUS network adapter (edit) based upon the 8192CU chip (edit)  has issues, deckoff.

Have just spent the best part of about 16 hours on and off over the last four days getting it to (sort of) work, with the ASUS network adapter.

In short.

Reverted back to 12.04 from 12.10 (12.10 had half-hourly crashes on my system - mainly nautilus and logitech squeezeserver)

Downloaded latest driver from:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Extracted it to home directory

Found the directory with the install.sh script and ran it with  via sudo bash install.sh

Installed but with fatal errors.

However, on bootup, the kernel driver (rtl8192cu) connects to the  internet, but does not reconnect if you disable/re-enable it.

I'd suggest the other option may be better (or less worse.)

Cheers,

AF

---

### Post by deckoff on 2013-01-13
It is decided, then. I am going for the WN821N model.
The other one is not asus, but another TP link device, but since it uses the same chipset I should expect the same problems.

Cheers

---

