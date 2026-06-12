---
title: "Ethernet Connection Problem in Jaunty"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by Goveynetcom on 2009-12-12
Sometime ago, I came here with a problem. For some reason or another my ubuntu installation wasn't allowing any type of connection at all to my router, then to the internet. I installed my new router and I have tested the ethernet ports and they work. In fact I have gotten my Live CD to connect (which is what I'm using to type this message), but I still can't get my normal connection to work. I looked through the routing info on this connection setup and it looks exactly my connection on the full install, but that one still doesn't work. I'm stumped on this and haven't used my ubuntu machine to connect to the internet in about a month. I have tried again and again to get it working and no success. I have no idea what to do and really need some assistance. Please help!!!

---

### Post by uncaspi on 2009-12-12
Do you see the network manager icon up to the right in the panel? You can add it by right click in the panel and choose add. Will you also post sudo /sbin/ifconfig and lshw -C network and dmesg | grep -e eth -e wlan

---

