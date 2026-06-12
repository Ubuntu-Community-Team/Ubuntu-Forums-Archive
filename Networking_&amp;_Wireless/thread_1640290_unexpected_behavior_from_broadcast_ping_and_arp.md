---
title: "unexpected behavior from broadcast ping and arp"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by decoherence on 2010-12-07
Hi!

I'm trying to track down the IP address of a wayward AP on our network. I do ping -b 255.255.255.255, let it run for a second or two, getting several dozen replies from different addresses. But when I check the arp table for the AP's MAC address, it has only one or two entries in it.

What am I missing here?

thanks,

---

### Post by puppywhacker on 2010-12-07
mac addresses are only exchanged on the link level, your switch (it's apparently not a hub) is your link and is the only one that communicates it's mac address to you.

---

### Post by decoherence on 2010-12-07
should i not then only get the one entry in the ARP table?

I've done this before through a switch and got the expected results.... perhaps those times the broadcast pings filled the switch's ARP table and kicked it in to hub mode? hmmmm....

thanks!

---

### Post by bab1 on 2010-12-07
> **decoherence said:**
> should i not then only get the one entry in the ARP table?

I've done this before through a switch and got the expected results.... perhaps those times the broadcast pings filled the switch's ARP table and kicked it in to hub mode? hmmmm....

thanks!

If the switch is unmanaged you should be able to broadcast pings.  Layer 2 switches have no MAC addresses.

Broadcasts should not traverse a router. I would the broadcast ping the subnet in question only.  Here is what I get from ping -b (going through 2 switches but not past the router):

```

bruce@rincon:~>ping -b [COLOR="red"]**192.168.1.255**[/COLOR]
WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.587 ms
64 bytes from 192.168.1.245: icmp_seq=1 ttl=64 time=1.85 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=1 ttl=64 time=7.14 ms (DUP!)
64 bytes from 192.168.1.154: icmp_seq=1 ttl=64 time=279 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.513 ms
64 bytes from 192.168.1.245: icmp_seq=2 ttl=64 time=0.816 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=2 ttl=64 time=6.01 ms (DUP!)
64 bytes from 192.168.1.154: icmp_seq=2 ttl=64 time=191 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.510 ms
64 bytes from 192.168.1.245: icmp_seq=3 ttl=64 time=0.772 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=3 ttl=64 time=6.00 ms (DUP!)
64 bytes from 192.168.1.154: icmp_seq=3 ttl=64 time=113 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.513 ms

--- 192.168.1.255 ping statistics ---
4 packets transmitted, 4 received, +9 duplicates, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 0.510/46.875/279.260/87.371 ms

bruce@rincon:~>[COLOR="Red"]**arp -a**[/COLOR]
bb-ap1 (192.168.1.245) at 00:14:BF:7D:D5:XX [ether] on eth1
bb-hp1 (192.168.1.200) at 00:01:E6:6B:9F:XX [ether] on eth1
bb-gw1 (192.168.1.1) at 00:0F:DB:B5:44:XX [ether] on eth1 [COLOR="red"]**<--Router**[/COLOR]
kona (192.168.1.15) at 00:1D:BA:F3:37:XX [ether] on eth1
? (192.168.1.154) at 00:25:00:E0:60:XX [ether] on eth1


bruce@rincon:~>ping -b [COLOR="Blue"]**255.255.255.255**[/COLOR]
WARNING: pinging broadcast address
PING 255.255.255.255 (255.255.255.255) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.525 ms
64 bytes from 192.168.1.245: icmp_seq=1 ttl=64 time=0.962 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=1 ttl=64 time=6.07 ms (DUP!)
64 bytes from 192.168.1.154: icmp_seq=1 ttl=64 time=158 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.474 ms
64 bytes from 192.168.1.245: icmp_seq=2 ttl=64 time=0.795 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=2 ttl=64 time=6.06 ms (DUP!)
64 bytes from 192.168.1.154: icmp_seq=2 ttl=64 time=74.6 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.450 ms
64 bytes from 192.168.1.245: icmp_seq=3 ttl=64 time=0.725 ms (DUP!)
64 bytes from 192.168.1.200: icmp_seq=3 ttl=64 time=6.04 ms (DUP!)
64 bytes from 192.168.1.154: icmp_seq=3 ttl=64 time=302 ms (DUP!)
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.488 ms

--- 255.255.255.255 ping statistics ---
4 packets transmitted, 4 received, +9 duplicates, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 0.450/42.929/302.072/86.904 ms
bruce@rincon:~>

bruce@rincon:~>[COLOR="Blue"]**arp -a**[/COLOR]
bb-ap1 (192.168.1.245) at 00:14:BF:7D:D5:XX [ether] on eth1 [COLOR="blue"]**<-- My Wireless AP**[/COLOR]
bb-hp1 (192.168.1.200) at 00:01:E6:6B:9F:XX [ether] on eth1
bb-gw1 (192.168.1.1) at 00:0F:DB:B5:44:XX [ether] on eth1 [COLOR="Red"][COLOR="Blue"]**<--Router**[/COLOR][/COLOR]
kona (192.168.1.15) at 00:1D:BA:F3:37:XX [ether] on eth1
? (192.168.1.154) at 00:25:00:E0:60:XX [ether] on eth1 [COLOR="Blue"]**<-- My iPhone**[/COLOR]


```

---

