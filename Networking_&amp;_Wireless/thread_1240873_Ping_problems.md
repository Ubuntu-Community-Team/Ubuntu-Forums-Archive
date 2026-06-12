---
title: "Ping problems"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by Spikerok on 2009-08-15
after installing router which supposed to be better my ping gone up to 50ish on servers like dustworld when before on basic modem with 1mb connection ping was 10-20.
What can be done to reduce my ping?
router 3mb and connected by wire.


trace to google.co.uk
|------------------------------------------------------------------------------------------|
| WinMTR statistics |
| Host - % | Sent | Recv | Best | Avrg | Wrst | Last |
|------------------------------------------------|------|------|------|------|------|------|
| dsldevice.lan - 0 | 237 | 237 | 0 | 46 | 110 | 47 |
| 92.22.160.1 - 0 | 237 | 237 | 31 | 47 | 94 | 47 |
| 92.31.253.110 - 1 | 237 | 236 | 31 | 50 | 125 | 47 |
| xe-11-2-0-scr001.log.as13285.net - 3 | 237 | 232 | 31 | 52 | 125 | 47 |
| xe-11-0-0-scr010.sov.as13285.net - 4 | 237 | 228 | 31 | 49 | 125 | 47 |
| google-pp-sov.as13285.net - 1 | 237 | 235 | 46 | 52 | 141 | 47 |
| 209.85.255.175 - 5 | 236 | 225 | 32 | 54 | 156 | 47 |
| 209.85.250.216 - 4 | 236 | 228 | 46 | 63 | 156 | 63 |
| 66.249.95.169 - 3 | 236 | 231 | 46 | 60 | 109 | 62 |
| 216.239.49.126 - 1 | 236 | 234 | 46 | 67 | 141 | 78 |
| gv-in-f104.google.com - 2 | 236 | 233 | 46 | 60 | 125 | 62 |
|________________________________________________|______|______|______|______|______|______|
WinMTR - 0.8. Copyleft @2000-2002 Vasile Laurentiu Stanimir ( [email]stanimir@cr.nivis.com[/email] )


trace to bbc.co.uk
|------------------------------------------------------------------------------------------|
| WinMTR statistics |
| Host - % | Sent | Recv | Best | Avrg | Wrst | Last |
|------------------------------------------------|------|------|------|------|------|------|
| dsldevice.lan - 0 | 257 | 257 | 0 | 49 | 110 | 16 |
| 92.22.160.1 - 0 | 257 | 257 | 31 | 46 | 94 | 47 |
| 92.31.253.78 - 0 | 257 | 257 | 31 | 50 | 141 | 47 |
| xe-11-2-0-scr001.log.as13285.net - 1 | 257 | 255 | 31 | 53 | 156 | 62 |
| xe-10-2-0-scr010.sov.as13285.net - 1 | 256 | 255 | 31 | 51 | 141 | 47 |
| bbc-pp-sov.as13285.net - 4 | 256 | 248 | 31 | 54 | 203 | 63 |
| 212.58.238.133 - 3 | 256 | 250 | 32 | 53 | 313 | 47 |
| virtual-vip.thdo.bbc.co.uk - 2 | 256 | 253 | 31 | 47 | 94 | 47 |
|________________________________________________|______|______|______|______|______|______|
WinMTR - 0.8. Copyleft @2000-2002 Vasile Laurentiu Stanimir ( [email]stanimir@cr.nivis.com[/email] )



Router is THOMSON ST585v6sl, connected by wire.
Trace which i have made is just after starting my pc.
I believe some thing wrong.

Linux traceroute to google.co.uk - different pc

traceroute to google.co.uk (72.14.221.104), 30 hops max, 40 byte packets
1 dsldevice.lan (192.168.1.254) 91.527 ms 91.077 ms 90.580 ms
2 92.22.160.1 (92.22.160.1) 49.236 ms 53.363 ms 56.320 ms
3 92.31.252.110 (92.31.252.110) 58.326 ms 60.419 ms 63.194 ms
4 xe-11-2-0-scr002.log.as13285.net (78.144.2.131) 69.308 ms 71.361 ms 74.216 ms
5 xe-11-0-0-scr010.thn.as13285.net (78.144.1.0) 78.170 ms 82.061 ms xe-10-2-0-scr010.thn.as13285.net (78.144.1.2) 86.256 ms
6 host-78-144-3-30.as13285.net (78.144.3.30) 87.979 ms 47.166 ms google-pp-thn.as13285.net (78.144.3.2) 78.819 ms
7 64.233.175.27 (64.233.175.27) 50.987 ms 50.892 ms 50.827 ms
8 209.85.250.54 (209.85.250.54) 125.190 ms 123.923 ms 144.776 ms
9 209.85.251.9 (209.85.251.9) 140.963 ms 138.892 ms 137.997 ms
10 72.14.232.215 (72.14.232.215) 139.407 ms 139.561 ms 142.654 ms
11 fg-in-f104.google.com (72.14.221.104) 145.116 ms 145.534 ms 138.687 ms


