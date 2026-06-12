---
title: "IPv4-IPv6 Gateway"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by em2slyn on 2013-01-27
Hi Folks:
 
I'm trying to build a demo IPv6 gateway that connects to an IPv4-only network and could some expertise work out the configuration.
 
Purpose: I'm building a system of servers on VMware Workstation 9.0.1 that I would like to configure using IPv6. I'd like to present the system with a IPv6 address (like what you would see from an ISP) that allows basic connectivity to the IPv6 resources on the internet while containing the system in a sandbox environment. The system sits behind a consumer-grade wireless router that only forwards TCP/UDP but not Protocol 41 needed for 6to4 tunneling. I'd prefer to use Teredo tunning using Miredo since it does not require special configuration. This is proof-of-concept only so performance is not a consideration.
 
So far, I've created a dual-homed virtual machine using Ubuntu 12.10 Server with eth0 bridged to the local network and eth1 connect to an isolated private virtual network. The gateway is configured as a simple IPv4 NAT and that seems to work just fine.
 
Now, I'd like to pass IPv6 through the gateway letting the gateway tunnel the IPv6 over the IPv4 network. I installed Miredo and can ping IPv6 sites from the gateway's command line and enabled IPv6 forwarding in /etc/sysctl.config. Next, I assigned a static IPv6 unique local link address to eth1 for the private network and can ping the IPv6 interface from another computer on the private network. The problem is that I can't seem to get the IPv6 to pass through the gateway.
 
Here's the configuration:
 
> /etc/network/interfaces
...
# Public IPv4 network
auto eth0
iface eth0 inet static
        address 192.168.1.13
        netmask 255.255.255.0
        gateway 192.168.1.1
 
dns-nameservers 8.8.8.8 8.8.4.4
 
iface eth0 inet6 auto
 
# Private dual-stack network
auto eth1
iface eth1 inet static
        address 10.0.0.1
        netmask 255.255.255.0

iface eth1 inet6 static
        address fd8d:4989:2b1a::1
        netmask 64
...
 
> /etc/sysctl.conf

...
net.ipv4.ip_forward=1
net.ipv6.conf.all.forwarding=1
...
 
> /etc/rc.local
...
iptables -A FORWARD -o eth0 -i eth1 -s 10.0.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -F POSTROUTING
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
...

I also tried adding the following command to /etc/rc.local
 
iptables -A FORWARD -o eth0 -i eth1 -s fd8d:4989:2b1a::/64 -m conntrack --ctstate NEW -j ACCEPT
 
but that did not seem to work.
 
I'm new to this forum, so your help is really appreciated. Thanks!

---

### Post by sanderj on 2013-01-27
I have no solution for you, but I'm just wondering: did you read an instruction how to this? For example:


NAT-PT: Providing IPv4/IPv6 and IPv6/IPv4 Address Translation
By J. W. Atwood, Kedar C. Das, and Ibrahim Haddad


I guess NAT64 is what you want, but I believe an IPv6 subnet for that (which miredo does not provide AFAIK)

---

### Post by em2slyn on 2013-01-28
Thank you for the suggestion. I built a NAT64 device using Tayga and it worked pretty good as an IPv6 gateway, however, it was not quite what I'm looking for since it only identifies IPv4 devices not IPv6 devices on the public side of the NAT. Let me offer a different explanation.
[LIST=1]
[*]I would like to have a server on a private IPv6 only network
[*]A gateway would connect the private IPv6 network to the internet cloud via a IPv4 network
[*]Out in the internet cloud there exists other IPv6 networks and servers (i.e. ipv6.google.com)
[*]From the server on the private IPv6 network, I would like to ping ipv6.google.com and receive a response
[*]To do this, the gateway needs to tunnel the IPv6 address through the IPv4 network to Google's IPv6 network.
[/LIST]If I have Miredo installed on the gateway, I can ping ipv6.google.com from the command line. This means that the gateway is tunneling the IPv6 address through the public IPv4 network to the destination IPv6 network at Google that resides in the public cloud.
 
