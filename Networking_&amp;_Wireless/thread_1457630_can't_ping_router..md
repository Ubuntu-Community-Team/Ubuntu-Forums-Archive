---
title: "can't ping router."
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by ravenkwill on 2010-04-18
I've been using Linux Mint fairly happily for awhile, but decided to try the 10.04 beta.  I'm having the same problem that I had with ubuntu the last time, which is huge problems accessing the internet through the wireless network. 

I'm working on a Dell Inspiron with a Broadcom BCM4312 802.11b/g wireless card, driver=wl0 driverversion=5.60.48.36 ip=10.42.  I can ping the local machine, but can't ping the router.  

System dual boots with Vista, where I can easily access the router and internet.  

Any suggestions for next steps?

Thanks.

---

### Post by 405jayb on 2010-04-18
Have you tried mac address filtering?

---

### Post by Iowan on 2010-04-18
Did you configure a static IP address for the machine - or did it manage to get a DHCP address?

---

### Post by ravenkwill on 2010-04-19
I didn't configure a static IP address, so it managed it's own address.  I don't know how to do mac address filtering, but will look that up.

Other thoughts?  I'm over my head on this.


Thanks for the support!

---

### Post by Iowan on 2010-04-19
ip=10.42 is only a partial address.
"ping the local machine"- another machine - or "localhost" (which doesn't really check the hardware)?
Check **sudo lshw -C network**. Does **ifconfig -a** verify the IP address you mentioned - and is it on wlan0 (ord whatever your wireless interface is called) or is it on the wired one (eth0)?

---

### Post by ravenkwill on 2010-04-20
My bad - I cut the line with the IP address and didn't notice.  Here's the results:

sudo lshw -C network
  *-network               
       description: Wireless interface 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth1 
       version: 01 
       serial: 00:22:5f:c5:85:9d 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 
multicast=yes wireless=IEEE 802.11bg 
       resources: irq:17 memory:f69fc000-f69fffff 
  *-network 
       description: Ethernet interface 
       product: 88E8040 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 13 
       serial: 00:25:64:41:07:c4 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256) 




ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:25:64:41:07:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:c5:85:9d  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0 
          inet6 addr: fe80::222:5fff:fec5:859d/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:3999 
          TX packets:11 errors:6 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2909 (2.9 KB) 
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6656 (6.6 KB)  TX bytes:6656 (6.6 KB)

---

### Post by ravenkwill on 2010-04-23
Anyone out there?  I just need some suggestions on what to try next.

---

### Post by ravenkwill on 2010-04-24
Anyone have any suggestions for next steps?  I'd like to keep ubuntu, but not if I can't access the internet wirelessly!!

---

### Post by Iowan on 2010-04-24
Just an announcement to others reading - you don't need a raven avatar to contribute to this thread :)
Are there other machines connected to this router? I *presume* it's issuing addresses in the 10.42.43.X subnet, but wonder if you have a way to check.

---

