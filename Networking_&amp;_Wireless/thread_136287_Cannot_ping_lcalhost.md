---
title: "Cannot ping lcalhost"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by mario.rimann on 2006-02-25
Hi there

If I start a "ping localhost" and stop this after a few seconds, ping tells me that 100% of packets got lost. The same happens if I start a "ping 127.0.0.1"

My /etc/network/interfaces contains the lines
auto lo
iface lo inet loopback
as it is described everywhere.

If I try an "ifconfig", this tells me that the loopback interface has no IP-Address bound to it. The name resolution for localhost works fine by the way.

"ping 192.168.1.34" works fine also (this is the IP I get by DHCP on eth0, WLAN).

Has anyone a hint on this? I'm quite new to Linux and Ubuntu.

Greetings from Switzerland,
Mario

---

### Post by linuxusr50 on 2006-02-25
Do you get the same results if you try to ping localhost or 127.0.0.1 as root... Just trying to rule out a permissions issues somewhere.

---

### Post by mario.rimann on 2006-03-03
Thanks for your help!

I don't understand it - but it works now. The day after writing the first message, I booted the system and since then it works fine.

Greetings,
Mario

---

