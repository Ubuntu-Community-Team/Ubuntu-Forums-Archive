---
title: "Intel 4965ABG +Karmic 9.10 +Wicd +WPA2 Fails"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by jfer on 2010-02-07
Hi,

I have an intel 4965abg card, and a Belkin G Router in AP mode.

It works very well with WPA2 in Backtrack, XP, and other distros.

WPA2 does not currently work, it hangs when getting an ip address, even with bad passphrase is entered instead of the correct one, so i suspect the WPA authentication maybe loaded instead of WPA2, even though wicd id's the essid it as WPA2 connection.

It does not seem wicd will allow me to specifically state WPA2, it loads as WPA1/2

I have tried using wext, and ipw as wpa drivers, both fail 

I have tried reinstalling wpa_supplicant, wicd, to no avail.
Also, static ip mappings fail "cannot associate with ap" is normally returned.

My AP does not do DHCP, but a server behind it does, I never see any arp requests on this dhcp server for this wificard, so i know the encryption handshake is generating a bad packet.

Any suggestions, I need WPA2 to work with this card on Karmic, any scripts or suggestions are welcome.

Jfer

---

