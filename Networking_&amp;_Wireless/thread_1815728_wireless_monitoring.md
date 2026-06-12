---
title: "wireless monitoring"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by dog-soldier on 2011-07-31
im looking for a program to monitor my network to make sure no one is stealing internet or at least trying to.i have wep set up but you never know.
i tried wireshark but had a hard time getting it figured out. i got wicd installed right now but its not giving me the info i want. i searched on here but really didnt find what i was looking for. 

im using Ubuntu 11.04 on a laptop.

---

### Post by Kooothor on 2011-07-31
> **dog-soldier said:**
> i have wep set up

Hello,
WEP is very insecure. Try WPA2.
~ktr

---

### Post by dog-soldier on 2011-07-31
> **Kooothor said:**
> Hello,
WEP is very insecure. Try WPA2.
~ktr

i messed up its not wep but wpa instead.

---

### Post by Kooothor on 2011-08-01
For monitoring, you can try : [http://autoscan-network.com/](http://autoscan-network.com/)
But there are lots of them.

---

### Post by haqking on 2011-08-01
> **dog-soldier said:**
> i messed up its not wep but wpa instead.

use wpa2 and use as hard a passphrase as possible.

WPA and Wep can be cracked very easily and quickly, especially if simple passwords are used in WPA.

As long as the handshake is captured it can take a few seconds if has a weak WPA password etc.

wireshark is one of the best monitoring tools available

see here for 802.11 capturing using wireshark if you are having problems [http://wiki.wireshark.org/CaptureSetup/WLAN](http://wiki.wireshark.org/CaptureSetup/WLAN)

---

