---
title: "Transmission Download Speed: 40 MBPS"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by DeusExM1 on 2009-05-03
Hey everyone,

My transmission download speed and upload speeds are incorrect. They are actually quite slow but it displays even as high as 40 MBPS. I have moblocker installed. I tried port forwarding via router, but it still says i have the "incoming" port closed. 

So how should i go about:

1. Making transmission report correct download/upload speeds
2. Increasing download speeds (I have cable and im getting like 20 KBPS). 

I have attached the screenshot for you guys to see.


I figured out that my WRT54GS wireless router was to blame. I port forwarded BOTH (tcp and udp) port for transmission. The important part was to make sure that at least 2 ports were entered ie: 6112 - 6113.  (before that i had 6112-6112).  These are just examples i used the Regular Transmission Port.

---

