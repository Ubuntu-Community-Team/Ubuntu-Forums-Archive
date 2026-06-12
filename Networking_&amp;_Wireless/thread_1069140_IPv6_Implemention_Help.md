---
title: "IPv6 Implemention Help"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by wiz561 on 2009-02-13
Hi,

I am new to IPv6 and attempting to implement it on our network.  We are NOT tunneling anything through a 3rd party.  Basically, our network admin said that the network is 2001:400...blah.../64, the gateway is 2001:400...blah...:1, and that we can use 2001:400...blah...:2 - FFFF.

On the server, I am running IPv4 and use it as a 'gateway'.  I have the public interface side eth0, and eth1 is the private subnet.  Nothing special is being done; just the usual home nat type setup.

On the server, I have configured it to successfully use IPv6 and can ping ipv6.google.com without any problems.  I did this by putting the following in /etc/network/interfaces...

iface eth0 inet6 static
	address 2001:400:<blah>::5
	netmask 64
	gateway 2001:400:<blah>::1


Now, what I want to do is have my machines behind the firewall/nat box be able to use IPv6 as well.  I setup radvd with the following in the config....

interface eth1
{
	AdvSendAdvert on;
   	prefix 2001:400:<blah>::/64
	{
	};
};   


Now, my problem is that the machines behind the firewall get an IPv6 number like...

          inet6 addr: 2001:400:<blah>:20c:29ff:fee5:cae/64 Scope:Global

But if I try to ping something, I get a strange error...

$ ping6 2001:400:2210:99::1
PING 2001:400:2210:99::1(2001:400:2210:99::1) 56 data bytes
From 2001:400:2210:99:20c:29ff:fee5:cae icmp_seq=1 Destination unreachable: Address unreachable
From 2001:400:2210:99:20c:29ff:fee5:cae icmp_seq=2 Destination unreachable: Address unreachable
From 2001:400:2210:99:20c:29ff:fee5:cae icmp_seq=3 Destination unreachable: Address unreachable

--- 2001:400:2210:99::1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5016ms

$ c


I believe the reason why this is happening is because eth1 is not forwarding the traffic to eth0 on the server/nat/gateway/firewall box.  However, I setup in sysctl.conf file the following...

# cat /proc/sys/net/ipv6/conf/all/forwarding
1
# 


I'm in a crunch for time to get out of work, but I am hoping that somebody might be able to give me a few hints on how to get this thing working.


Thanks!

---

### Post by netztier on 2009-02-13
> **wiz561 said:**
> 

Now, my problem is that the machines behind the firewall get an IPv6 number like...

          inet6 addr: 2001:400:<blah>:20c:29ff:fee5:cae/64 Scope:Global



Expected. The radvd announces the 2001:0400:<blah> prefix, and the machines are making up the host part (the second 64bits) of their IPv6 address by EUI64-converting their 48bit MAC address to 64bits.

> **wiz561 said:**
> 
But if I try to ping something, I get a strange error...

$ ping6 2001:400:2210:99::1
PING 2001:400:2210:99::1(2001:400:2210:99::1) 56 data bytes
From 2001:400:2210:99:20c:29ff:fee5:cae icmp_seq=1 Destination unreachable: Address unreachable


Expected as well.

Your box now has *both* it's eth0 and eth1 in the same subnet - the same thing happens when you assign 192.168.1.1 to ethX and 192.168.1.2 to ethY (each time with subnet mask 255.255.255.0) ona a single box. You can't **route** between interfaces in the same subnet.

You either have to set up a *bridge* between eth0 and eth1 and give the IPv6 address to the (virtual) bridge interface (most often named br0), and then you can assign addresses out of your subnet to machines behind eth1 as well.

Or you'll have to ask your admin for another /64 IPv6 prefix (aka subnet) that you use for the network behind eth1, and then ask him to configure a (static) route for that subnet pointing to your box' eth0 address 2001:400:<blah>::5. And then of course you need to enable forwarding for IPv6 on your box. 

See /etc/sysctl.conf
```
# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1

```

If network address assignment was done properly, your network admin has at been given at least a /48 prefix for the institution/organisation. That makes for 2^16 or 65'536 /64 prefixes he can allocate across his networking domain - He might just as well assign a handful of these to you.

NAT? IPv6 don't need no NAT... It can be done, possibly, and iptables might even be able to do so. Yet, one of the design goals of IPv6 was to eliminate the need for NAT - so why should you?


regards

Marc

---

### Post by wiz561 on 2009-02-15
Thank you for the response.  I am new to IPv6 and attempting to learn.  It sounds to me like I'm sort of on the right track and all that I should have to do is bridge eth0 and eth1.  I'll make an attempt to do this next week and see what happens.

Thanks again for the information.
Mike

---

### Post by netztier on 2009-02-16
> **wiz561 said:**
> Thank you for the response.  I am new to IPv6 and attempting to learn.  It sounds to me like I'm sort of on the right track and all that I should have to do is bridge eth0 and eth1.

Be aware though - you might be bridging more that just IPv6 that way, but the entire network that is "behind" your router box. It might not be what you intended. 

