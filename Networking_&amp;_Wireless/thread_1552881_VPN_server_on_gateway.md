---
title: "VPN server on gateway"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by loop on 2010-08-14
I'm trying to establish a VPN connection between two networks and I'm having a little difficulty figuring out what software I should be using and whether my setup is possible.

The configuration is this:
(Windows XP machine - the client) -> Linksys router -> the internet -> (Zaphod - ubuntu server acting as an internet gateway/firewall) -> (Kryten - ubuntu server)

Ideally I would like the VPN server to sit on Zaphod as that is the machine I use for serving most things and Kryten is quite often off the network for various reasons. I've been playing around with pptpd but I'm having limited success and am now not even sure if that is the right software to use.

I can get the client to connect and establish a connection but as soon it is connected the internet facing interface on zaphod ceases to do anything and Zaphod effectively ceases to exists on the internet. Then after 2.5 minutes the pptpd timeout kicks in and disconnects the client. Then Zaphod appears back on the internet. During this time the windows XP client receives no traffic and is unable to ping anything on the internal network of Zaphod.

Most guides I've read seemed to indicate the VPN server should not be sat on the gateway, or that it at least makes it more complicated. Also OpenVPN seems to get mentioned quite a lot as an alternative to pptpd.

Does anyone have any experience with getting VPN working on a gateway and if so how did you manage it?

Below is the configs I've got for pptpd at the moment:

/etc/pptpd.conf
```

option /etc/ppp/pptpd-options
logwtmp
localip 192.168.0.110
remoteip 192.168.0.80-90

```

/etc/ppp/pptpd-options
```

name pptpd
refuse-pap
refuse-chap
refuse-mschap
require-mschap-v2
proxyarp
nodefaultroute
lock
nobsdcomp 

```

Zaphods network configuration is eth0 facing the internet and getting a dynamic IP address from our ISP and eth1 facing internally with an IP address of 192.168.0.1.

---

### Post by loop on 2010-08-19
Well I've decided to use OpenVPN instead as there seems to be more information around on that.

My first question is how do I get the bridging set up?
My understanding is that I need to create a bridge interface on my internal network (eth1) and then use my firewall to forward all traffic on the correct port from my external interface to that bridge interface (eth0 -> br0). Is that correct?

I figure if I get the bridging right first there is a fighting chance I'll get the server configuration sorted.

---

### Post by yaztromo on 2010-08-22
bump for great justice

---

### Post by nbkr on 2010-08-22
It depends on how you want to connect the two networks. You can bridge them, so that they act like a single LAN. This is necessary for some software, but slows down the speed of some other tools like Windows Filesharing. Reason for that is, that those tools send out network broadcasts which, if OpenVPN bridges the two networks, have to travel over the small WAN connection. For this method to work, all computers have to be in the same network i.e. all in the 192.168.1.0/24 range.

The other method is to join them like a router would do. You then would have to reconfigure the routing on both networks. This is the faster method.

So which one is it, that you need?

---

### Post by loop on 2010-09-16
Sorry about the delay in responding.

I would prefer to go with the bridging method as it seems like that would require the least amount of configuration effort on my brother's part (he is very non technical). Arranging it so that all our PCs are on the same subnet is not a problem either.
Every time I have tried to get the bridging working I end up killing the net connection of Zaphod until the VPN connection times out and then it all starts working again. Obviously I had something set very wrong. That was using pptpd.

---

