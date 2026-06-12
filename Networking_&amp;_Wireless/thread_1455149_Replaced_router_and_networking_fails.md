---
title: "Replaced router and networking fails"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by at both ends on 2010-04-15
I replaced my wired router and networking has gone south on one of my boxes.  It's a Dell tower, a few years old, triple boot (ubuntu 8.10, FreeBSD, WindowsXP).  Old router used 192.168.254.* via DHCP, new one is 192.168.2.* via  DHCP.  The router replacement caused no problems for either FreeBSD or WinXP on this box, nor for any of the other boxes on the network (one of which is ubuntu 9.10).

Ubuntu 8.10 simply will not connect to the new router.  I'm presuming that something somewhere down deep has been compromised and I just don't know where to start looking or what buttons to push to reconfigure correctly.  Router status displays show an IP address of 192.168.2.35 for this box, booted under all three operating systems.  Using network-manager to force that static address instead of relying on DHCP does not seem to help.

Can anyone help a n00b find the right toggles?  Clean re-install is an option but rather drastic.

---

### Post by Iowan on 2010-04-15
What's in /*etc/network/interfaces*? If the interface is configured there, NM might not touch it...

---

### Post by at both ends on 2010-04-15
```
# cat /etc/network/interfaces
auto lo
iface lo inet loopback

# ifconfig
eth0      Link encap:Ethernet  HWaddr ...  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202317 (202.3 KB)  TX bytes:2367 (2.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10616 (10.6 KB)  TX bytes:10616 (10.6 KB)

#lshw -C network
  *-network
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: ...
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ...
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```The MAC address is correct, matching what the router says DHCP has assigned 192.168.2.35. The DISABLED on the second interface (Bluetooth?) doesn't seem relevant - no bluetooth on this cheapo Dell - but I'm always willing to be educated if that has some effect.

It's just bizarre. The box has run flawlessly since I installed 8.10, more than a year ago.  I rarely boot BSD or XP and only did today because I thought the NIC might have blown up.  As I wrote earlier, neither of those have any problem with the new router and the new IP supplied by DHCP.

---

### Post by frantid on 2010-04-15
your MTU should be 1500 for ethernet.  It seems to be 64 in your config.  If you did not set it, try to set your router to 100MB full duplex instead of auto.  If your router is new with gig lan, some routers don't fall back correctly with older nic cards.

---

### Post by at both ends on 2010-04-15
Thank you.  Thank you.  Thank you.

NM wouldn't touch it but I forced it with ifconfig and it connected immediately!  Magic!!

Followup questions ...

1) How could I have known that?
2) What could have changed that setting?  I certainly didn't do it myself.

---

### Post by frantid on 2010-04-15
I wouldn't worry about not noticing.  Default for ethernet is 1500, 1492 for ppoe over asdl, etc...  MTU has become less prevalent since broadband became more common.  Networking people, some admins, and others who used to try to increase their performance over dial-up know about it.  It's been plug and play for sometime, it really should be left alone 99% of the time.  I'm just an old networking guy, so I noticed.

I don't know enough about Ubuntu to know the answers of how it got changed. 

It could be just an auto-negotiation error between the new router and the box.

glad it's sorted, cheers.

---

