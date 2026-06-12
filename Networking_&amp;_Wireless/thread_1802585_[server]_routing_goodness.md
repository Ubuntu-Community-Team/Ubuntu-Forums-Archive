---
title: "[server] routing goodness"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by creiss on 2011-07-12
Ugh. 
Headache.
Help.

I am running a Ubuntu 11.04 Server here, with 3 network cards:

eth0 - unconfigured, connected to DSL modem
eth1 - administrative network, 192.168.25.0 / 255.255.255.0
eth2 - callcenter network, 192.168.26.0 / 255.255.255.0

And 2 virtual devices:

ppp0 - DSL uplink.
tap0 - OpenVPN Virtual Adapter, 192.168.27.0 / 255.255.255.0

Now ignore the tap0, then  everything is working fine. The eth1 guys can use nat to use the internet provided by ppp0. The eth2 cant do jackshit except some dhcp, ntp and selected other services.

Now some folks want to work from home, so I want to set up a openvpn server, which happily works. Certificate auth et all working, and clients get assigned (an) ip: 192.168.27.2. From which I can pink the 192.168.27.1 flawlessly. And directly from the server to that client. What I cant do is ping anything else, nor from the LAN to the VPN client or the other way around.

Pinging anywhere from/ to the eth1 to eth2 in any way is working, too.

What I can do, tho, is if i push a default-gateway at the client, to browse the internet over the vpn connection.

I am out of my wits banging my head at this stuff.

For your "convenience" I created a small textfile with hopefuly all relevant data, which should be attached to this post.

Thank you [COLOR="Red"]oh so much[/COLOR] for your help.


-Chris.

---

### Post by SeijiSensei on 2011-07-12
A quick glance at iptables suggests you don't have a rule permitting traffic to be forwarded to 192.168.25.0/24, just 26.0/24.  

I usually just use rules like this for tunnels:

```
iptables -A FORWARD -i tun0 -j ACCEPT
```

which permits all traffic over the tunnel interface.

Should users in any 192.168.x.0/24 network be able to access all other hosts in 192.168.x.0/24, or do you need to restrict certain subnets?  If the former, why not just use 192.168.0.0/16 for all the internal subnets?

---

### Post by creiss on 2011-07-13
Thanks for your help and reply.
Will try that in a few minutes.

I need to restrict those subnets, but I'll do some firewalling on the tap0 device (not tun0).

Cheers!
-Chris. :popcorn:

---

### Post by creiss on 2011-07-13
Update: That still gives no routing joy :(

a traceroute from a terminal within the lan results in this:

```

chris@workwench ~ $ traceroute 192.168.27.2
traceroute to 192.168.27.2 (192.168.27.2), 30 hops max, 60 byte packets
 1  servpuro (192.168.25.5)  0.144 ms  0.118 ms  0.104 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

---

