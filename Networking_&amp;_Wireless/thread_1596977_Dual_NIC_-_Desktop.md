---
title: "Dual NIC - Desktop"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by FNxGuy on 2010-10-14
I've just installed 10.10 on a desktop with DUAL NICs, both have static IPs. The both work fine and are connected to 2 different networks. eth0 is used for internal (and right now everything else). The network bandwidth on this side is extremely slow. eth1 is setup for higher bandwidth access. 
 
I'm trying to set this up so that any external traffic goes thru eth1 so I don't have to wait 45 minutes for a 5 MB download.
 
I did my search but so far everything dual-nic related seems to be server side. Any help would be appreciated.

---

### Post by annoyingrob on 2010-10-14
You'll have to do a little bit of research on setting up network routes under linux. Most of it WILL apply to servers acting as routers and such, but your desktop will be set up similarly.

---

### Post by kreggz on 2010-10-14
you could mess around with static routes or you could try not setting the default gateway on eth0

---

### Post by Iowan on 2010-10-14
Check **route -n** to verify the (only) gateway goes through eth1.

---

### Post by FNxGuy on 2010-10-15
They are on 2 different networks, each with their own gateway.  Removing one gateway does work, but I was trying to do this thru routes.  Thanks for the help!

---

### Post by SeijiSensei on 2010-10-15
Let 192.168.1.0/24 be the internal network (eth0) with gateway 192.168.1.1 and 192.168.2.0/24 be the external network (eth1) with gateway 192.168.2.1.  You need to use the "ip" command to add these routes:

```

ip route add 192.168.1.0/24 dev eth0
ip route add 192.168.2.0/24 dev eth1
ip route add default via 192.168.2.1

```

Now traffic for the internal network goes out eth0, and external traffic goes out eth1 via 192.168.2.1.  If there are other internal networks that you need to reach via 192.168.1.1, you'll need to add specific static routes like this:

```

ip route add 192.168.100.0/24 via 192.168.1.1

```

I usually put static routes into /etc/rc.local, which is the last startup script run during boot.  There's probably some "official" place to put them as well.  Of course all these commands need to be run as root (using "sudo" if you're testing from the command prompt).

---

### Post by pricetech on 2010-10-15
Remove the gateway on your internal NIC.  You can add the route using the route command if you want, but it's a lot easier to just add it in the network manager where you configure your other network settings.

For example;
My eth0 was my primary connection set up to access the Internet etc via our broadband gateway.
My eth1 had no gateway, but had a route added to access all our internal networks thusly:
Network 192.168.0.0 netmask 255.255.0.0 gateway 192.168.0.1 (assuming 192.168.0.0 is eth1's subnet and .1 is the router on that subnet)

Worked like a charm.

---

### Post by wkearney99 on 2010-10-15
> **SeijiSensei said:**
> I usually put static routes into /etc/rc.local, which is the last startup script run during boot.  There's probably some "official" place to put them as well. 

Wouldn't it be appropriate to put these into /etc/network/interfaces?

As in:```

auto eth0
iface eth0 inet static
        address 192.168.1.37
        netmask 255.255.255.0
        gateway 192.168.1.1
        post-up ip route flush dev eth0
        post-up ip route add 192.168.1.0/24 dev eth0
        pre-down route del -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1

auto eth1
iface eth1 inet static
        address 192.168.2.37
        netmask 255.255.255.0
        gateway 192.168.2.1
        post-up ip route flush dev eth1
        post-up ip route add 192.168.2.0/24 dev eth1
        post-up ip route add default gw 192.168.2.1
        pre-down route del -net 192.168.12.0 netmask 255.255.255.0 gw 192.168.12.1
        pre-down route del default gw 192.168.2.1

```

---

### Post by SeijiSensei on 2010-10-15
As I said, I don't always do things the "official" way.  Partly that's because I manage both RedHat and Ubuntu Linux distros which have rather different ways of configuring networking.  I'm more than happy to believe your suggestions are the correct method for Ubuntu/Debian.

Also I've been doing this stuff for about fifteen years now. Over that time distros have come and gone, and even the methods used for earlier versions of distros like RedHat were replaced by different methods in later versions. So I've tended to use methods that I know work pretty much across various distributions like placing things in /etc/rc.local.

By the way, the "iproute2" command syntax is a bit simpler than the older BSD-style "route" command.  You can replace 

```
route del -net 192.168.12.0 netmask 255.255.255.0 gw 192.168.12.1
```
with 
```
ip route del 192.168.12.0/24 via 192.168.12.1
```

---

### Post by wkearney99 on 2010-10-15
> **SeijiSensei said:**
> As I said, I don't always do things the "official" way.  Partly that's because I manage both RedHat and Ubuntu Linux distros which have rather different ways of configuring networking.  I'm more than happy to believe your suggestions are the correct method for Ubuntu/Debian.

Also I've been doing this stuff for about fifteen years now. Over that time distros have come and gone, and even the methods used for earlier versions of distros like RedHat were replaced by different methods in later versions. So I've tended to use methods that I know work pretty much across various distributions like placing things in /etc/rc.local.

By the way, the "iproute2" command syntax is a bit simpler than the older BSD-style "route" command.  You can replace 

```
route del -net 192.168.12.0 netmask 255.255.255.0 gw 192.168.12.1
```with 
```
ip route del 192.168.12.0/24 via 192.168.12.1
```

Six of one, as they say, regarding the use of route vs ip.  They both get the job done.  

I pointed out the use of the interfaces file and the pre and post commands because they're integrated with other features of the distro.  This being an ubuntu-related forum it seems useful to focus on how it handles this.  

It becomes more important when dealing with come-and-go networking, like wireless or VPN connections.  Going with where the distro expects them to be helps avoid conflicts.  That and you also get the connections and routes handled automagically when the interfaces are brought up or down.  Using the rc scripts is likely to only get them fired at boot time.  I'm all for going with traditions, except when it's likely to make for greater headaches down the road.  Sometimes change is good.  But go with whatever works best for you.

---

### Post by FNxGuy on 2010-10-19
We set eth0 to connect only to resources on it's network (making sure the subnet was setup correctly).  Then made eth1 the default, added DNS from eth0

Probably the wrong way to about this but I got the end result I was looking for.


Thanks for the insights and the help.

---

