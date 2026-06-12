---
title: "Help deciphering a traceroute result please"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by cryptotheslow on 2012-02-12
Hi

Can anyone shed some light on what is going on with hop 8 here?

```
traceroute to 69.4.225.224 (69.4.225.224), 30 hops max, 60 byte packets
 1  192.168.1.254 (192.168.1.254)  4.427 ms  3.922 ms  3.889 ms
 2  * * *
 3  * * *
 4  bbr01.lon01.networklayer.com (195.66.225.183)  20.460 ms  21.041 ms  22.140 ms
 5  ae1.bbr02.tl01.nyc01.networklayer.com (50.97.18.204)  97.294 ms  98.238 ms *
 6  ae7.bbr01.tl01.nyc01.networklayer.com (173.192.18.176)  173.905 ms  170.672 ms  171.945 ms
 7  ae1.bbr01.eq01.wdc02.networklayer.com (173.192.18.156)  93.168 ms  93.061 ms  92.638 ms
 8  ae0.dar01.sr01.wdc01.networklayer.com (173.192.18.197)  92.396 ms ae0.dar02.sr01.wdc01.networklayer.com (173.192.18.203)  97.560 ms  98.500 ms
 9  po1.fcr02.sr01.wdc01.networklayer.com (208.43.118.149)  94.369 ms  94.349 ms  95.192 ms10  69.4.225.224 (69.4.225.224)  98.463 ms  99.786 ms  99.760 ms
```Those 2 hosts on hop 8 seem to randomly change places, but both are always there on the same hop.

Is this just a brain-fart from traceroute or is it like that for some some genuine reason? Never seen a result like that before :confused:

Thanks :)

---

