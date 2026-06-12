---
title: "Ubunto does not detect my wireless network... but it detect others!?"
date: 2012-04-16
forum: Networking &amp; Wireless
---

### Post by Danieltba on 2012-04-16
Hello, i just installed ubuntu 11.10 32 bit on my hp pavillion dv4 laptop, Everything is fine except that it detects every wifi network on my building except mine :S! I have no trouble detecting and connecting to my network with other devices or even with the same laptop when it had windows. I have tried to add the network information manually but i cant connect. So anyone knows what could be the problem?

Regards

---

### Post by ZekeGraal on 2012-04-16
> **Danieltba said:**
> Hello, i just installed ubuntu 11.10 32 bit on my hp pavillion dv4 laptop, Everything is fine except that it detects every wifi network on my building except mine :S! I have no trouble detecting and connecting to my network with other devices or even with the same laptop when it had windows. I have tried to add the network information manually but i cant connect. So anyone knows what could be the problem?

Regards

Welcome to the Ubuntu Forums!

Did you set up the WiFi on the computer before it had Ubuntu? If it detects all the other networks and not yours, the SSID of your router may be hidden. The SSID is the name or identification used for routers, which in some cases it can be set to hide itself. On your router, find the SSID. (It should be on it somewhere). Find the WEP or WPA code or other password technology that it may have. On Ubuntu click the wireless icon in the upper right of the desktop and select "connect to hidden wireless network". Type in the SSID and select the pass code type (if there is a code), and hit confirm/connect.

Report back so we can mark as solved or possibly give you more help!

EDIT: I got ahead of myself, sorry. What type of router is it? Point that out and we may be able to give you more help ;)

~Zeke

---

### Post by roelforg on 2012-04-16
Get someone with a laptop/cell/pda/etc with wireless to stop by and see if their device can connect, chances are theirs can't either and this isn't ubuntu's fault.

---

### Post by Danieltba on 2012-04-16
Solved, simply changed the channel of the wireless, maybe the driver isnt very fine tuned for my card. Thank you very much.

---

### Post by roelforg on 2012-04-16
> **Danieltba said:**
> Solved, simply changed the channel of the wireless, maybe the driver isnt very fine tuned for my card. Thank you very much.

Maybe someone else was using that channel? They could interfer with you that way.

---

