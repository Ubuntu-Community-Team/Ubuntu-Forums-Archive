---
title: "Gbit network speed not the same in different directions"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by zarqoon on 2010-10-23
Situation:
Two Systems both Lucid.
2.6ghz Athlon 2 X4
1.6ghz Atom Dualcore
TPLink 5Port GBit Switch.
Brand new 3m cat5e s/ftp cables on both systems.

In the process of optimizing the nfs perfomance with the Atom as the server i measured the network speed with setting up a port
```
nc -ul 5000 > /dev/null
```
On one side and sending to it
```
pv < /dev/zero | nc -u IP_ADDRESS 5000
```
on the other.

With the Atom listening i get a transfer rate of 109MB/s which is not the theoretical maximum but near enough.
If i try the same with the X4 Listening i get only around 40MB/s.

I've got the same discrepancy with nfs file transfers. While fiddling with the settings i got the speed of writing to the atom up to 80MB/s but reading speed is only 40MB/s. Local Disc1 to Disc2 transfer on the Atom is about 100MB/s so Disc speed should not be the bottleneck.

While i can live with these speeds i think the difference in speed depending on the direction is weird but can not find out what causes it.
Anyone got ideas?

---

