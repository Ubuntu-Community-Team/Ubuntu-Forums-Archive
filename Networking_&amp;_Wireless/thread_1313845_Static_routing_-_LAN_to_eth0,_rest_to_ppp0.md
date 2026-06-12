---
title: "Static routing - LAN to eth0, rest to ppp0"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by steenbras on 2009-11-04
Hi,

I connect to a wired network mainly for printing and intranet, but use my 3G dongle for all web traffic. At the moment it's a pain to plug in the LAN cable, and print, then unplug as I want to browse.

Ideally I'd like to ensure that all traffic is routed via the ppp0 interface, except for the LAN network which should go to eth0. I've tried doing this without success.

Here's the routing table with the LAN cable unplugged:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1.2.3.4     *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     0      0        0 vboxnet0
link-local      *               255.255.0.0     U     0      0        0 pan0
link-local      *               255.255.0.0     U     0      0        0 usb0
default         1.2.3.4     0.0.0.0         UG    0      0        0 ppp0

```

(replaced actual IP with 1.2.3.4)

Plugging in the LAN cable I get:
> $ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1.2.3.4     *               255.255.255.255 UH    0      0        0 ppp0
10.16.44.0      *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 vboxnet0
link-local      *               255.255.0.0     U     0      0        0 pan0
link-local      *               255.255.0.0     U     0      0        0 usb0
default         10.16.44.1      0.0.0.0         UG    0      0        0 eth0


As you can see, it takes the default route. I thought I could overcome this by removing the default route and specifying it myself:

```
# route del default
# route add default netmask 0.0.0.0 gw 1.2.3.4 dev ppp0
```

Which gives me this routing table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1.2.3.4     *               255.255.255.255 UH    0      0        0 ppp0
10.16.44.0      *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 vboxnet0
link-local      *               255.255.0.0     U     0      0        0 pan0
link-local      *               255.255.0.0     U     0      0        0 usb0
default         1.2.3.4     0.0.0.0         UG    0      0        0 ppp0

```

But that hasn't worked. What am I missing? How can I do this?

---

### Post by hal10000 on 2009-11-04
> 10.16.44.0 * 255.255.255.0 U 1 0 0 eth0
this ip-address is very unlikely, because usually addresses ending with .0 are occupied, so you should give it another address (e.g. 10.16.44.10 or something similar). But if you get this address fom your provider, then it's o.k.

Plug in all your cables and post the content of the file [COLOR="Red"]/etc/network/interfaces[/COLOR]
and/or attach thumbnails of your network-manager configuration for both connections

btw., the best you can do is to buy an ethernet router (costs about 20-40 $)

---

### Post by t0mppa on 2009-11-04
> **hal10000 said:**
> this ip-address is very unlikely, because usually addresses ending with .0 are occupied, so you should give it another address (e.g. 10.16.44.10 or something similar). But if you get this address fom your provider, then it's o.k.

If you bothered to check the mask, you'd have found out that it's simply a route to a subnet, not to a specific IP. And routes to subnets are configured by their network addresses, which indeed are reserved addresses by definition.

> **steenbras said:**
> Which gives me this routing table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1.2.3.4     *               255.255.255.255 UH    0      0        0 ppp0
10.16.44.0      *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 vboxnet0
link-local      *               255.255.0.0     U     0      0        0 pan0
link-local      *               255.255.0.0     U     0      0        0 usb0
default         1.2.3.4     0.0.0.0         UG    0      0        0 ppp0
```
But that hasn't worked. What am I missing? How can I do this?

Is your printer in the 10.16.44.0/24 subnet then and not on some other subnet that needs to be accessed through 10.16.44.1, like the route you removed was providing access to?

---

### Post by steenbras on 2009-11-04
Thanks for the response.

The printer's IP is 10.16.201.98 - that is a different subnet from 10.16.44/24 isn't it? There will be other things, like network shares, etc... but they'll also be on 10.16

I suppose that what I'm after is this - anything to 10.*.*.* via eth0, anything else via ppp0. DNS should resolve via local too, but that's fine - they're 10.16 addresses too.

---

### Post by t0mppa on 2009-11-04
> **steenbras said:**
> Thanks for the response.

The printer's IP is 10.16.201.98 - that is a different subnet from 10.16.44/24 isn't it? There will be other things, like network shares, etc... but they'll also be on 10.16

I suppose that what I'm after is this - anything to 10.*.*.* via eth0, anything else via ppp0. DNS should resolve via local too, but that's fine - they're 10.16 addresses too.

Then just keep the default route with ppp0 and change the eth0 route with ```
route del -net 10.16.44.0 netmask 255.255.255.0 dev eth0
route add -net 10.0.0.0 netmask 255.0.0.0 dev eth0
```

---

### Post by steenbras on 2009-11-04
Excellent t0mppa - thanks very much. I always lose the ppp0 default route to eth0, so the only thing I've added to yours is

```

route del default
route del -net 10.16.44.0 netmask 255.255.255.0 dev eth0
route add -net 10.0.0.0 netmask 255.0.0.0 dev eth0
route add default gw 1.2.3.4 dev ppp0

```

Working perfectly!

---

### Post by t0mppa on 2009-11-04
Are you using Network Manager (or some other GUI) or the /etc/network/interfaces file for handling your connections? Just asking, since it's not too hard to automate the creation of said routes, so you don't always have to do it manually.

---

### Post by steenbras on 2009-11-06
I actually wrote a simple bash script covering the commands in this thread, since it's for my laptop, and when not in the office I'm happy for it to route simply through the 3G dongle, or a normal wifi port. It's only when I need access to the intranet and local printers/file shares etc.

---

