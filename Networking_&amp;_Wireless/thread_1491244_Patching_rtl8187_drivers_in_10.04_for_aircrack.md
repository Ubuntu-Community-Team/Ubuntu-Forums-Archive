---
title: "Patching rtl8187 drivers in 10.04 for aircrack"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by nihilum on 2010-05-23
I'm trying to capture a WPA handshake with aircrack, and so far I've been unable to do so. Putting the device in monitor mode and testing injection with aireplay both work, I've cracked a WEP access point with fake authentication successfully, but I can't seem to capture a WPA 4-way handshake. First of all, would patching the rl8187 driver even help with what I'm trying to do? The patch is at [http://www.aircrack-ng.org/doku.php?id=rtl8187](http://www.aircrack-ng.org/doku.php?id=rtl8187) and it's supposed to help injection speed. I'm not sure if the problem is with deauthenticating the client or actually capturing the reauthentication. (Edit: moved the client that I was deauthenticating into the same room and was able to capture the full handshake, so it may have just been a range issue)

---

