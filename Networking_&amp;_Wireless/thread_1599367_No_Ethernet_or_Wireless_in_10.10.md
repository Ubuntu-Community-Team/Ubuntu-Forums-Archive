---
title: "No Ethernet or Wireless in 10.10"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by Chameco on 2010-10-17
Hello. I have been using Ubuntu for quite a while now (~3 years.) I recently installed 10.10 on an HP Mini 1000. The installation went fine, but now I am puzzling over how to connect to the internet. When I plug an ethernet cable into the netbook, the port light lights up, but the system does absolutely nothing. Under the connections menu on the top panel, it just says disconnected. Also, the wireless connection section states that the device is not ready because firmware is not installed. Most solutions I see for problems of this kind are to download the drivers, but I cannot do that because neither connection works. Please help!

---

### Post by Iowan on 2010-10-17
Some things to check:
**sudo lshw -C network** for hardware information
**ifconfig -a** to see if the system acknowledges either/both interface(s).

---

