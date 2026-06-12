---
title: "non-stop error message in /var/log/messages relate to a windows client/"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by odror on 2012-05-16
OS: ubuntu 12.04

I have a windows 7 machine (192.168.0.16) on my local network (eth2) . I continously get this error message in /var/log/messages.
> May 16 19:16:12 linux-machine kernel: [43104.242199] Unknown InputIN=eth2 OUT= MAC=01:00:5e:7f:ff:fa:70:71:bc:78:5e:31:08:00 SRC=192.168.0.16 DST=239.255.255.250 LEN=684 TOS=0x00 PREC=0x00 TTL=1 ID=18403 PROTO=UDP SPT=52505 DPT=3702 LEN=664
What does it means? How I can I stop it. It fill my SSD drive with garbage. It also makes my massages file difficult to read because it is mostly trash like this message. It looks thatit is related to UPNP

---

### Post by chili555 on 2012-05-17
> May 16 19:16:12 linux-machine kernel: [43104.242199] Unknown InputIN=eth2 OUT= MAC=01:00:5e:7f:ff:fa:70:71:bc:78:5e:31:08:00 SRC=192.168.0.16 [COLOR="Red"]DST=239.255.255.250[/COLOR] LEN=684 TOS=0x00 PREC=0x00 TTL=1 ID=18403 PROTO=UDP SPT=52505 DPT=3702 LEN=664 Please see: [http://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol](http://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol)> In IPv4, the multicast address is [COLOR="Red"]239.255.255.250[/COLOR] and SSDP over IPv6 uses the address set ff0X::c for all scope ranges indicated by X.I doubt it's an error. I think your machines are telling each other that they have files to share, a printer to share, etc. I'm not sure how to get rid of the messages and keep the services.

---

### Post by odror on 2012-05-17
> **chili555 said:**
> Please see: [http://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol](http://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol)I doubt it's an error. I think your machines are telling each other that they have files to share, a printer to share, etc. I'm not sure how to get rid of the messages and keep the services.

It would be nice to turn these messages off. These messages take more than 90% of /var/log/messages. It is difficult to trace error in the system when there are so many useless messages.

---

