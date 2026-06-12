---
title: "Duplicate Pings with Virtualbox - Ubuntu Guest"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by wareagle on 2009-10-13
I am running Virtualbox on Windows XP with a Ubuntu guest. It has bridged networking. Whenever I ping any server, I get duplicate pings.

The only thing that doesn't give me a duplicate ping is the host computer's IP address.

When I open the capture in Wireshark, I see that I am getting ICMP redirects from my host computer's IP and it is redirecting me to my default gateway. However, a 'route -n' reveals that my default gateway is already what it should be (not the host computer).

Any idea why this is?

---

