---
title: "Ndiswrapper (Monitor Mode Not Supported)"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by 11BrathovdeA on 2011-04-24
Hi there,

I've been trying to mess around with aircrack-ng, and i think that i installed everything that i needed correctly. My wireless driver seems to be working correctly and appears to be properly working off of my windows driver. But when i enter in the code sudo airmon-ng start wlan0, it comes up with :

Found 6 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
706    avahi-daemon
709    avahi-daemon
719    NetworkManager
743    wpa_supplicant
2598    dhclient
2724    dhclient
Process with PID 2724 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Unknown       ** ndiswrapper (MONITOR MODE NOT SUPPORTED)**

From what i've been looking at trying to have the aircrack-ng program work i need monitor mode to be supported and working. Is there another driver that supports monitor mode that i can install? Or maybe a setting that i can tweak with to help me move forward?

Thank you to those who take the time to read this and a special thanks to those who answer.
Feel free to request more information if it can help me in anyway.

Regards,

Andrew

---

