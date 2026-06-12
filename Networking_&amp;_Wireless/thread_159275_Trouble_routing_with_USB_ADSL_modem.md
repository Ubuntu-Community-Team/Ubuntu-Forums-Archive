---
title: "Trouble routing with USB ADSL modem"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by walkingbeard on 2006-04-12
Hi!

I've got a PC with a Speedtouch ADSL modem, which works fine, and also a normal ethernet card. I have another machine with an ethernet card.  I've connected the two with a crossover cable and I can successfully ping one from the other.  I just can't get Internet access from the second machine.  I've done this before when I've been using a cable modem connected to the one machine with an ethernet cable, but I can't work it out.

We spent ages trying to get the USB modem working and eventually we got some proper nerds (in a good way) from the local Linux User Group to fix it up for us.  Unfortunately, nobody seems to know how to contact them now.

I'm using Firestarter to look after the firewall and routing stuff, because I haven't found a decent tutorial on doing that kind of thing manually.  Everything appears to be set up right and it reports that the Internet connection is via ppp0, which sounds just right and I set eth0 as the network connection.  There's also sit0, an IPv6 tunnel, which sounds a bit dodgy to me, but I'm not up on these things.  If anyone can be of help, thanks in advance!

route (on the gatewat machine) eth0(192.168.0.2)
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
cr0.wsdou.uk.ea *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         cr0.wsdou.uk.ea 0.0.0.0         UG    0      0        0 ppp0

```

route (on the internal machine) eth0(192.168.0.3)
```
Destination  Gateway  Genmask  Flags  Metric  Ref  Use Iface
192.168.0.0     *   255.255.255.0    U  0   0     0  eth0
```

---

