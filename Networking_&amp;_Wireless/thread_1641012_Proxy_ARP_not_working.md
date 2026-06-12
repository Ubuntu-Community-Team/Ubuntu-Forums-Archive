---
title: "Proxy ARP not working"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by Karl1982 on 2010-12-08
I'm having an issue on multiple Lucid boxes where I can't get proxy ARP to work.  This is to be used in conjunction with openswan IPSec.  I've enabled forwarding and disabled sending/accepting ICMP redirects for each interface as per openswan's requirements.  I've added the proxy arp lines for all, default, eth0, and lo to sysctl.conf:

```
net.ipv4.conf.eth0.proxy_arp = 1
```I then connect the IPSec client, and I have connectivity to the server.  When I try to ping (or otherwise access) something else on its subnet, I reach the intended target, but then it ARPs for the sending machine, and the Ubuntu server doesn't respond to the ARP.

I have an ARP entry that looks like this, added via *arp -s 192.168.254.100 -D eth0 -i eth0 pub*:


[LIST]
[*]Address: 192.168.254.100 (the correct virtual IP for the client)
[*]HWtype: *
[*]HWaddress: <from_interface>
[*]Flags Mask: MP
[*]Iface: eth0
[/LIST]
Best I can tell, everything is in order... I can listen in with wireshark on the server and see that it's receiving the ARPs, but I can't get it to respond to them.  What am I missing?

---

### Post by Karl1982 on 2010-12-11
bump

Edit: I read somewhere that, if proxy_arp is enabled, Ubuntu will automatically send ARP replies for any host or network to which it's routing.  I tried adding a route to the host, but it still isn't responding to ARPs for the required address (verified with tcpdump).

---