Now, I'd like to ping ipv6.google.com from the server on the private IPv6 network and still reach Google's IPv6 network in the public cloud despite the intervening IPv4 network. In a sense, I'd like to make the intermediate public IPv4 network appear transparent between two IPv6 sites. The question is, what kind of IPv6 transitional device would work? This is what I know so far,
[LIST]
[*]Teredo tunnels IPv6 over a IPv4 network and works through intervening NAT devices (+)
[*]My consumer grade router only forwards TCP/UDP so forwarding Protocol 41 used by a 6in4 tunnel broker is out (-)
[*]My wireless router does not support 64rd (-)
[*]Still looking at 6to4 as an possibility (?)
[*]NAT64 works but only identified IPv4 devices
[/LIST]Any other suggestions? Thanks!
 
Have a GREAT DAY!!

---

### Post by hawkmage on 2013-01-29
I did this a bit different I used a 6in4 tunnel to Hurricane Electric's free IPv6 tunnel broker on a Ununtu server that I set up as an IPv6 router.

Here is a decent post on how to do this:
[http://ubuntuforums.org/showthread.php?t=1681815&highlight=Tunnelbroker+IPv6](http://ubuntuforums.org/showthread.php?t=1681815&highlight=Tunnelbroker+IPv6)

---

### Post by em2slyn on 2013-01-30
Thanks folks!
 
@Hawkmage: Yes, that is the way to go and I just built it this morning before I read your posting. I did not fully understand how to setup my wireless router to enable 6in4 and figured it out last night--hence the roadblock to using HE's tunnel broker and the search for an alternate solution. Nonetheless, I bookmarked your instructions for reference and I continue to refine and improve on the solution. Thanks!

---

### Post by lemming465 on 2013-02-02
Best wishes for your IPv6 R&D.  It's the future of the internet; both Cisco and AT&T predict that backbone routing of IPv4 will cease by 2020, though I suspect it will linger on in the back offices till 2036 or so.

A couple of comments:

6to4, ISATAP, and 6in4 tunnels all use protocol 41 (IPv4 packet with the payload being an IPv6 packet).  Teredo uses NAT44 tunneled UDP.   The automatic tunnels (6to4, Teredo) tend to have [very high failure rates]("http://www.potaroo.net/ispcol/2010-12/6to4fail.html"), which may not be a problem for R&D but would be operationally.

6rd is an ISP ploy to get around lack of dual-stack capability in their about to be upgraded head-end gear; they have native dual-stack IPv4+IPv6 at their border, but set up protocol 41 tunnels between their modems and an in-house relay.  If your ISP doesn't offer native v6 yet, but does offer 6rd, this may be a good way to go. It looks like native to your clients: their modem is emitting ICMPv6 Router Advertisements which lets your clients autoconfigure global-scope IPv6 addresses, and the latency may be better than with 3rd party 6in4 relays.

Some of the 6in4 relays can tunnel over TCP if protocol 41 isn't available on your wifi or modem gear.  Eventually we're all going to have to replace our routers and modems with stuff that has dual-stack support for native IPv6; don't buy anything new that doesn't.

The fd::/7 *unique local* IPv6 prefixes are not globally routable, but a lot of OS network stacks get confused about that if they also see global-scope addresses (2::/3 prefix).  

Remember that fe80://64 is link-local, and ff::/8 is multicast.  Most of your multicast will be ff02:://16 unflagged link-scope using IANA registered groups like all-hosts (::1) or all-routers (::2) or all DHCP relays (::1:3).

Being IPv6 only is not a fun place yet; only [about 5-15% of the Alexa top million web sites]("http://bgp.he.net/ipv6-progress-report.cgi") have IPv6 so far.  However, dealing with carrier-grade NAT44 in the face of IPv4 address exhaustion will be so bad in Eurasia (both RIPE and APNIC RIR's are out of regular IPv4, as is IANA) that IPv6 is going to get a lot more popular Real Soon Now.  Note that in the USA, most (all?) LTE4 cellphone networks are IPv6 only; to get to the legacy IPv4 internet you have to go through a carrier NAT64+DNS64 gateway.  Of course, top destinations like facebook, google, youtube etc. *are* dual-stacked and you'll get good, direct native IPv6 performance with them.

---

