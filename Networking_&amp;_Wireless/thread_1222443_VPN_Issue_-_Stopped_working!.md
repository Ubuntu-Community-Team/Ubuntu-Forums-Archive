---
title: "VPN Issue - Stopped working!"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by arunz on 2009-07-24
Hi,

I'm a newbie to Ubuntu (Linux!). Yesterday I installed kvpnc to connect to my cisco vpn at work. Everything went fine. 

However today morning there was a power failure in my area and system got rebooted. Today when I started the VPN connection, I see the following issue even though I get the notification that connection is successful:

1. My DNS server entry over my default eth0 interface is overwritten with new ones.
2. I couldn't ping any addresses in tun0 interface. There's a network specific route over tun0 interface. So DNS servers supplied during the VPN are not accessible.
3. DNS look up fails. However I could ping with real IP addresses. The default route is still my eth0 interface and the communication is over the eth0 and not tun0 interface.
4. After couple of minutes VPN is disconnected as the DNS is not working anymore
5. I still see the old DNS entries and so I have to restart my eth0 interface to set it right.

Any pointers?

Thanks.

---

### Post by arunz on 2009-07-27
When I started kvpnc on the shell using "sudo kvpnc", things work fine. However starting it through "Applications-->Internet -->KVpnc" has the problem I reported earlier. Why?

---

### Post by arunz on 2009-07-27
Worse yet.. After starting once using sudo, even the other things work now(I closed that opened through GUI). Overall there's no problem now. What really fixed the problem?

---

