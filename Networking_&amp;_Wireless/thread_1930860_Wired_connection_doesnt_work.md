---
title: "Wired connection doesnt work"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by thebrandon on 2012-02-24
I normally have no use for having a wired ethernet connection but I have been experimenting with dd-wrt on my router and I am about to try openwrt and I cant use my wired connection in ubuntu, I have to boot into windows.  I have poked around in Network Connections and nothing seems out of the ordinary, how can I get it up and working so I dont have to fight with windows?

---

### Post by sanderj on 2012-02-24
Things to check and post:

dmesg: relevant messages about the network card (probably eth)
ifconfig
lspci

---

### Post by roelforg on 2012-02-24
```

sudo bash
ifconfig -a
cat /etc/network/interfaces
uname -a
cat /etc/resolv.conf
lshw -C network

```

---

### Post by thebrandon on 2012-02-25
Thank you!  Works perfectly!

---

