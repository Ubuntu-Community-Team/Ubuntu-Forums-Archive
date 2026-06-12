---
title: "WiFi disconnects with WEP?"
date: 2006-01-12
forum: Networking &amp; Wireless
---

### Post by dtlinker on 2006-01-12
I am new to Ubuntu, and have installed Breezy on a new Dell Inspiron B130 laptop set up for dual-boot, with Dell Wireless 1370 WLAN Mini-PCI Card, made by Broadcom. 

I have gotten the interface to connect to an Apple Airport wireless station without encryption, as an "open" network.

If I enter a 40 bit key, I can rarely get it to work for a short time, using System->Administration->Networking. I am unable to get 128 bit keys to work.

If I use the terminal and write:
sudo iwconfig wlan0 key restricted <thekey> essid <the station>

followed by:
iwconfig

I see that the connection has been made. If I repeat the iwconfig command a few times, the connection is lost!!!!

How do I get it to keep a WEP connection? Or is there something else I should be doing?

Thanks in advance.

---

