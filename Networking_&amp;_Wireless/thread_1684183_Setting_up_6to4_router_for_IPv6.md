---
title: "Setting up 6to4 router for IPv6"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by pjfasano on 2011-02-08
With the news of [IPv4 addresses being exhausted]("http://tech.slashdot.org/story/11/02/01/0036227/Last-Available-IPv4-Blocks-Allocated"), I decided to try and get my network ready for IPv6. All of my hosts are set up to do stateful autoconfig, I have radvd installed and working, and I can ping6 ipv6.google.com from my Ubuntu server. However, when one of the clients on the inside tries to ping6, no packets return and I get this message in the router's syslog:

```
Feb  8 17:55:17 foo kernel: [ 1344.824474] Dead loop on virtual device tun6to4, fix it urgently!
```Any suggestions?

---

### Post by lemming465 on 2011-02-10
Could we see the output of *ip address show; ip -4 route show; ip -6 route show;* and maybe also *head /proc/sys/net/ipv6/conf/all/**?

---

### Post by annoyingrob on 2011-02-10
You probably just haven't properly set up some default routes. Can you post your radvd config? Is it pointing to the right IP6 address for its gateway? Can you post your tunnel config? A very common problem is that people advertise the tunnel prefix in radvd rather than the network prefix.

---

### Post by pjfasano on 2011-02-14
> **lemming465 said:**
> Could we see the output of *ip address show; ip -4 route show; ip -6 route show;* and maybe also *head /proc/sys/net/ipv6/conf/all/**?

```
root@foo:~$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 52:54:00:8f:39:14 brd ff:ff:ff:ff:ff:ff
    inet 192.168.55.254/24 brd 192.168.55.255 scope global eth0
    inet6 fe80::5054:ff:fe8f:3914/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 52:54:fd:eb:65:7e brd ff:ff:ff:ff:ff:ff
    inet 216.24.124.2/28 brd 216.24.124.15 scope global eth1
    inet6 fe80::5054:fdff:feeb:657e/64 scope link 
       valid_lft forever preferred_lft forever
4: sit0: <NOARP> mtu 1480 qdisc noop state DOWN 
    link/sit 0.0.0.0 brd 0.0.0.0
5: tun6to4: <NOARP,UP,LOWER_UP> mtu 1480 qdisc noqueue state UNKNOWN 
    link/sit 216.24.124.2 brd 0.0.0.0
    inet6 2002:d818:7c02::1/16 scope global 
       valid_lft forever preferred_lft forever
    inet6 ::216.24.124.2/128 scope global 
       valid_lft forever preferred_lft forever

root@foo:~$ ip -4 route show
216.24.124.0/28 dev eth1  proto kernel  scope link  src 216.24.124.2 
192.168.55.0/24 dev eth0  proto kernel  scope link  src 192.168.55.254 
default via 216.24.124.1 dev eth1  metric 100 

root@foo:~$ ip -6 route show
pjfasano@cherubim:~$ cat ipv6_diag.txt 
root@foo:~$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 52:54:00:8f:39:14 brd ff:ff:ff:ff:ff:ff
    inet 192.168.55.254/24 brd 192.168.55.255 scope global eth0
    inet6 fe80::5054:ff:fe8f:3914/64 scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 52:54:fd:eb:65:7e brd ff:ff:ff:ff:ff:ff
    inet 216.24.124.2/28 brd 216.24.124.15 scope global eth1
    inet6 fe80::5054:fdff:feeb:657e/64 scope link 
       valid_lft forever preferred_lft forever
4: sit0: <NOARP> mtu 1480 qdisc noop state DOWN 
    link/sit 0.0.0.0 brd 0.0.0.0
5: tun6to4: <NOARP,UP,LOWER_UP> mtu 1480 qdisc noqueue state UNKNOWN 
    link/sit 216.24.124.2 brd 0.0.0.0
    inet6 2002:d818:7c02::1/16 scope global 
       valid_lft forever preferred_lft forever
    inet6 ::216.24.124.2/128 scope global 
       valid_lft forever preferred_lft forever

root@foo:~$ ip -4 route show
216.24.124.0/28 dev eth1  proto kernel  scope link  src 216.24.124.2 
192.168.55.0/24 dev eth0  proto kernel  scope link  src 192.168.55.254 
default via 216.24.124.1 dev eth1  metric 100 

root@foo:~$ ip -6 route show
::/96 dev tun6to4  metric 1  mtu 1480 advmss 1420 hoplimit 4294967295
::/96 via :: dev tun6to4  metric 256  mtu 1480 advmss 1420 hoplimit 4294967295
2002::/16 dev tun6to4  proto kernel  metric 256  mtu 1480 advmss 1420 hoplimit 4294967295
2000::/3 via ::192.88.99.1 dev tun6to4  metric 1  mtu 1480 advmss 1420 hoplimit 4294967295
fe80::/64 dev eth1  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
fe80::/64 dev eth0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
fe80::/64 dev tun6to4  proto kernel  metric 256  mtu 1480 advmss 1420 hoplimit 4294967295

```Here's the contents of /proc/sys/net/ipv6/conf/all/*
```
==> /proc/sys/net/ipv6/conf/all/accept_dad <==
1

==> /proc/sys/net/ipv6/conf/all/accept_ra <==
1

==> /proc/sys/net/ipv6/conf/all/accept_ra_defrtr <==
1

==> /proc/sys/net/ipv6/conf/all/accept_ra_pinfo <==
1

==> /proc/sys/net/ipv6/conf/all/accept_redirects <==
0

==> /proc/sys/net/ipv6/conf/all/accept_source_route <==
0

==> /proc/sys/net/ipv6/conf/all/autoconf <==
1

==> /proc/sys/net/ipv6/conf/all/dad_transmits <==
1

==> /proc/sys/net/ipv6/conf/all/disable_ipv6 <==
0

==> /proc/sys/net/ipv6/conf/all/force_mld_version <==
0

==> /proc/sys/net/ipv6/conf/all/forwarding <==
1

==> /proc/sys/net/ipv6/conf/all/hop_limit <==
64

==> /proc/sys/net/ipv6/conf/all/max_addresses <==
16

==> /proc/sys/net/ipv6/conf/all/max_desync_factor <==
600

==> /proc/sys/net/ipv6/conf/all/mtu <==
1280

==> /proc/sys/net/ipv6/conf/all/proxy_ndp <==
0

==> /proc/sys/net/ipv6/conf/all/regen_max_retry <==
5

==> /proc/sys/net/ipv6/conf/all/router_solicitation_delay <==
1

==> /proc/sys/net/ipv6/conf/all/router_solicitation_interval <==
4

==> /proc/sys/net/ipv6/conf/all/router_solicitations <==
3

==> /proc/sys/net/ipv6/conf/all/temp_prefered_lft <==
86400

==> /proc/sys/net/ipv6/conf/all/temp_valid_lft <==
604800

==> /proc/sys/net/ipv6/conf/all/use_tempaddr <==
0

```And here's my radvd.conf:
```
interface eth0
{
   AdvSendAdvert on;
#   prefix fec0::/64
#   {

    prefix 0:0:0:1::/64
    {
    AdvOnLink on;
    AdvAutonomous on;
    Base6to4Interface eth1;
    };
#   prefix 0:0:0:0::/64
#   {
#           Base6to4Interface lo:1;
#   };
 };

```

Thanks! :)

---

### Post by lemming465 on 2011-02-15
I don't have personal experience with this configuration, but as I understand it, the downstream network needs to be part of the /48 your 6to4 tunnel is routing.  You have 2^16 subnets available; there is no NAT66 in IPv6.  So if your eth1 uplink has v4 address 216.24.124.2, your 6to4 prefix is is 2002:d818:7c02:://48, and the v6 subnet on the tun6to4 tunnel is 2002:d818:7c02:0::/64.  Your eth0 LAN needs a different v6 subnet within the same prefix, e.g. 2002:d818:7c02:1::/64.  You need to statically assign eth0 an address on that subnet, e.g. ```
ip -6 addr add 2002:d818:7c02:1::1/64 dev eth0
```and have radvd advertise that second subnet.  Replace *prefix 0:0:0:1::/64* with *prefix 2002:d818:7c02:1::/64* so that the LAN clients are getting globally routable 6to4 addresses under your /48 tunnel, and try again.

---

### Post by pjfasano on 2011-02-21
> **lemming465 said:**
> You need to statically assign eth0 an address on that subnet, e.g. ```
ip -6 addr add 2002:d818:7c02:1::1/64 dev eth0
```

That's all I needed to do! As soon as I did that, my clients could connect correctly. I added it to /etc/network/interfaces and it all works wonderfully now! :)

Thank you! :D

---

### Post by good_life on 2012-04-04
Hi, everyone!
 I did study and read ideas of everybody! but I don't understand, can i make tunnel 6to4 in local networks(no internet)? 

IPv6/IPv4 (192.168.1.0/24) <--->IPv4(192.168.1.0/24)<--->IPv6/IPv4(192.168.1.0/24)

  I did make follow tutorial in internet(example: [http://tldp.org/HOWTO/Linux+IPv6-HOWTO/configuring-ipv6to4-tunnels.html](http://tldp.org/HOWTO/Linux+IPv6-HOWTO/configuring-ipv6to4-tunnels.html),...) but not done!!! :(! Please! everyone help me!!!

Thank you!!!

---

### Post by lemming465 on 2012-04-10
short oversimplified answer: no, you shouldn't try to use 6to4 on your LAN

Less oversimplified, 6to4 tunnels connect dual-stack IPv4+IPv6 hosts with the IPv6 internet using protocol 41 encapsulation ("slap an IPv4 header on the front of an IPv6 packet") to anycast relays over a v4-only uplink.   On the v4 side the anycast relays are advertising 192.88.99.0/24 routes (using BGP-4) and live at 192.88.99.1.  On the v6 side the anycast relays are advertising 2002::/16 routes.  

So in the standard configuration your v6 packet gets a v4 header with your public v4 source address and 192.88.99.1 destination address.  The relay, whereever it is, strips off the v4 header and forwards the v6 packet to the v6 destination.  The v6 server replies to your 2002:a.b.c.d::/48 v6-encoded v4 6to4 special v6 address with a native v6 packet.  The nearest relay to the server (probably a different anycast relay) snarfs up the v6 packet, decodes your v4 address (embedded), and synthesizes a new v4 header to encapsulate it with, using either its own v4 address or 192.88.99.1 as the source, and your v4 as the destination.

Optimization: windows 7 and Linux have embedded 6to4 translators and will cut out the second relay, replying directly to the v4 destination with a protocol 41 packet.

So windows 7 and Linux hosts on a LAN can potentially communicate via 6to4, but that's a silly thing to do, since the net effect is to cut the MTU size by 1 IPv4 header for the encapsulation, and all the host to host traffic on the LAN is actually v4 packets, you aren't sending any native v6 (ethertype 0x86dd; v4 is ethertype 0x0800).

A better choice for native LAN communication would be to generate a "unique local adddress prefix" (fd + 40 random bits), pick a 16 bit subnet structure (e.g. all zeroes), and use that as your native v6 /64 LAN prefix.  You'll still have to use static host entries or dynamic DNS or multicast DNS or something so that the LAN hosts can find each other, and you might have to configure radvd on one host or something on a dual-stack router/firewall device so that ICMPv6 router advertisements are being sent.

---

