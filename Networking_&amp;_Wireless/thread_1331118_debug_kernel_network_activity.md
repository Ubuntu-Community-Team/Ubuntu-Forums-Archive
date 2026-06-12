---
title: "debug kernel network activity?"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by thinking on 2009-11-19
hi

im wondering myself how to debug the kernel so that i know how a packet
travels through the kernel
at work i was confronted with a situation where the kernel just droped packets during connection initializiation
in a wild guess of mine i disabled tcp_timestamps and tcp_window_scaling
which solved the problem

now i have the question:
given a situation where i know the kernel is causing the problem
how do i know the path of the packets through the kernel
so i dont have to guess which knob to turn,
but i can really know and understand the mechanisms and its knobs to solve it?

thx

---

