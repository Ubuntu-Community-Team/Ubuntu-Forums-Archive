---
title: "Broken connections never reset for ICMP ping or IM"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by Taemojitsu on 2010-07-13
Is this normal behavior? If my router resets (Tomato on WRT54GL with standard NAT/firewall), my applications in Ubuntu seem to never 'detect' it.

1) 'ping -f google.com -i 1' gives a series of dots after the router resets. using a normal 'ping google.com' will cause nothing to show after the router resets, unless the connection on Ubuntu connection manager is broken in which case it will begin to display destination unreachable messages. 15 minutes after resetting it is still printing '.........', and earlier on a series of E's which I assume were destination unreachable error messages.


2) Pidgin (both with 2.6.6, and with the latest 2.7.1) does not refresh connections to MSN either, for at least 15 minutes after the connection breaks. If you use it, you will appear to be connected to the server but messages and status updates are not sent or received.


Are these application-specific problems, a problem with Ubuntu settings, a result of the way Tomato handles unregistered port connections, or just the way connections to the Internet work when broken?


UPDATE: It seems problem with the way Lucid handles overflows or something. I know wireless worked differently with errors in 9.10, I think ping errors are different too. Using an interval of 10 does not cause the connection to 'break' when I restart my router. One dot (= missed packet) is printed with an interval of 10, but after that no further packets are missed. But a ping running simultaneously with interval of 1 does not resume normal working order after the router restarts, but continues to print a series of dots.

Similarly, sending updated information on MSN in Pidgin while the router is down causes the connection to 'break'. If no information is sent, after the router is finished restarting update information and conversations are sent and received normally.

---

