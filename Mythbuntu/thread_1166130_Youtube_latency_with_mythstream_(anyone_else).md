---
title: "Youtube latency with mythstream (anyone else?)"
date: 2009-05-21
forum: Mythbuntu
---

### Post by sr_guy on 2009-05-21
Anyone else notice horrible latency and choppiness on youtube using mythstream the last day or so?

Here's my traceroute, and top shows no cpu utilization issues:

traceroute to [www.youtube.com](www.youtube.com) (208.65.153.253), 30 hops max, 60 byte packets
 1  sr_guy (192.168.1.1)  1.174 ms  1.315 ms  1.510 ms
 2  c-3-0-ubr02.ypeast.mi.michigan.comcast.net (73.40.48.1)  10.411 ms  10.761 ms  11.096 ms
 3  ge-2-2-ur02.ypeast.mi.michigan.comcast.net (68.87.184.185)  11.365 ms  14.380 ms  14.714 ms
 4  te-0-1-0-5-ar01.taylor.mi.michigan.comcast.net (68.87.190.141)  15.397 ms  15.728 ms  16.001 ms
 5  pos-0-5-0-0-cr01.cleveland.oh.ibone.comcast.net (68.86.90.105)  18.517 ms  22.486 ms  22.820 ms
 6  pos-0-8-0-0-cr01.chicago.il.ibone.comcast.net (68.86.85.50)  32.786 ms  24.895 ms  24.540 ms
 7  pos-0-1-0-0-pe01.350ecermak.il.ibone.comcast.net (68.86.86.38)  29.388 ms  30.184 ms  32.109 ms
 8  te4-3.ccr02.ord03.atlas.cogentco.com (154.54.11.253)  30.928 ms  31.209 ms  24.629 ms
 9  youtube.demarc.cogentco.com (38.112.0.102)  109.281 ms !X * *


root@mythbuntu:~# top -n 1 | grep "Cpu"
Cpu(s):  2.5%us,  1.3%sy,  4.7%ni, 90.2%id,  1.2%wa,  0.1%hi,  0.0%si,  0.0%st
root@mythbuntu:~#

---

