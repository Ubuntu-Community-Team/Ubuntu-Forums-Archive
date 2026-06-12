---
title: "Can openVPN bridge 2 clients"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by rzj on 2011-09-14
I have 2 subnets with local IP behind NAT routers.
I have a remote VPS with fixed IP
What I would like to do is set up openVPN so that the VPS bridges 2 tunnels between 2 clients so that a computer from each subnet connects and sees the other subnet

home pcs,printers etc---- home net --- home pc ---- tunnel ----- VPS ---- tunnel ---- office pc --- office subnet --- office pc's, printers and servers

is this possible

---

### Post by poolet on 2011-09-14
Well it's possible but it's depend of which type of vpn you have... If you have LT2P you must have NAT-T (transparent) in order to pass through your NAT.... Check the following link:::

[http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

---

### Post by rzj on 2011-09-14
Thanks but I should have been clearer.

It wasn;t a NAT question. I can connect using keys to the server from a client behind NAT without problems

What I want to know is can I have 2 clients connect to the server and have their traffic bridged by the server rather than one connecting direct to the other.

My clients can easily find the server but they can't find each other unless I port forward but then I can only have one NAT'd target and I want to be able to connect to different PCs on each net especially in case one is down

---

### Post by SeijiSensei on 2011-09-14
Does the server not route between the two subnets?  Maybe you just need to add a route or relax an iptables forwarding rule to enable them to see each other.  

Another possibility is that the server will route the packets already, but the clients don't have the appropriate routes to see each other.  If one client is in 10.10.1.0/24 and the other on 10.10.2.0/24, on the first client add the route:

```
ip route add 10.10.2.0/24 via servers.tunnel.ip.addr
```

Then packets destined for hosts in 10.10.2.0/24 will be sent over the tunnel to the server for forwarding to their final destinations.

I avoid bridging and use IP routing wherever possible.

---

