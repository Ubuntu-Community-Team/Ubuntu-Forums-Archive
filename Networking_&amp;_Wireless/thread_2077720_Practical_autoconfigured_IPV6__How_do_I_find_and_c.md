---
title: "Practical autoconfigured IPV6:  How do I find and connect to my router?"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by 1clue on 2012-10-29
Hi,

This is the opposite of the problem I expected.  I'm using Comcast as an ISP, and a LinkSys/Cisco EA6500 router.  I plugged it in, went through the auto configuration, and suddenly I have IPV6 support.  I can get to IPV6-only sites, and my outside IP address is reported as a non-FE80 ipv6.

I did this the hard way through hurricane electric before, and I guess now I'm running into issues I hadn't anticipated from that experience.  Now everything is auto-configured, and I had nothing to do with it.  Most people who buy this router probably will not even know it's IPV6 or what that means.

So the first thing I try to do is connect to the router via IPV6.  Can't do it.  Here are questions/problems I've encountered in just a few minutes of trying, which a few hours later I have not yet resolved:

[LIST=1]
[*]How do you figure out where your IPV6 router is?  (Ok this one is rdisc6, but that's not in any help page I found)
[*]How do I connect to it?  Firefox doesn't understand ipv6 addresses, and ping6 doesn't seem to do anything either.
[*]What can I actually use those lines in /etc/hosts for?
[/LIST]  

ff02::2 is a multicast to ip6-allrouters, but I can't ping6 ip6-allrouters or ff02::2.  Invalid argument.

I'm pretty familiar with IPV4 and can use netstat -rn and ifconfig to tell me just about anything I need to know about my network, but using the 6 flags for those commands provides me not much that's practical.

If somebody has experience with this, I had thought I could just turn off IPV4 dhcp on my router and have a happy experience, but not until I can find my router.  :)

---

### Post by 1clue on 2012-10-29
OK I made a small breakthrough but it still doesn't answer any of my questions in terms of Linux.

