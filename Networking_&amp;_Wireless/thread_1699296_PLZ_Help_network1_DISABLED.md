---
title: "PLZ Help network:1 DISABLED"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by MrFire on 2011-03-03
p { margin-bottom: 0.21cm; }  Requirement: Need to connect more than 1 USB to Ethernet adapter on my PC.
 

 Problem: Although drivers are recognized by Ubuntu 10.10 & USB NIC are also working, when 	    connected individually.
 

 	    But the problem arrises when I try to connect more than 1 USB NIC, the second one is 	    disabled & not able to communicate to the network.
 		
  Note:     The USB NIC have the same MAC address can this cause the problem. If so how do i change MAC address & enable the eth2-eth1 interface.
 	    
 	   eth2-eth1 is also not visible in ifconfig display also.
 

 output for: sudo lshw -C network; echo; uname -a; lsb_release -a
 

 *-network                
        description: Ethernet interface 
        product: 82567LF-2 Gigabit Network Connection 
        vendor: Intel Corporation 
        physical id: 19 
        bus info: pci@0000:00:19.0 
        logical name: eth0 
        version: 00 
        serial: 00:1c:c0:90:16:10
        capacity: 1GB/s 
        width: 32 bits 
        clock: 33MHz 
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.8-5 latency=0 link=no multicast=yes port=twisted pair 
        resources: irq:41 memory:e0100000-e011ffff memory:e0124000-e0124fff ioport:f0e0(size=32)


  
   *-network:0 
        description: Ethernet interface 
        physical id: 1 
        logical name: eth1 
        serial: 00:10:13:50:a4:90 
        size: 100MB/s 
        capacity: 100MB/s 
        capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=dm9601 driverversion=22-Aug-2005 duplex=full firmware=Davicom DM9601 USB Ethernet ip=192.168.1.1 link=yes multicast=yes port=MII speed=100MB/s 
 

   *-network:1 DISABLED 
        description: Ethernet interface 
        physical id: 2 
        logical name: eth2-eth1 
        serial: 00:10:13:50:a4:90 
        size: 10MB/s 
        capacity: 100MB/s 
        capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=dm9601 driverversion=22-Aug-2005 duplex=half firmware=Davicom DM9601 USB Ethernet link=no multicast=yes port=MII speed=10MB/s


  
 Linux Fire 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux 
 No LSB modules are available. 
 Distributor ID:	Ubuntu 
 Description:	Ubuntu 10.10 
 Release:	10.10 
 Codename:	maverick

---

### Post by MrFire on 2011-03-03
p { margin-bottom: 0.21cm; }  Well couple of restarts did enable the Disabled interface, but now my final questions is:-
 

 [SIZE=4][COLOR=Red]&#8220; **How do you assign different MAC addresses to two different USB NIC's, having same physical MAC addresses to establish connectivity to a single switch?**&#8221;[/COLOR][/SIZE]
 

 Is it even possible in Ubuntu 10.10?
 

 I tried creating different wired connections (eth1, eth2, etc..) & assign different MAC addresses to it, but it does not work.
 

 Any suggestions PLEASE!:confused:

---

### Post by MrFire on 2011-03-03
The only question that I would like to ask is:


  [SIZE=4]**“[COLOR=Red]Is it possible to change the firmware MAC address of NIC?[/COLOR]”**[/SIZE]


  OR


  [SIZE=4]**“[COLOR=Red]Assign different MAC addresses to different USB NIC, having same firmware MAC Address?[/COLOR]”**[/SIZE]


  OR


  [SIZE=4]**[COLOR=Red]Whatever can provide solution to my problem?[/COLOR]**[/SIZE]


  [FONT=&quot]If the answer is Yes, then how?:confused:

Thanks
[/FONT]

---

### Post by steaksauce on 2011-03-03
> **MrFire said:**
>  Note:     The USB NIC have the same MAC address can this cause the problem. If so how do i change MAC address & enable the eth2-eth1 interface. 

It's impossible to physically change the MAC address of a network interface, however you can spoof it, but I'm sure that it wouldn't work.

I don't know why you would need more than one network interface running at once, unless you connect to multiple networks at once and it would make more sense to combine the networks. Whenever I'm plugged in to my network (wired in) and access it on wireless as well, my Ethernet connection takes priority and my wireless connection is ignored.

But that is within the same network, as for separate networks, I'm not for sure.

Hope that helped a little ;)

---

