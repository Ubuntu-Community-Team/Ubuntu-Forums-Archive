---
title: "network card driver on HP ML115 G5 server"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by pubsoftware on 2009-09-17
Hello,  I have ubuntu 8.04 server installed on an HP ML115 G5, but unfortunately no Ethernet driver.

dmesg | grep eth

eth0: Tigon3 [partno(N/a) rev a200 PHY(5722/5756)] (PCI Express) 10/100/1000Base-T Ethernet
eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] WireSpeed[1] TSOcap[1]
eth0: dma_rwctr[76180000] dma_mask[64-bit]

Just wondering if anyone has been able to get this working ...

Ubuntu list this server as valid hardware - [http://webapps.ubuntu.com/certification/hardware/200712-186/](http://webapps.ubuntu.com/certification/hardware/200712-186/)

There are RPM drivers for Redhat and SUSE on the HP website but I don't think these can be used with Ubuntu.

Any help appreciated.
Colin

---

### Post by chili555 on 2009-09-17
There is a driver built in to the kernel for this card. Perhaps it didn't get loaded. Please try:```
sudo modprobe tg3
ifconfig
```Was an interface, eth0, perhaps, created? If so, please do:```
sudo dhclient eth0
```Did you connect? If merely loading the lazy module works, we can make it permanent by adding *tg3* to */etc/modules*.

I don't have this card, so I can't offer an opinion on whether *tg3* works well or at all.

---

### Post by pubsoftware on 2009-09-17
perfect thanks chili,

the commands above worked!

driver still loaded after a restart

cheers
:P

---

