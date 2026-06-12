---
title: "MAC address change to eth0 doesn't stick"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by letsplayfootsy on 2013-02-06
Hey everyone,
I'm having trouble trying to get my requested MAC address to "stick".
I would like to spoof a MAC address on eth0, however any attempts to make it stick seem too "hackish".

If I make changes in the GUI (I guess this is the preferred method of doing it), the MAC address is reset (to the real MAC) as soon as I plug in the ethernet cable.

If I then delete the entry from Wired Connections, change the MAC using:
```

ifconfig eth0 down
ifconfig eth0 hw ether <desired-mac-address>
ifconfig eth0 up

```
and then plug in an ethernet cable, it works (huzzah!).

However, once I unplug the ethernet cable, the address reverts to the original (doh!). My current workaround is to run the above code in /etc/network/if-post-down.d/ and it will reset it to my desired mac address once again, ready for the next time I plug it in.

Unfortunately, this is not the only time the mac-address gets reset. Under some conditions (which I haven't tested yet, but likely related to sleep/resume), the interface STILL finds a way to get reset to it's original setting. 

What is the method that will tell Ubuntu that whenever the interface gets reset, assign it THIS mac address?

---

### Post by letsplayfootsy on 2013-02-07
Bump.
I messed with it a few hours again yesterday, but no luck so far. Anybody else can confirm/deny that they have this problem as well? I guess this is either a bug with NetworkManager or a compatibility issue with the hardware. It would be really nice to let Network Manager handle the connections, but it seems the facility for changing the MAC address is broken.

I'm powered by the e1000e driver. lshw gives me this:

```

$ lshw -C net
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 00:15:f2:4c:f9:e2
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-3 latency=0 multicast=yes port=twisted pair
       resources: irq:47 memory:f3500000-f351ffff memory:f353b000-f353bfff ioport:6080(size=32)

```

---

### Post by linux nubee on 2013-03-19
> **letsplayfootsy said:**
> Bump.
I messed with it a few hours again yesterday, but no luck so far. Anybody else can confirm/deny that they have this problem as well? I guess this is either a bug with NetworkManager or a compatibility issue with the hardware. It would be really nice to let Network Manager handle the connections, but it seems the facility for changing the MAC address is broken.

I'm powered by the e1000e driver. lshw gives me this:

```

$ lshw -C net
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 00:15:f2:4c:f9:e2
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-3 latency=0 multicast=yes port=twisted pair
       resources: irq:47 memory:f3500000-f351ffff memory:f353b000-f353bfff ioport:6080(size=32)

```

I have the same problem, and came across your post while looking for a solution. Did you ever find a fix?

---

### Post by letsplayfootsy on 2013-03-19
> **linux nubee said:**
> I have the same problem, and came across your post while looking for a solution. Did you ever find a fix?

No unfortunately not. I am currently (manually) running a script to change the mac address before docking my laptop. Let me know if you do find something though, I haven't had the time these days to mess around with it. Luckily I only need to run it once or twice a day, but if more, it would definitely be a bigger issue.

---