You might want to see if you can configure bridging for IPv6 only (ethertype 0x86DD, where IPv4 has ethertype 0x0800), so that you don't break your current IPv4 setup with NAT.

Also worth checking if you do bridging: the need for your own radvd, it might not be needed anymore. Don't your network admins run one in the 2001:400:<blah>: /64 subnet for you, probably on a router of theirs?

regards

Marc

---

### Post by wiz561 on 2009-02-17
> 

 Don't your network admins run one in the 2001:400:<blah>: /64 subnet for you, probably on a router of theirs?


I will check, but don't you need to run radvd to hand out addresses?  I was under the impression that you need this or else it will fail.  I guessed this because nothing is ever that easy.

Thanks!

---

### Post by wiz561 on 2009-02-17
Another question...  How does one go about bridging the interface so that it will work correctly?  I put the following in my network/interfaces file, but it seems like when I restart the interface, an ipv4 number does not get assigned to the interfaces and I can't pass traffic.  :(  Also, for what it's worth, I am running Shorewall.

---
# The loopback network interface
auto lo
iface lo inet loopback
	# address		127.0.0.1
	# netmask		255.0.0.0

# List of hot pluggable network interfaces.
auto eth0
auto eth1
auto br0

# the outside interface
iface eth0 inet static
	address		192.x.x.x
	netmask		255.255.255.224
	gateway		192.x.x.225

iface eth1 inet static
	address		192.168.101.1
	netmask		255.255.255.0
	broadcast	192.168.101.255
	network		192.168.101.0

iface eth0 inet6 static
	address 2001:400:<blah>::5
	netmask 64
	gateway 2001:400:<blah>::1

#the local network bridge
 iface br0 inet static
	bridge_ports eth1 eth0
	address 2001:400:<blah>::4
	netmask 64
	gateway 2001:400:<blah>::1

---



Thank you again for all the help!

---

### Post by netztier on 2009-02-17
> **wiz561 said:**
> I will check, but don't you need to run radvd to hand out addresses? 

Why yes, a router should be advertising the prefix(es) for the local subnet - but there's no obligation to do so. There is also DHCPv6 that can do the job, in a "small" version to compliment a radvd's possibilities; for example, a router (or a radvd) can't hand out information about DNS servers in it's advertisments. Then there's the "stateful" version of DHCPv6 which works pretty much the way we know it from DHCPv4.

That's why I wondered if your network admins had one running in the local subnet - after all, there seems to be an IPv6 enabled router in the subnet, or else you would'nt be able to connect anywhere using v6.

If you'd bridge eth0 and eth1 together to form br0, the router's (or some other radvd's) advertisments would also reach the network segment behind your box, and hosts back there could learn the prefix that way.

However if you already have IPv4 running and use shorewall to configure the NAT and routing - things are going to get difficult; you'd have to make sure that only the relevant Layer2-protocols and IPv6 are be bridged, excluding bridging of IPv4. In that case, only br0 should have an IPv6 address, eth0 and eth1 themselves should only have IPv4 adresses.
Now how such a "selective bridging of IPv6 only" would be configured - I have no clue right now.

Coming to think of it... bridging and routing on a same box is just asking for configuration trouble - makes me shudder when I think of the days back at my employer where the same routers had to bridge NetBEUI and route IP (of course with OSPF and RIP) at the same time.

It might be worth checking if iptables/shorewall is IPv6 enabled after all. Then you could generate a "private" /48 IPv6 prefix [1] for your network (just like the 192.168.x.x addresses), assign a single /64 subnet from that range to eth1, turn on radvd on it and have the systems behind eth1 use these addresses.

Maybe shorewall/iptables can then do what was not intended to happen with IPv6: NAT.

I still consider this the best option: ask the network admin to give you a second /64 prefix from their range that you can use behind your box.

regards

Marc



[SIZE="2"][1] [ RFC4193 ]("http://tools.ietf.org/html/rfc4193") defines a range in the IPv6 address space that can serve a similar purpose as the RFC 1918 addresses (10.x.x.x, 172.16-31.x.x, 192.168.x.x) do. The address space is called "Unique Local Unicast" ([http://www.iana.org/assignments/ipv6-address-space](http://www.iana.org/assignments/ipv6-address-space)) and it's addresses all start with FC00:: or FD00::. Also see: [http://en.wikipedia.org/wiki/Unique_local_address](http://en.wikipedia.org/wiki/Unique_local_address), where you find a link to a tool that will generate a probably globally unique /48 prefix for you.[/SIZE]

---

### Post by wiz561 on 2009-02-17
Thanks again for the information.  I kind of wished that there was a good page write up on this somewhere without using a tunneling provider.  It seems like almost all of the writeups I've seen use sixxs or freenet6.

I know the latest version of shorewall is ipv6 capable, but the version that is in the ubuntu repo is not.  I'm toying with the idea of getting rid of shorewall and just configure everything by hand.  After all, I believe that is the only real way of knowing and controlling what is going on.

Thank you again for all of your help.  If you have any web pages of reference, howto's, tutorials, etc., that would be great if you can post.

Thanks!

---

