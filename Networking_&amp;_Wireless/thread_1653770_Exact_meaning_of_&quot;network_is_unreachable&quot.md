---
title: "Exact meaning of &quot;network is unreachable&quot;?"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by hodad on 2010-12-27
I've been having a lot of trouble with getting wireless networking devices to work. I guess I have  a lot of company, since mfrs don't seem to be very interested in supporting Linux.

It seems that one common symptom is that, when I try to "Ping" using the Terminal, I get "network is unreachable".

Does this mean anything specific, or is it a general output whenever the network is not carrying on two way communications?  Does it mean that the wireless interface is down? Does it mean that the wireless hardware is not transmitting?  Not receiving?  Does it point to a driver problem?

It could be a useful troubleshooting tool if I just knew what it is pointing to.

Thanks!

---

### Post by dandnsmith on 2010-12-27
It means that the IP address you've called for requires routing for which there is no entry.

If you gave a name (requiring lookup to turn into IP address) then it may be that the DNS lookup server cannot be reached.

Things to check are the IP address assigned to your network interface, and the routing table entries.
For these I use command line stuff (ifconfig and route), but others may prefer network tools.

---

### Post by hodad on 2010-12-27
Thanks for the reply; your answer points me in the right direction.

I'll look into routing tables (heard of them, but haven't delved into).  Maybe I'll also try iwconfig with both essid and IP address options.   

Again, Thanks!

---

### Post by Iowan on 2010-12-29
From a terminal, the **route** command (and **man route**) might be useful. :)

---

