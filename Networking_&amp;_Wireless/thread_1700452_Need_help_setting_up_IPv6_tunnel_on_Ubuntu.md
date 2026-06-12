---
title: "Need help setting up IPv6 tunnel on Ubuntu"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2011-03-05
EDIT:  Solved.  My IPv6 works great now.  See the last post by me to see why it worked.

I set up an IPv6 tunnel at Hurricane Electric and need help.  I'm using Ubuntu 10.04 and am very confused.  I followed this tutorial at [https://wiki.ubuntu.com/IPv6#Get%20connected%20with%20Hurricane%20Electric]("https://wiki.ubuntu.com/IPv6#Get%20connected%20with%20Hurricane%20Electric")

But I think the part about network manager might be a bit out of date.  The part about the gateway is confusing as I don't see any gateway thing in network manager.

---

### Post by lemming465 on 2011-03-05
Oh dear, it looks like someone is going to have to going to do more editing on the wiki page.  The tunnelbroker.net section is a bit incoherent at present, isn't it?

Hurricane Electric doesn't support the *tunnel setup protocol*, so you can't use the gogoc client with it.  Network manager doesn't grok tunnels, and doesn't really like to touch anything mentioned in /etc/network/interfaces.

So, you have two options, both of which involve non-gui stuff.

First, you can just cut and paste the commands tunnelbroker.net will show you if you pick *tunnel details* and click the *show config* button with the dropdown set to *linux-route2*.  You'll see something like:```
modprobe ipv6
ip tunnel add he-ipv6 mode sit remote **209.51.181.2** local **97.87.56.247** ttl 255
ip link set he-ipv6 up
ip addr add **2001:470:1f10:d47::2/64** dev he-ipv6
ip route add ::/0 dev he-ipv6
ip -f inet6 addr
```
The parts in bold will be different for each user and tunnel.
Start up a terminal window (applications -> accessories -> terminal), get a root shell prompt by e.g. **sudo -i**, and cut & paste the command block.
The modprobe makes sure that the kernel has ipv6 support loaded, if it wasn't permanently built in.
The "ip tunnel ..." creates a point to point tunnel, using the outside IPv4 address of your NAT router/firewall/modem as the local side and the selected relay as the remote side, where the relaying will happen.
The "ip link ..." should be self-explanatory; it turns the tunnel on.
The "ip addr add ..." configures the IPv6 address your host is using.
The "ip route add" configures a default v6 route pointing at the tunnel, so that any v6-traffic headed to the general internet will know where to go.
The last line is optional; it just exhibits the addresses on the various interfaces.  You should get output similar to:
> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qlen 1000
    inet6 fe80::221:70ff:fe6b:10c2/64 scope link 
       valid_lft forever preferred_lft forever
9: he-ipv6: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1480 
    inet6 2001:470:1f10:d47::2/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::6157:38f7/128 scope link 
       valid_lft forever preferred_lft forever

It might also be enlightening to compare the output of *ip -4 route show* and *ip -6 route show*.

Anyway, the manual cut & paste method works fine, but has to be repeated each time you boot the computer or restart the network and want IPv6.

For those who would like an automatic, always-on connection, they can put the tunnel configuration into /etc/network/interfaces.  However, anytime their DHCP lease from their upstream ISP mutates, they will have to delete the old tunnel at tunnelbroker.net, make a new one, and fix up the particulars in /etc/network/interfaces.  I'm not entirely happy with the example config on the wiki page; I'm not sure how the tunnel will behave if you don't configure the local address.  Maybe try:```
auto he-ipv6
iface he-ipv6 inet6 v4tunnel
     endpoint **209.51.181.2**
     local **97.87.56.247**
     address  **2001:470:f10:d47::2**
     netmask  64
     up ip -6 route add default dev he-ipv6
     down ip -6 route del default dev he-ipv6
```
Remember, the parts in bold have to be changed to fit your tunnel of the moment.
Ignore references to a *gateway* keyword in the intervfaces(5) man page; that's only useful with staticly configured native tunnels.  Which is why this one use the "up" and "down" keywords to manipulate the default route.  In the IPv6 context, "default" means the same as "::/0"; either will work.  Sometimes you'll see "2000::/3", as all global unicast v6 addresses currently start with "2".

If you have edited /etc/network/interfaces, you can then bring your tunnel up or down manually with *sudo ifup he-ipv6* and *sudo ifdown he-ipv6*.  Since you gave it the "auto ..." treatment, if you reboot or completely restart networking, e.g. *sudo /etc/init.d/networking restart*, then in addition to autostarting the loopback interface and your ethernet or wifi interface, it will autostart the tunnel too.

---

### Post by MechaMechanism on 2011-03-06
Thanks.  I feel bad because I did solve part of the problem already.  I marked the thread solved because I found out about the ip commands at HE.  Anywayhoo the interface file has never worked.  It says Failed to bring up he-ipv6.  If I try to power down it says ifdown: interface he-ipv6 not configured.

This is how I have it configured.  I assume you meant my IP address as handed out by my ISP, I put that in local.

auto he-ipv6
iface he-ipv6 inet6 v4tunnel
     endpoint 72.52.104.74    ##HE website Server IPv4 address: 72.52.104.74
     local 174.44.178.56      ##IP from ISP
     address  2001:470:1f04:1a82::2   ##HE website Client IPv6 address: 2001:470:1f04:1a82::2/64
     netmask  64
     up ip -6 route add default dev he-ipv6
     down ip -6 route del default dev he-ipv6

I would like the interface file to work, however it's not that big of a deal as I only reboot at most once a month.  So redoing the ip commands ain't too bad.  But it would be nice.

---

### Post by MechaMechanism on 2011-03-17
[lemming465]("http://ubuntuforums.org/member.php?u=194283")'s post about the network interface file worked great, that is after a reboot.  After close to three weeks of uptime, a kernel update forced me to do a reboot and voila the network interface file edits finally worked.

Very big thanks go to [lemming465]("http://ubuntuforums.org/member.php?u=194283") for his help on the network interfaces file.  Try a reboot if the interfaces file is not working but do try as a last resort though.

Thanks again [lemming465]("http://ubuntuforums.org/member.php?u=194283")

P.S.  The interface file means I don't have to enter those IP commands upon every reboot.  Thats why I'm excited.

---

