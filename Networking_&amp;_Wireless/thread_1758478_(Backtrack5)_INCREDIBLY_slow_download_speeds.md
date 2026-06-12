---
title: "(Backtrack5) INCREDIBLY slow download speeds?"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by drackor1991 on 2011-05-14
Alright, just got a small netbook around the time BT5 came out, decided to test it out. Only to find out my internet is INCREDIBLY slow. We're talking 20 kb/s download speed or less, on ANY download source.
I googled around and found my router maybe being used as a nameserver. 

nano /etc/resolv.conf
And sure enough it is. I change them to my ISP's dns's and it helps pages load faster but download speed is still terrible. I tried changing them to OPENdns, and same thing.
Getting a 1 mb/s down and 3 mb/s up on speedtest (on windows It's like 4 mb/s down and 4 mb/s up)

Here's two traceroutes I ran to google and youtube.

**root@bt:~#** traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (74.125.93.147), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  3.616 ms *  13.930 ms
 2  ip70-173-238-1.lv.lv.cox.net (70.173.238.1)  25.110 ms  25.116 ms  25.076 ms
 3  24-234-8-93.ptp.lvcm.net (24.234.8.93)  24.708 ms  24.633 ms  24.580 ms
 4  24-234-6-61.ptp.lvcm.net (24.234.6.61)  24.636 ms  25.301 ms 24-234-6-177.ptp.lvcm.net (24.234.6.177)  25.946 ms
 5  langbprj02-ae1.rd.la.cox.net (68.1.1.15)  32.546 ms  32.356 ms  32.339 ms
 6  209.85.248.187 (209.85.248.187)  30.331 ms * 209.85.248.185 (209.85.248.185)  18.752 ms
 7  64.233.174.190 (64.233.174.190)  25.415 ms 64.233.174.192 (64.233.174.192)  25.147 ms 64.233.174.186 (64.233.174.186)  25.200 ms
 8  64.233.174.145 (64.233.174.145)  78.209 ms 64.233.174.147 (64.233.174.147)  82.083 ms  81.800 ms
 9  209.85.254.46 (209.85.254.46)  89.275 ms  88.893 ms *
10  209.85.254.235 (209.85.254.235)  84.728 ms 209.85.254.237 (209.85.254.237)  98.883 ms *
11  * * 64.233.174.182 (64.233.174.182)  81.208 ms
12  qw-in-f147.1e100.net (74.125.93.147)  75.736 ms  75.502 ms  76.324 ms

**root@bt:~#** traceroute [www.youtube.com](www.youtube.com)
traceroute to [www.youtube.com](www.youtube.com) (74.125.224.192), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.705 ms  3.604 ms  5.021 ms
 2  ip70-173-238-1.lv.lv.cox.net (70.173.238.1)  22.543 ms  22.540 ms  22.589 ms
 3  24-234-8-89.ptp.lvcm.net (24.234.8.89)  22.320 ms  22.308 ms  22.279 ms
 4  24-234-6-233.ptp.lvcm.net (24.234.6.233)  22.300 ms  22.270 ms  22.221 ms
 5  langbprj02-ae1.rd.la.cox.net (68.1.1.15)  27.363 ms  27.222 ms  54.076 ms
 6  209.85.248.187 (209.85.248.187)  27.075 ms  17.925 ms  17.328 ms
 7  72.14.236.13 (72.14.236.13)  17.086 ms  21.889 ms  21.692 ms
 8  74.125.224.192 (74.125.224.192)  21.120 ms  20.810 ms  20.505 ms

Also lspci for my wireless:
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)




So....just basically asking if ANYBODY has help for me, or at least the next step I should be taking?

---

