---
title: "VLC ignores UDP multicast traffic"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by AlexDragon on 2009-08-13
Hello, 

I have a strange problem with vlc under ubuntu 8.04 (seems to happen on 8.10 and 9.04 too). I have the interface eth0.10, with 224.0.0.0/4 routed on it. When I ask vlc to join a multicast stream, it does so, but it doesn't receive any traffic. However, i can se the traffic comming on port 1234 with tcpdump. I don't know of any security setup in linux kernel that stops the traffic to go from network layer to app layer (vlc in this case). I really don't know how to solve it or how to debug this.

---

### Post by superprash2003 on 2009-08-13
do you run firestarter , gufw or anything similar?

---

### Post by AlexDragon on 2009-08-13
I don't have any firewall, but you gave me a great idea :) Seems it was rp_filter :(((

---

