---
title: "I thought I have an IPV6 address?!"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by KevinQ on 2011-09-02
I know that IPv6 is supported in linux. Then how comes when I type ifconfig in terminal, the ethernet interface doesn't have an ipv6 address?
It only shows

eth0      Link encap:Ethernet  HWaddr (omitted)
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          ....
while my lo and wlan0 both had IPv6 address. And when I test my IP address following this link:[http://test-ipv6.com/](http://test-ipv6.com/) using WIFI, it still reports I don't have an IPv6 address even it's shown on my wlan0 interface.
Now I am quite confused about the meaning of "IPV6 support".

---

### Post by haqking on 2011-09-02
> **KevinQ said:**
> I know that IPv6 is supported in linux. Then how comes when I type ifconfig in terminal, the ethernet interface doesn't have an ipv6 address?
It only shows

eth0      Link encap:Ethernet  HWaddr (omitted)
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          ....
while my lo and wlan0 both had IPv6 address. And when I test my IP address following this link:[http://test-ipv6.com/](http://test-ipv6.com/) using WIFI, it still reports I don't have an IPv6 address even it's shown on my wlan0 interface.
Now I am quite confused about the meaning of "IPV6 support".

"IPv6 Support" means just that, it means it is supported.

[https://wiki.ubuntu.com/IPv6#IPv6_Introduction](https://wiki.ubuntu.com/IPv6#IPv6_Introduction)

[http://www.cyberciti.biz/faq/ubuntu-ipv6-networking-configuration/](http://www.cyberciti.biz/faq/ubuntu-ipv6-networking-configuration/)

---

### Post by KevinQ on 2011-09-02
I have read those two links before, my question still not solved.

---

### Post by nm_geo on 2011-09-02
> **KevinQ said:**
> I have read those two links before, my question still not solved.
 
Read this 
 
[http://www.thetechlabs.com/tech-news/ipv4-vs-ipv6/](http://www.thetechlabs.com/tech-news/ipv4-vs-ipv6/)
 
> 
This has no direct consequences or relations to home consumers and average internet users (meaning you), the IPv6 protocol switch only seriously pertains to large online organizations with an extensive listing of online hosted content.
You will likely see little to no change in online functionality or service.

 
Someday our IP providers might have to give us IPv6 protocols.

---

### Post by haqking on 2011-09-02
> **KevinQ said:**
> I have read those two links before, my question still not solved.

Give yourself one then ;-)

Network manager, edit connections and IPv6 Settings.

As long as other devices are using it on your LAN.

As for you WAN IP then that is down to your ISP not you.

edit your /etc/network/interfaces file and add one.

Is this your question ? I read it as why dont you have one and you thought it was supported.

So yes it is supported, and you can give yourself one.

But not much point if nothing else is using it, why do you want one ?

---

### Post by lemming465 on 2011-09-04
Congratulations on being interested in trying IPv6.  Persevere; you can make it work.  A quick & dirty test is "ping6 -c3 ipv6.google.com".  If that works, you have some kind of IPv6; if it doesn't you probably only have IPv4.

Saying IPv6 is "supported" in Linux doesn't, as you have noticed, quite tell you how to use it.  It's certainly potentially available, in the sense that one can compile a Linux kernel which supports the "inet6" address family, and typical distributions ship tools which can configure it.  Ubuntu will normally include both IPv4 and IPv6 support and tools.

My favorite commands for displaying network settings use the newer iproute2 tools, for instance```
ip -4 address show
ip -6 address show
ip -4 route show
ip -6 route show
ip -4 neighbor show
ip -6 neighbor show
```

The next hurdle is that there are different kinds of IPv6 addresses, and you may or may not have the kind you Really Want, which is "global scope native unicast", which would start with a "2" currently. The "::1" (127 zero bits, 1 one bit) loopback address can only be used on-host with local processes, i.e. it has "node scope".  You'll only find that one on your loopback interface, usually named "lo".  Addresses which start off "fe80::/64" are "link-local scope", and can only be used with immediate neighbors, places you can reach without crossing a router or firewall.  These are similar to IPv4 "zeroconf" addresses which start off 169.254.0.0/16.  Multicast addresses (delivered simultaneously to multiple destinations) start off with "ff00::/8", e.g. the "ff02::1" link-scope all nodes address.

Global scope addresses, the ones you can use with IPv6 peers on the general IPv6 internet, start with "2" currently.  E.g. "2001:470:0:64::2" for ipv6.he.net.  Global scope addresses might be either native or tunneled.  For native, your ISP has to offer IPv6; most of them don't yet.  And the network gear between your computer and your ISP has to support IPv6, e.g. your Wifi router and broadband (cable or DSL) modem.  Most of them don't support IPv6 yet either.  So just because your OS (Ubuntu Linux) supports IPv6 doesn't mean you can use it.  You can tell if you have native IPv6 by whether or not you are receiving ICMPv6 type 134 "router advertisement" messages sent to that ff02::1 link-scope all-nodes address.

If you are getting RA's, flag bits in the RA say whether your client computer should configure an address by DHCPv6 or by stateless autoconfiguration. Ubuntu Linux supports both.

If your ISP doesn't offer IPv6, yet, nag them about that.  By 2015 most of the planets ISP's should be offering native v6 to their customers.  If your wifi or broadband gear doesn't support IPv6, upgrade it.  It will be cheaper and higher quality by around 2013, so only early adopters should be in a hurry and do it this year. IPv4 -> IPv6 is kind of like the US transition from analog TV to digital: new gear all around, for mostly the same old content.

You may have options for tunneled IPv6 even if you can't yet get native.  The tunnel idea is for your dual-stack (IPv4 + IPv6) host to get past the IPv4-only moat your ISP presents by enlisting a dual-stack partner on the far side who does have native IPv6, and who can forward traffic on your behalf.   Your best choices, in order of preference, are:

(1) a point to point tunnel, aka "6in4", usually using the protocol 41 encapsulation, where you slap an IPv4 header in front of your IPv6 packet, addressed to your relay.  There are free tunnel broker services for this run by freenet, gogo6, and hurricane electric ("tunnelbroker.net").  In the hurricane electric case you will have to cut and paste a few commands they give you into a terminal window running root to bring up the tunnel.  This looks something like:```

modprobe ipv6
ip tunnel add he-ipv6 mode sit  remote 209.51.181.2 local 192.0.24.10 ttl 255
ip link set he-ipv6 up
ip addr add 2001:db8:1f10:11bc::2/64 dev he-ipv6
ip route add ::/0 dev he-ipv6
```
Ignore any "sit0" interface you see; it's a legacy artifact which is unusable for making actual tunnels with, and it's presence in a list of interfaces tells you nothing about your actual IPv6 connectivity.  You have to register with the web site of the tunnel broker and ask for a tunnel to be activated for you before you can configure your end and send packets.

(2) an anycast "6to4" tunnel.  I like the "tun6to4" script [published by New Zealand ISP anyweb for this]("http://www.anyweb.co.nz/tutorial/Linux6to4Host").  You computer has to be on a public, global scope IPv4 address (not an RFC-1918 private address such as 192.168.1.100), your wifi & broadband gear has to pass protocol 41, and someone nearby, preferably your ISP, should be running a 6to4 relay.  6to4 relays have BGP advertisements for 192.88.99.1/24 on the v4 side, and 2002::/16 on the v6 side.  6to4 tunnels will break if your firewall doesn't allow arbitrary protocol 41 packets in, so if you are using 6to4 tunneling, you should have your ip6table host-based firewalling turned on.

(3) if all else fails, use the Teredo protocol, which can work over UDP from behind a NAT44 device, as is typical at home.  For Linux, install the "miredo" package.  You'll again want a host-based firewall.

Note: windows 7 hosts will try to automatically configure at least one of the ISATAP, 6to4, or Teredo tunneling protocols, depending on their network environment.  You can see what a windows host is doing by typing commands like "ipconfig /all", "netsh interface ipv6 show neighbor", and "route print".

---

