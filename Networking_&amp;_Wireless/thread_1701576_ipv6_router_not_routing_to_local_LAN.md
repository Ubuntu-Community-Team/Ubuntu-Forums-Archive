---
title: "ipv6 router not routing to local LAN"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by fader on 2011-03-06
Hi all,

I need some help getting my local clients connected to the IPv6 internet.

I've already designated a machine to act as the router to the hurricane electric tunnel. I created a he-ipv6 device on it and can ping ipv6.google.com. No problem.

The problem happens when I want clients to use that router. That is, I can't ping ipv6.google.com from other machines on my LAN.

I setup /etc/radvd.conf, which seemed to successfully give out addresses to my clients:

interface eth0
{
	AdvSendAdvert on;
	prefix MY:HE:PREFIX::/64
	{
		AdvOnLink on;
		AdvAutonomous on;
	};
};

I start the daemon and check that my clients have new ip6 addresses. So far so good. On my router, I do a sysctl -p and see that /proc/sys/net/ipv6/conf/all/forwarding = 1. I haven't touched ip6tables/iptables yet. Both are in a flushed state.

My ipv6 router is actually inside the LAN which gets internet from another machine which has let ipv6 packets through using protocol 41. I figure I don't have to worry about anything else because if my router can ping6 ipv6.google.com, the failure point would be there.

So my clients get ip6 addresses, but can't ping6 the router nor the ipv6.google.com. They do resolve ipv6.google.com however and I checked the traffic on the router over he-ipv6 from ifconfig and RX and TX bytes were changing during the ping.

My router has only one physical device for forwarding, eth0 and the tunnel device he-ipv6. Do I need to add some kind of ip6tables to see a simple ping from my clients?

Thanks and help appreciated!

---

### Post by annoyingrob on 2011-03-08
there may be an issue with not specifying the gateway in radvd.conf. I don't know, it might just default to the radvd server if you don't give it one.

take a look at "ip6tables --list", and make sure your default forward policy is set to accept.

---

