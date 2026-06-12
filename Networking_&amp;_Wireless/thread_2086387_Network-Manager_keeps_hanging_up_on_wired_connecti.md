---
title: "Network-Manager keeps hanging up on wired connection"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by Mozai on 2012-11-20
TL;DR  wired ethernet works just fine if I don't let Network-Manager manage it, but if I entrust it to network-manager, it is constantly shutting down and restarting the interface because "(reason 'carrier-changed')"

Ubuntu: 12.10
Packages: 
 - network-manager 0.9.6.0-0ubuntu7
 - isc-dhcp-client 4.2.4-1ubuntu10.1
 - ifupdown        0.7.2ubuntu2
 - kernel          3.5.0-18-generic
Hardware:
 - Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
 - using kernel module 'e1000e'

Expected behaviour:
  $ sudo service network-manager start
Network manager does not see any mention of eth0 in /etc/network/interfaces, assumes it is intended to be managed.  Checks the device, sees ethernet carrier signal, launches dhclient to configure the network interface device.  If I break the physical wires (pulling the cable out of the jack), network-manager will notice that carrier is lost, terminate dhclient, set the network interface's state to 'down' and remove related routes from the routing table.

What happens instead:
  $ sudo service network-manager start
Notify OSD says "Wired network Disconnected - you are now offline" every 15 seconds, repeatedly.  routes table is always empty, and I'm seeing many instances of dhclient starting and getting killed.

I've seen people who wish to help insist on posting device stats and logfile entries -- Network Manager is noisy, and posting all 425 lines here may be excessive (I had to gzip it before attaching it as a file since the original size exceeded this forum's limits.  I think these quotes are the relevant bits:

>     *-network
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=1.7-7 ip=192.168.0.198 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s

...
NetworkManager[15152]: <info> (eth0): device state change: ip-config -> unavailable (reason 'carrier-changed') [70 20 40]
NetworkManager[15152]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
NetworkManager[15152]: <info> (eth0): canceled DHCP transaction, DHCP client pid 15157
NetworkManager[15152]: <info> (eth0): taking down device.

This is what I'd expect to see if I pulled out the cable or turned off the hub, but I'm not doing either of these things.


When I add the line 'iface eth0 dhcp' to /etc/network/interfaces, and restart network-manager so it will not try to manage this interface, my network interface works just fine with the old 'ifdown eth0; ifup eth0' commands from before network-manager.  So it's not the wires, nor something the network interface or drivers uses anywhere but in collaboration with network-manager.


I would like Network-Manager to manage the wired interface again, so I do not need to manually un-do the wifi settings and manually re-do the wired settings as I move this laptop from table to table.

---

### Post by larytet on 2012-11-30
I confirm the problem. The Ethernet works just fine both DHCP and static IP if I add the interface to the /etc/network/interfaces

Network manager can not bring the link up and reports "Cable unplugged". 

There is no light (?) on the Ethernet connector. It appears that Ethernet is really down (hardware). On the Ethernet switch  the light slowly blinks.

Hardware Zotac Neon, Intel Ethernet

---

