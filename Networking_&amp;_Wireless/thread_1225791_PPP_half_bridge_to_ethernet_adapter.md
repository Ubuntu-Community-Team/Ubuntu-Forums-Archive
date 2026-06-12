---
title: "PPP half bridge to ethernet adapter"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by graynetwork on 2009-07-28
Basicly want I want to do is create a ppp half-bridge to my ethernet adapter. What I plan to use the ubuntu box for is ml-ppp (to bond my adsl connections) I haven't had any issues getting that going but im pretty sure I can't just bridge ppp and ethernet since there 2 different protocols. What ive been reading says I should use a half bridge.


Iwant I want is when I plug into my ethernet port on the machine it be the same as the pppoe connection, I static one of the ip's from my range my isp has provided to me then enter the ip address of my isp's ERX router on the other end as the gateway. Then I have internet connectivity with my external ip address, and im not running through iptables or a router or anything similar.

 My work currently has this setup on a cisco 2521 router but we want something with more network interfaces so we can increase the multi-link bundle size from 4x6meg connections to 6x6meg connections.

---

