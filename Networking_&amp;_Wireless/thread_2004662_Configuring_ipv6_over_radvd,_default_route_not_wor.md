---
title: "Configuring ipv6 over radvd, default route not working"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by Genius2999 on 2012-06-16
Hello all,

So this morning, I have been trying to configure IPv6 upon my network using the guide I found on reddit (of all places) at [http://ipv6friday.org/blog/2012/06/ipv6-enabling-training/](http://ipv6friday.org/blog/2012/06/ipv6-enabling-training/) .Now at first glance, this appears to be working, however, the machine that I am testing, while it is correctly obtaining an address from the range, isn't routing IPv6 where I would expect as demo'd by:

**[server]** output of "ping6 -c 3 www.facebook.com"
```
PING www.facebook.com(www6-slb-10-03-frc1.facebook.com) 56 data bytes
64 bytes from www6-slb-10-03-frc1.facebook.com: icmp_seq=1 ttl=47 time=133 ms
64 bytes from www6-slb-10-03-frc1.facebook.com: icmp_seq=2 ttl=47 time=132 ms
64 bytes from www6-slb-10-03-frc1.facebook.com: icmp_seq=3 ttl=47 time=133 ms

--- www.facebook.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 132.464/133.152/133.669/0.506 ms

```

and

**[client]** output of "ping6 -c 3 www.facebook.com"

```
PING www.facebook.com(www6-slb-10-03-frc1.facebook.com) 56 data bytes

--- www.facebook.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

```

A copy of relevant configurations is below. I have partially anonymised the ranges used:

**[server]** /etc/radvd.conf
```
interface eth0
{
AdvSendAdvert on;

# This may be needed on some interfaces which are not active when
# radvd starts, but become available later on; see man page for details.

# IgnoreIfMissing on;

#
# These settings cause advertisements to be sent every 3-10 seconds. This
# range is good for 6to4 with a dynamic IPv4 address, but can be greatly
# increased when not using 6to4 prefixes.
#

MinRtrAdvInterval 3;
MaxRtrAdvInterval 10;

#
# You can use AdvDefaultPreference setting to advertise the preference of
# the router for the purposes of default router determination.
# NOTE: This feature is still being specified and is not widely supported!
#
AdvDefaultPreference low;

#
# Disable Mobile IPv6 support
#
AdvHomeAgentFlag off;

#
# The network prefix I got from SIXXs on the tunnel details page
#
	prefix 2a01:348:6:XXX::/64 {
		AdvOnLink on;
		AdvAutonomous on;
		AdvRouterAddr off;
	};

#
# RDNSS
# NOTE: This feature is not very widely implemented.
#
	RDNSS 2a01:348:6:XXX::2 {
		AdvRDNSSLifetime 30;
	};

};
```

**[client]** output of "sudo ifconfig"
```
wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:dd  
          inet addr:192.168.1.31  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a01:348:6:XXX:XXX:feff:fe81:70dd/64 Scope:Global
          inet6 addr: fe80::c617:XXX:XXX:70dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99921 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103144730 (103.1 MB)  TX bytes:10523791 (10.5 MB)
```

**[client]** output of "ip -6 route show dev wlan0"
```
2a01:348:6:XXX::/64  proto kernel  metric 256  expires 86405sec
fe80::/64  proto kernel  metric 256 
default via fe80::202:XXX:XXX:7345  proto kernel  metric 1024  hoplimit 64
```

Now by my thinking, this is trying to route IPv6 over loopback by default and not using the other route via 2a01. My question, what is going on here and how do I change the default routing?

Thanks in advance!

---

