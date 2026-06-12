---
title: "Gateway setting in NetworkManager being deleted"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by frisket on 2010-06-08
I just installed 10.4 LTS and went to set the fixed IPv4 settings for Auto eth0 in the NetworkManager applet. I could enter my workstation address, DNS addresses, and netmask, but when I entered the campus gateway address, the applet converted it to 0.0.0.0

In fact *anything* entered in the Gateway field gets turned into 0.0.0.0, which means I cannot connect off-campus.

Has something changed in the way NM accepts this data? And is there some way to force it to accept and obey the gateway address?

I could edit /etc/NetworkManager/system-connections/Auto eth0, but I cannot find any man pages on the syntax for this file.

[Later]

Turns out this is a bug. You have to press the Enter key after entering the Gateway address, otherwise it doesn't see it. You can't just click Apply.

---

