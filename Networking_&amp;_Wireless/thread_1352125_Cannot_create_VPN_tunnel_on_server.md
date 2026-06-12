---
title: "Cannot create VPN tunnel on server"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by Martin B on 2009-12-11
I just did a fresh reinstall of 9.10 on my server which previously ran 8.10 with a working VPN setup, Relakks as the provider. My problem is that I cannot get the VPN setup to work on 9.10, using the same guide as before:
guide:[http://forum.suprbay.org/showthread.php?tid=36732](http://forum.suprbay.org/showthread.php?tid=36732)

I connect fine with Relakks but then I get this error: Cannot **determine ethernet address for proxy ARP**

Here is the full details from my logon attempts:

root@Server:~# pon relakks
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address 93.182.135.57
remote IP address 93.182.135.2
primary   DNS address 93.182.182.85
secondary DNS address 93.182.182.85

Extremely grateful for any help on this!

---

