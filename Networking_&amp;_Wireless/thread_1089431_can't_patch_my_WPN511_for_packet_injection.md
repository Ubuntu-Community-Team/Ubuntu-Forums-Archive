---
title: "can't patch my WPN511 for packet injection"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by K-a-M-u-Z-u on 2009-03-07
i'm working on ubuntu 8.10 on a thinkpad R40 with two WIRELESS CARDS:
1.Built-in ipw2100.
2.PCMCIA Netgear WPN511.

i want to try cracking my own WEP router(D-link 614+) because i always hear its so easy to crack it.
i have read allot of guides, and seen allot of videos, and it really seems easy.
so i'm able to start the aircrack suite and capture data packets with my IPW2100, but the rate of the packets is extremly low.(left it for two day and got around 100+ IVS)
i know i have to patch the WPN511 with the madwifi patch so i could inject packets to make it go faster, but i just cant.
When i input:
```
 sudo  patch -N -p 0 -i madwifi-ng-r3925.patch
```
i get the next error:
```
patching file ath/if_ath.c
Hunk #1 FAILED at 3002.
Hunk #2 FAILED at 3015.
Hunk #3 FAILED at 3040.

```
no matter what, i just can't find any good guide or methood for patching it.
thnx.

---

