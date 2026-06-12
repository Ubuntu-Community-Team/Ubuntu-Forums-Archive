---
title: "Netgear wg602v4 and ubuntu 10.04 64 bit help..."
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by uncooldrewl on 2010-11-25
Hello guys

I'm having a lot of troubles to get this access point working. I just plugged it in, but ubuntu doesn't recognize it, it stays for min in " eth0 loading " and then it just says wired network offline, it seems to me like some issue with the dhcp server, i have a netgear dg834g v3 and it works perfectly as soon as i plug it in, no problems, it just works. On the other hand there is no way i can get the wg602 working, i tried millions time to reset it etc but nothing, i'd like to know if i gotta set some static ip or what... im really stuck here.

here the /var/log/messages if it can help:

```

Nov 25 19:58:35 frank-laptop kernel: [22089.146551] tg3: eth0: Link is up at 100 Mbps, full duplex.
Nov 25 19:58:35 frank-laptop kernel: [22089.146558] tg3: eth0: Flow control is on for TX and on for RX.

```thanks for any help

---

### Post by uncaspi on 2010-11-25
Your wired connection works? Possible something with your driver. Let's see what lsusb say,please post

---

