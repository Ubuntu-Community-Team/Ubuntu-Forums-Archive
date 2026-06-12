---
title: "Wireless working, wired  not"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by Ludachrispeed on 2009-03-21
For a long time now, I have not been able to connect with a wired connection.  In wicd, it gets stuck on "Obtaining IP address..." 

I think this shows important information, but I'm not sure how to interpret it. Can anyone help me out?

dmesg | grep eth0
```

[    2.484755] eth0: Tigon3 [partno(BCM5752KFBG) rev 6002 PHY(5752)] (PCI Express) 10/100/1000Base-T Ethernet 00:15:c5:a8:23:80
[    2.484761] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    2.484764] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   28.504567] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.257161] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   30.257172] tg3: eth0: Flow control is on for TX and on for RX.
[   30.257574] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.602001] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.139134] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   33.139142] tg3: eth0: Flow control is on for TX and on for RX.
[   33.139516] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   43.464075] eth0: no IPv6 routers present
[ 1235.672571] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1236.301855] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1237.838273] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1237.838275] tg3: eth0: Flow control is on for TX and on for RX.
[ 1237.838503] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1242.542476] tg3: eth0: Link is down.
[ 1244.203765] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1244.203767] tg3: eth0: Flow control is on for TX and on for RX.
[ 1248.128124] eth0: no IPv6 routers present
[ 1252.696989] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1254.359816] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1254.359823] tg3: eth0: Flow control is on for TX and on for RX.
[ 1254.360042] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1264.812119] eth0: no IPv6 routers present


```

Thanks in advance! Any help is appreciated!

---

### Post by jeremyjjbrown on 2009-03-22
I have this problem on my MSI WIND with the newest kernel. Rather than mess about I just boot to the previous kernel. Maybe you can try loading an older kernel.

---

### Post by Ludachrispeed on 2009-03-22
That's a really good idea!  Thanks, I'll try that as soon as I get home.

---

### Post by kvelandia on 2009-05-15
I have the opposite problem. Wired works wireless doesn't.

I have tried changing the WPA supplicant driver, each possible combination and I still can not get wireless connections.

It either gets stuck on validating authentication or obtaining ip address.

---

