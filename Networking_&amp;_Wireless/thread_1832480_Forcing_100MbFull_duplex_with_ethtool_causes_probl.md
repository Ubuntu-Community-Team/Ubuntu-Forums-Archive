---
title: "Forcing 100Mb/Full duplex with ethtool causes problems"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2011-08-24
I am a network tech at a small ISP, and our Linux router (Ubuntu server 11.04) plugs into a port on a Juniper router that belongs to Telus.

The problem we have is that instead of seeing the 100Mbps that we should be, we are only seeing speeds of about 10-20Mbps. 

When I called Telus, they remotely logged into their Juniper router and said that they were seeing some errors on the port. I then unplugged our Linux server from the Juniper router, and instead plugged in a regular laptop running Ubuntu. A speed test from speedtest.net showed about 10Mbps on the laptop, and the Telus guy told me that they were still seeing errors on the port. The guy suggested that it may be a duplex or speed problem, so I used ethtool on my laptop to check my speed/duplex, and sure enough, the laptop's port was set for half duplex/100 meg instead of full duplex/100 Meg like the Juniper's port was. I tried to use ethtool to change the interface's duplex to 100/full and turn off autonegotiation, but that either caused me to lose my internet completely, or the command did nothing and the interface stayed at half duplex. The command I used was:

```
sudo ethtool -s eth1 speed 100 duplex full autoneg off
```

Then I booted the laptop into Win 7 and forced the network interface into 100/Full duplex state. All of a sudden I started seeing results of 90Mbps+ on speedtest.net. Plugging in my Ubuntu router again however, the results on the LAN side of the router are back to 10Mbps.

Attempting to force 100/full duplex on the ubuntu router with the command above has also been unsuccessful, as this drops the speed down to ~3Mbps and ifconfig on the Ubuntu router starts reporting errors. 

The weird thing is that if I let the ubuntu router's interface autoneg, ethtool reports that the port gets configured for

```
Speed: 100Mb/s
Duplex: Full
```

and the speed speedtest.net reports is ~15Mbps. Also at this point, the Juniper router reports errors while the ubuntu router sees none. 

If on the other hand I try to force it to do the exact same speed and duplex with:

```
sudo ethtool -s eth1 speed 100 duplex full autoneg off
```

The speed speedtest.net reports drops to ~3Mbps and ifconfig starts reporting errors.

Is there a better/different way to force an interface into 100Meg/full duplex and disable autoneg? Or am I doing something wrong?

Edit:

After a lot of digging, it turns out that the speed problem is not caused by the ubuntu server, but the 2km fiberoptic link from the Juniper router to the ubuntu server. I'm still not sure why the laptop running ubuntu would reject my attempts to force it to 100Meg/Full duplex, but that's not important anymore. Now I gotta find someone who will fix the fiber link...

---

