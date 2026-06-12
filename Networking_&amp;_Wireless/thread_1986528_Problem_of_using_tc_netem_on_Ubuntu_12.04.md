---
title: "Problem of using tc netem on Ubuntu 12.04"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by Jionghui on 2012-05-25
Hi all,
 
I would like to emulate packet delay and loss for UDP on Ubuntu 12.04 to measure the performation of an application. 
 
Following some suggestion, I choose to use netem leverages functionality which is already built into Linux.
 
However, when I run
 
*# tc qdisc change dev eth0 root netem loss 0.1%*
 
It shows "**RTNETLINK answers: Operation not permitted**". Any one knows why and how to fix it? Please help me. Thank you very much.

---

