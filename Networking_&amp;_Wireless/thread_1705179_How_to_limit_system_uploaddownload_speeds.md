---
title: "How to limit system upload/download speeds"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by scross on 2011-03-11
I'm looking for a mechanism to accurately limit the upload/download speeds of the entire system (local computer) to specific upper bounds. I've looked at wondershaper which seems to be inaccurate and do lots of unnecessary bandwidth shaping (I just need to limit the bandwidth - nothing else), and I've looked at trickle, which doesn't apply for all applications on the system. The approach shouldn't rely on any hardware, and it should be easy to change the limit via the command line at any point. I've tried using 'tc', to no avail - particularly because filters must apply rules, whereas I want to filter all traffic.

---

