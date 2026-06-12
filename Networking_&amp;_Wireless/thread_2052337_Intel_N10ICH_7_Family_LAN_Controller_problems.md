---
title: "Intel N10/ICH 7 Family LAN Controller problems"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by NRV on 2012-09-03
hi. need help. recently did a clean install of Ubuntu 12.04.1 on a Shuttle X200 desktop. this has built-in wireless and ethernet. lspci shows the ethernet card to be an Intel N10/ICH 7 Family LAN Controller. network manager doesn't show the connection even though a working LAN cable is connected to it. the wifi does work but i need to have this desktop on a cable connection. tia.

---

### Post by chili555 on 2012-09-03
What does this tell us?```
lspci -nn | grep 0200
```Thanks.

---

### Post by NRV on 2012-09-03
> **chili555 said:**
> What does this tell us?```
lspci -nn | grep 0200
```Thanks.

01:08.0 Ethernet controller [0200]: Intel Corporation N10/ICH 7 Family LAN Controller [8086:27dc] (rev 02)

also. ```
lshw
``` shows:

           *-network UNCLAIMED
                description: Ethernet controller
                product: N10/ICH 7 Family LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=64 maxlatency=56 mingnt=8
                resources: memory:fbfff000-fbffffff ioport:ef00(size=64)

---

### Post by chili555 on 2012-09-03
This device works with the driver e100. If it is not loading automatically, there may be something wrong. Hook up the ethernet cable and do:```
sudo modprobe e100
```And check for warnings or other clues:```
dmesg | grep e100
```Thanks.

---

### Post by NRV on 2012-09-05
thanks. will try this.

---

