---
title: "Communication between computers on LAN"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by charlie cat on 2011-09-24
I need help with sending UDP packets between 2 computers on the same LAN, but where both of the computers are sending the packets to the router's IP instead of their internal IP's.  Port numbers distinguish the computers.
Oddly, this works correctly when a Windows 7 machine is sending the packets, but not when an Ubuntu 11.04 or a Windows XP computer are sending packets.  When these computers send the packets, they appear to be routed correctly (as far as the sender can tell), but the packets never reach their destination.
Using the external IP of the router works in a simple test program I have, but not in my actual application, so I'm hoping I can get this method to work instead.

Further info: the program is a Java program, running on j2se 1.6 on both computers.
All ports have been forwarded correctly, and both computers have static internal IP's.
My router is a Broadcom WRT64G.

Can anyone shed light on this?

---