______________
traceroute to bbc.co.uk

traceroute to bbc.co.uk (212.58.224.138 ), 30 hops max, 40 byte packets
1 dsldevice.lan (192.168.1.254) 57.919 ms 57.463 ms 56.999 ms
2 92.22.160.1 (92.22.160.1) 52.464 ms 55.475 ms 61.130 ms
3 92.31.253.78 (92.31.253.78 ) 61.767 ms 62.570 ms 63.292 ms
4 xe-11-2-0-scr001.log.as13285.net (78.144.2.3) 68.428 ms 72.298 ms 74.226 ms
5 xe-10-2-0-scr010.sov.as13285.net (78.144.0.216) 77.221 ms 81.091 ms 83.097 ms
6 bbc-pp-sov.as13285.net (78.144.5.1) 86.263 ms 46.719 ms 49.939 ms
7 212.58.238.133 (212.58.238.133) 51.366 ms 52.883 ms 47.573 ms

---

### Post by dlmarti on 2009-08-15
You didn't give your router type before and after.
WinMTR is a windoze program not Linux.
You didn't show your traceroute info before and after.

Without this its impossible to debug what changed.

---

### Post by Spikerok on 2009-08-15
Router is THOMSON ST585v6sl, connected by wire.
Trace which i have made is just after starting my pc.
I believe some thing wrong.

If you want i can give trace from ubuntu, not sure if it will be different

---

### Post by Spikerok on 2009-08-15
Linux traceroute to google.co.uk

traceroute to google.co.uk (72.14.221.104), 30 hops max, 40 byte packets
 1  dsldevice.lan (192.168.1.254)  91.527 ms  91.077 ms  90.580 ms
 2  92.22.160.1 (92.22.160.1)  49.236 ms  53.363 ms  56.320 ms
 3  92.31.252.110 (92.31.252.110)  58.326 ms  60.419 ms  63.194 ms
 4  xe-11-2-0-scr002.log.as13285.net (78.144.2.131)  69.308 ms  71.361 ms  74.216 ms
 5  xe-11-0-0-scr010.thn.as13285.net (78.144.1.0)  78.170 ms  82.061 ms xe-10-2-0-scr010.thn.as13285.net (78.144.1.2)  86.256 ms
 6  host-78-144-3-30.as13285.net (78.144.3.30)  87.979 ms  47.166 ms google-pp-thn.as13285.net (78.144.3.2)  78.819 ms
 7  64.233.175.27 (64.233.175.27)  50.987 ms  50.892 ms  50.827 ms
 8  209.85.250.54 (209.85.250.54)  125.190 ms  123.923 ms  144.776 ms
 9  209.85.251.9 (209.85.251.9)  140.963 ms  138.892 ms  137.997 ms
10  72.14.232.215 (72.14.232.215)  139.407 ms  139.561 ms  142.654 ms
11  fg-in-f104.google.com (72.14.221.104)  145.116 ms  145.534 ms  138.687 ms


______________
traceroute to bbc.co.uk

traceroute to bbc.co.uk (212.58.224.138 ), 30 hops max, 40 byte packets
 1  dsldevice.lan (192.168.1.254)  57.919 ms  57.463 ms  56.999 ms
 2  92.22.160.1 (92.22.160.1)  52.464 ms  55.475 ms  61.130 ms
 3  92.31.253.78 (92.31.253.78 )  61.767 ms  62.570 ms  63.292 ms
 4  xe-11-2-0-scr001.log.as13285.net (78.144.2.3)  68.428 ms  72.298 ms  74.226 ms
 5  xe-10-2-0-scr010.sov.as13285.net (78.144.0.216)  77.221 ms  81.091 ms  83.097 ms
 6  bbc-pp-sov.as13285.net (78.144.5.1)  86.263 ms  46.719 ms  49.939 ms
 7  212.58.238.133 (212.58.238.133)  51.366 ms  52.883 ms  47.573 ms

---

### Post by Spikerok on 2009-08-15
I think some thing wrong with router.. from the start ping from 50 to 100 on the router

---

### Post by Spikerok on 2009-08-15
bump

---

### Post by Spikerok on 2009-08-15
bump

---

### Post by Spikerok on 2009-08-16
bump

---

### Post by Spikerok on 2009-08-16
bump

---

### Post by Spikerok on 2009-08-22
bump

---

### Post by Spikerok on 2009-08-23
bump

---

