---
title: "Ndiswrapper problem again"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-03-18
I don't know which driver is being loaded. There's a folder inside /etc/ndiswrapper named netrtuw. In side the folder netrtuw there are many .conf file
```

coppen@coppen-laptop:/etc/ndiswrapper/netrtuw$ ls
0769:11F2.F.conf  0DF6:000D.F.conf  13D1:ABE6.F.conf  rtl8187.sys
0789:010C.F.conf  114B:0150.F.conf  18E8:6232.F.conf
0BDA:8187.F.conf  1371:9401.F.conf  netrtuw.inf

```
And ndiswrapper -l shows this
```

netrtuw : driver installed
	device (0BDA:8187) present (alternate driver: rtl8187)

```
Is the driver installed properly?

lshw -C network tells nothing about the driver version
```
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:43:74:7b:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.123.10 multicast=yes wireless=IEEE 802.11bg

```

---

### Post by Ayuthia on 2009-03-18
Does ```
lsmod|grep ndiswrapper
```return anything, if not, then ndiswrapper is not loaded.

---

### Post by afeasfaerw23231233 on 2009-03-21
My problem seems solved

[http://ubuntuforums.org/showthread.php?p=6932570#post6932570](http://ubuntuforums.org/showthread.php?p=6932570#post6932570)

---

