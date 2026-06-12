---
title: "Pass eth1 through eth0 to router"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by Durkslag on 2013-06-20
Hi!

I've been searching the Internet for a while, found some answers but nothing works, so I'm trying with the pros (yes, you!).

I have a home server running Ubuntu Server (so no GUI) with a build in ethernet card, eth0, connected to the router. The server gets a reserved IP number through DHCP and everything works great.

I also have a Raid card (Areca Arc-1230) with it's own ethernet port and built in web interface. I wanted to be able to connect to this card with a normal IP-number. This works of course if I connect the raid card with a cable to the router. The problem is that currently I only have one ethernet jack where the server is and that one is connected to eth0 for network connection to Ubuntu.

So i bought a second network card and installed it to the server and connected it with a small cable to the Raid Card. Here's a picture explaining it:
"Till router" means to router :)
[IMG]http://oi40.tinypic.com/ff9yjq.jpg[/IMG]

How do I make the Raid Card connectable to the router so I can access it from my LAN? Either with it's own LAN IP or through the server with it's own port.
Tried bridging eth1 and eth0 but not sure I'm doing it right.

Here's my /etc/network/interfaces:
```

# The loopback network interface
auto lo
iface lo inet loopback


# The default network card connected to router
auto eth0
iface eth0 inet dhcp


# The new, extra ethernet card
#auto eth1
#iface eth1 inet manual    # or something?

```

And here's the raid card ethernet settings when connected to the router:
[IMG]http://oi42.tinypic.com/2qsotpl.jpg[/IMG]

I'm not very good with network and hopefully this isn't that hard to solve :)

Thank you in advance!

---

### Post by scbingham on 2013-06-20
A very simple way could be to use a cat5/6 splitter ie 2 into 1.

---

### Post by Durkslag on 2013-06-20
You mean like a switch? I don't want to use one because of the location of the server.
I considered a splitter on each side that only uses 4 out of the eight wires in the TP cable but the one I could get at work only provides 100 Mbit/s due to only using 4/8 wires.

Preferably I'd like to avoid a hardware solution to this problem. 

But maybe you're right. It might be a lot easier to solve it that way :) maybe I need to buy a gigabit switch...
Thanks for the reply!

---

### Post by SeijiSensei on 2013-06-20
Put eth1 and the RAID card into a different IP subnet from that in use by eth0.  I'd make sure to use static addressing for all the interfaces so you can control their addresses.  DHCP is not an appropriate solution for things like servers where addresses need to remain fixed.  Read this for details: [https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)

---

### Post by Durkslag on 2013-06-20
Thanks for answering, SeijiSensei!

I don't know much about network and even less about subnets. I read a little about it and it seams way to advance for me to learn atm, at least for this problem.
Think I just have to buy a switch and try to make it fit. 

I have reserved an IP number in my router for the MAC address of the server's ethernet card. So it will always get the IP 192.168.1.101 and no other device could get that IP even if the server was shut down. Isn't that enough or should I make it static even in the interfaces file?

---

### Post by SeijiSensei on 2013-06-20
MAC reservation is fine.

On eth1 and the RAID card you could use 192.168.2.1 and 192.168.2.2.  You'll need to set the RAID address with its utility; to set eth1, edit the file /etc/network/interfaces and add this stanza:
```

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0

```

If you need to see the RAID from a machine connected to eth0 via the router, then you'll need to enable IP forwarding.  If all that matters is that the new Ethernet card talk to the RAID card, you can skip this.  To enable IP forwarding, edit (as root with sudo) the file /etc/sysctl.conf and uncomment the "net.ipv4.ip_forward=1" directive.  When you have edited both files, reboot.