In a fit of desperation I just typed **[http://myroutername](http://myroutername)** and it connected.  There must be some sort of DNS service for the local network in addition to what's handled from the WRT series Cisco/Linksys products.

Even so I thought I should be able to use some tool to find my router and connect to it by IP.

Thanks.

---

### Post by The Cog on 2012-10-29
"route -6 -n" should show you the next-hop  address.

ping6 works - try "ping6 ::" which piings your loopback address
I can't work out how to get firefox to connect to ipv6 addresses.

P.S.
Chromium understands IPv6 addresses (in square brackets). 
This works on my PC: [http://[::1]:631/](http://[::1]:631/)

---

### Post by 1clue on 2012-10-29
Route -6 -n shows me a bunch of stuff, but that stuff doesn't include the address which is reported by the router troubleshooting page.

I can ping6 that address and it works, but as yet the **rdisc** and **route -6 -n** commands don't have that number in their output, and none of the numbers that actually work point to a device which is not my workstation.

---

### Post by 1clue on 2012-10-29
The square brackets work, thanks.  ***Edit:** The square brackets work in firefox.*
However again the only thing that works is the IP reported on the web page of the router.

And AFAICT the web connection to the router is in IPV4 using local 192.168 addresses.

Sorry I'm not really comfortable putting my actual ip addresses on the forum for a combination of two reasons:
[LIST=1]
[*]I obviously know nothing about locking ipv6 down.
[*]ipv6 doesn't have NAT.
[/LIST]

---

### Post by lemming465 on 2012-10-31
Congratulations on having native IPv6 support!  By 2015 everyone will have or need this.  Short version: turn on your IPv6 firewall with the same rules as IPv4 and be happy.

The IPv6 autoconfiguration is based on ICMPv6 router advertisement messages. Your client's network stack, or rdisc6 sends a router solicitation to ff02::2, the all-routers multicast group.  The router periodically, and in response to your RS probe, sends back an RA.  The link-local (fe80::/64 prefix) address of the router is the source address; the payload contains the flags which control DHCPv6, the list of local on-link global address prefixes, etc.   The source address in the RA packet is the only way of finding your upstream router; IPV6 gateway address is not (yet) an option in DHCPv6, unlike v4.

The router may be using multicast link-local DNS to put its name on the link, which could be where firefox by name is getting it.

Most web browsers are using the [2xxx:yyyy:....] square bracket syntax for raw IPv6 addresses, because the URL format was already using ":" as a separator between usernames and passwords.

Your router may or may not be supporting management over IPv6 yet; TCP connections don't care whether their IP network is IPv4 or IPv6, so managing the IPv6 configuration using an IPv4 connection works just fine, as you have noticed.  Similarly DNS queries use UDP (mostly) or TCP (sometimes) to ask A (IPv4) or AAAA (IPv6) questions without regard the the network layer.

Both IPv4 and IPv6 are packet-switched protocols based on next-hop routing and best-effort delivery.  So they have basically the same threat model, which means they have basically the same defensive measures.   The main issues with IPv6 compared to IPv4 are:
  * v6 hosts will be simultaneously using link-local fe80::/64 scope addressees and global scope 2000::/3 addresses.  v4 hosts tend to abandon v4 169.254.0.0/16 zeroconf addresses once they have a real address, typically by DHCP.

  * depending on the upstream router, v6 hosts may either autoconfigure their global addresses or less commonly use DHCPv6 (new protocol) to reserve them.  On Linux and Mac OS-X the default autoconf host part strategy is to use the EUI-64 mapping off the layer 2 ethernet MAC address.  This mapping inserts FFFE in the middle and flips the global/local flag bit, so your MAC address is easily recovered from your IPv6 address.  If this is viewed as a privacy problem, you can turn on privacy addresses, where 62 of the 64 host bits are chosen at random; the other two are the global/local and multicast/unicast flag bits. 

  * dual-stack IPv4 + IPv6 hosts will be using both protocols, sometimes with the same web site, e.g. you may make a v6 connection to the main web site of some forward-thinking place like google, yahoo, netflix, xbox, etc. and still end up with ads or other content delivery network stuff coming from 3rd party sites on v4.  Monostack snooping will not tell you what a dual-stack host is doing.

  * on v4 networks you have to worry about rogue DHCPv4 servers and ARP poisoning attacks.  on v6 networks you similarly have to worry about rogue DHCPv6 servers, ND (neighbor discovery) poisoning attacks, and rogue RA routers.  On both v4 and v6 this are traditionally mitigated by tactics like 802.1x forwarding security, DHCP-guard, RA-guard, switchport ACLs to filter out rogue client packets, etc.  It's more of a problem in public WIFI areas like coffeeshops or airports than at home or on corporate networks.

  * v6 network stacks are written with younger code than v4 stacks.  On the bright side they have benefited from 20 years of progress in security engineering and software development practices, on the dark side they are less mature.  So the v6 code in your OS may be buggier than the v4 code.  Patch as needed.

  * applications tend to care about the data, and perhaps the transport layer such as UDP or TCP.  The applications tend not to care about the network protocol below.  So you firewall v6 the same way you firewall v4, based on DNS names at a proxy server, ports, source or destination addresses, etc.  On Linux the v4 and v6 routing and firewalls are managed separately (ip -4 route ...; ip -6 route ....; iptables, ip6tables ...).

  * While IPv6 does not have NAT, it does have "unique local addresses", RFC 4193.  These would start with fc00::/7 if they were in use; generally they are not.  Note that NAT44 does not actually provide IPv4 security; the security is coming from the use of stateful firewalls and application proxy gateways.  You are quite welcome to continue to use stateful firewalls and application proxies with IPv6 traffic.  Delusions that RFC-1918 addresses are actually private and invisible to outside users are just that; there are a lot of ways for bad guys to go spelunking on your LAN, e.g. using malicious javascript sent to your web browser.

  * there are a lot of tunneling technologies, too many in fact, for encapsulating IPv6 traffic in IPv4, in case you need to reach an IPv6 destination across an IPv4 moat.  E.g. with a tunnel broker such as hurricane electric (or sixxs, or gogo6).  Teredo (miredo package on Linux) uses a UDP based encapsulation; most other protocols like 6in4 or 6to4 or ISATAP use a protocol 41 encapsulation (slap an IPv4 header on the front of the IPv6 packet).  You can cut off most of the tunnels by blocking protocol 41 and the standard teredo server port 3544/udp.  Both IPv4 and IPv6 can be tunneled over IPSEC (ESP is protocol 50) or GRE (protocol 47, slap a v4 header on an ethernet packet) or SSL, so you have the same data loss prevention risks over v6 that you have been living with over v4.  

  * By the way, ICMPv4 is protocol 1, IGMPv4 is protocol 2, TCP is protocol 6, UDP is protocol 17.  You've been multiprotocol all along.  It's just that in v6 next header (the replacement for protocol) 58 for ICMPv6 is really important. In v4 nodes could be sloppy and violate RFC's by careless blocking all ICMPv4 at a firewall, and they would sort of work, badly, but in cases where nothing was going wrong, they'd limp along seeming successfully.  In v6 you need to be more subtle, as failing to allow ICMPv6 errors types 1-4 and RA/RS plus ND/NS types 133-136 **will break your network**.  Because in v6 most of the exciting ICMP messages are restricted to hop limit 255 and link-local soruces, this is less risky than with ICMPv4.  Neither v4 nodes nor v6 nodes should be careless emitting or believing ICMP redirect messages; those should only be coming from routers on networks with multiple uplinks.

The problem with trying to ping6 ff02::2 is that link-local multicast groups are valid on all interfaces.  Ditto for fe80::/64 scope link-local sources.  You will have to specify which interface you want the packet to go out on.  Try e.g.```
ping6 -I eth0 ff02::1
```to see which IPv6 hosts you have on-link with you.

---

### Post by 1clue on 2012-11-03
Wow, a lot of information there.

I think I got about half of that, optimistically.  I'll go through it again until it makes sense.

Your -I eth0 worked.

I've read about scopes for IPV6 several times and for some reason I still get messed up on link-local and all that.  I figured with practice it would all make sense, just not there yet.  I keep thinking link-local is the network attached to an interface card (eth0, eth1, etc) but evidently that's not quite it.

Thanks a bunch for your help.

---

### Post by lemming465 on 2012-11-05
Address scopes is a slightly fuzzy concept in IPv6.  We see them on unicast addresses, even though technically they are defined on multicast addresses.  Potentially there could be 16 multicast scopes, since they use a 4-bit field for them.  So far only 7 have been defined with 2=link-local and e=global being popular.  1=node isn't heavily used.  No one seems to be quite sure what the distinction between 4=admin-local, 5=site-local, and 8=organization local really means in practice.  In both unicast (1 destination) and multicast (multiple destinations) the big distinction is between node-only (e.g. loopback), link-local (usable with immediate neighbors) and global (usable past routing hops with the general internet).  On the unicast side link-local scope addresses have special prefix fe80::/64.  Deprecated site-local scope addresses used to have special prefix fec0::/10.  Multicast has ff::/16 as its marker, but the next 8 bits are 4 flag bits plus four scope bits, which is why you see a lot of ff02::/64 stuff: multicast, no flags, link-local scope, group ID mostly down in the low bits, e.g. for neighbor discovery.

The tricky point to wrap your head around regarding link-local addresses is how the interaction between the the address, the interface, the link, and the node plays out.  The addresses are assigned to interfaces.  The addresses are only valid within a particular scope.  The scopes at network layer 3 in the OSI reference model (IPv4 or IPv6 in TCP/IP internets) interact with the implementation technologies at layer 2, e.g. over ethernet broadcast (in v4) and multicast (in both v4 and v6) are both layer 2 ethernet concepts and layer 3 IP concepts.  These days ethernet scope tends to be synonymous with VLAN broadcast reach, which fuzzes things across multiple switches and ports in network administrator defined ways.  What fun!

Back at the fe80::/64 link-local unicast scope addresses.  All IPv6 interfaces have these, since you can't find routers or neighbors without them.  The node has to have one or more strategies for picking the host parts of these addresses.  Strategies include the unlikely case of static assignment, the more typical case of EUI-64 mapping from the 48-bit ethernet address, or the privacy approach of picking most of the bits at random.  Let's say we're a typical Linux notebook with 3 hardware network interfaces for ethernet, wifi, and bluetooth.  Each one has a 48-bit ethernet style MAC address, which gets prefixed by fe80:: to make a 128-bit interface identifier with link-scope.  So "ip address show" will exhibit 4 interfaces, loopback, ethernet, wifi, and bluetooth.  They'll all have link/ether scope layer 2 addresses (null for loopback), and at layer 3 maybe some ipv4 "inet" family address, and an inet6 family link-local address.  If you have a configured IPv6 global scope address, say on eth0, you'll have at least two inet6 family addresses, the link-local scope one starting with fe80, and the global scope one starting with 2. 

Now consider the routing dilemma for trying to ping ff02::2, all routers.  It's got multicast scope 2, link-local, so we're going talk to it using a link-scope unicast address.  But we've got 3 of those.  Which interface should we use?  In the IPv6 literature the link-scope destinations have to be further qualified with a "zone identifier" to resolve this dilemma.  The official notation is address%zone, but what the zone ID is allowed to be is implementation specific.  On windows zones are numeric and show up in the output of "ipconfig /all".  On Linux they might be the name of the interface, e.g. %eth0, but not all commands like that sort of thing yet.

The whole scope versus interface versus address family thing may become a bit clearer if you run```

ip address show
ip maddress show
ip -4 route show
ip -6 route show
```

---