You should now be able to ping your router with "ping 192.168.1.1" (assuming that is the router's address) and also ping the RAID card with "ping 192.168.2.2".  If something doesn't work, run the command "route -n" and post the results here in [noparse][code][/noparse] tags.

---

### Post by scbingham on 2013-06-20
I was thinking of something much simpler:

[http://www.ebay.co.uk/itm/2X-RJ45-CAT-5-6-LAN-Ethernet-Splitter-Connector-Adapter-Plug-Coupler-Extender-PC-/310669662421?_trksid=p5197.m2280&_trkparms=aid%3D222002%26algo%3DSIC.FIT%26ao%3D1%26asc%3D191%26meid%3D8519717130230925494%26pid%3D100068%26prg%3D1104%26rk%3D1%26sd%3D350794813996%26%26clkid%3D8519717089347878420&_qi=RTM1177911](http://www.ebay.co.uk/itm/2X-RJ45-CAT-5-6-LAN-Ethernet-Splitter-Connector-Adapter-Plug-Coupler-Extender-PC-/310669662421?_trksid=p5197.m2280&_trkparms=aid%3D222002%26algo%3DSIC.FIT%26ao%3D1%26asc%3D191%26meid%3D8519717130230925494%26pid%3D100068%26prg%3D1104%26rk%3D1%26sd%3D350794813996%26%26clkid%3D8519717089347878420&_qi=RTM1177911)

Basically this gives you 2 ports from the one you already have.

---

### Post by Durkslag on 2013-06-20
I really appreciate you taking time helping me!
I could buy a switch if this won't work so don't spend too much time on this if you don't want to :)

I've done what you said and from the server I can ping both 192.168.2.1 and 192.168.2.2.
But how do I access it from another computer in the LAN through the router (192.168.1.2)?

I have uncommented net.ipv4.ip_forward=1 and rebooted. UFW is turned off btw.
Will check the router settings.

Heres my "route -n"
```
 
Kernel IP routing table
Destination     Gateway         Genmask        Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.2     0.0.0.0            UG    100    0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

Here's my /etc/network/interfaces:
```

# The loopback network interface
auto lo
iface lo inet loopback


# The default network card connected to router
auto eth0
iface eth0 inet dhcp


# The extra NIC for connection to Areca Raid
auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0

```

The Raid Card has these settings:
Local IP: 192.168.2.2
Gateway IP: 192.168.2.1   # tried both server IP and router IP 
Subnet Mask: 255.255.255.0

--- --- ---

> **scbingham said:**
> I was thinking of something much simpler:

[http://www.ebay.co.uk/itm/2X-RJ45-CAT-5-6-LAN-Ethernet-Splitter-Connector-Adapter-Plug-Coupler-Extender-PC-/310669662421?_trksid=p5197.m2280&_trkparms=aid%3D222002%26algo%3DSIC.FIT%26ao%3D1%26asc%3D191%26meid%3D8519717130230925494%26pid%3D100068%26prg%3D1104%26rk%3D1%26sd%3D350794813996%26%26clkid%3D8519717089347878420&_qi=RTM1177911](http://www.ebay.co.uk/itm/2X-RJ45-CAT-5-6-LAN-Ethernet-Splitter-Connector-Adapter-Plug-Coupler-Extender-PC-/310669662421?_trksid=p5197.m2280&_trkparms=aid%3D222002%26algo%3DSIC.FIT%26ao%3D1%26asc%3D191%26meid%3D8519717130230925494%26pid%3D100068%26prg%3D1104%26rk%3D1%26sd%3D350794813996%26%26clkid%3D8519717089347878420&_qi=RTM1177911)

Basically this gives you 2 ports from the one you already have.
That adapter won't allow me to use both connection simultaneously. It will only work with one NIC at a time.
I could use something like this: [http://oi40.tinypic.com/2prem3d.jpg](http://oi40.tinypic.com/2prem3d.jpg) . One at the router and one at the server but it only supports 100 MBit/s. Thanks for helping though :)

---

### Post by SeijiSensei on 2013-06-20
You probably need to add a static route on your router for the 192.168.2.0 network with subnet mask 255.255.255.0 and 192.168.1.101 as the gateway.  What is happening now is that traffic sent to 192.168.2.2 arrives at the router and is then sent out over the Internet rather than to the Linux box because the router's default gateway is upstream.  I bet if you add that route everything will work as expected.

---

### Post by Durkslag on 2013-06-21
I think all this was too difficult for me to achieve :confused:

I feel a little bad for all the time you spent helping me when I can't get it to work.
I am very thankful! You don't have to put any more effort into this, I'll go the hardware way from now on.

[IMG]http://f.cl.ly/items/3I08251U1t091Y1R0j1n/dir655.png[/IMG]

---

### Post by SeijiSensei on 2013-06-21
That error makes no sense to me.  How can 192.168.1.101 not be in the "interface subnet" of 192.168.1.2?  It makes even less sense since you are assigning the 101 address with a MAC reservation!

---

