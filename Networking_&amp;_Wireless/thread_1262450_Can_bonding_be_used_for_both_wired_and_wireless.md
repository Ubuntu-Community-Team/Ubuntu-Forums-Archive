---
title: "Can bonding be used for both wired and wireless"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by seanacais on 2009-09-09
I am trying to set up failover bonding on 8.04 Desktop on a Dell Latitude 6500 containing one ethernet and one wireless port.  I am using VMWare Workstation and would like to set up the VMWare bridge to bond0 since I am sometimes in a place where I can only work wired and other times only wireless.  My thought is that putting the bridge on bond0 with wired as the primary the failover will carry traffic thru to the wireless when I'm not plugged in.

Each of these interfaces works fine individually, and I can create the bond0 interface and enslave eth0 to it.  bond0 passes traffic with no issues.  When I attempt to enslave eth1 I get the following message:

# ifenslave --verbose bond0 eth1
ifenslave.c:v1.1.0 (December 1, 2003)
o Donald Becker (becker@cesdis.gsfc.nasa.gov).
o Detach support added on 2000/10/02 by Willy Tarreau (willy at meta-x.org).
o 2.4 kernel support added on 2001/02/16 by Chad N. Tindel
  (ctindel at ieee dot org).
ABI ver is 2
current hardware address of master 'bond0' is 00:25:64:4e:37:35, type 1
Interface 'eth1': flags set to 1042.
Interface 'eth1': address cleared
Master 'bond0': Error: SIOCBONDENSLAVE failed: Too many open files in system
Master 'bond0': hardware address set to 00:25:64:4e:37:35.
Slave 'eth1': MTU set to 1500.
Master 'bond0', Slave 'eth1': Error: Enslave failed

I cannot find any reference to this message in either the ubuntu forums or in google.
The message is clear, but I don't see how I could have reached an open file limit. (it happens too early in the boot sequence and it is way to reproducible.)

I know that  the problem is not the ability to change the MAC address on the wireless interface because the ifconfig output shows it as changed

# ifconfig -a 
bond0     Link encap:Ethernet  HWaddr 00:25:64:4e:37:35  
          inet addr:192.168.1.85  Bcast:192.168.1.0  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe4e:3735/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:3464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3608704 (3.4 MB)  TX bytes:343742 (335.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:25:64:4e:37:35  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:3464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3608704 (3.4 MB)  TX bytes:343742 (335.6 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:25:64:4e:37:35  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:176
          TX packets:6 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11069 (10.8 KB)  TX bytes:508 (508.0 B)
          Interrupt:17 Base address:0xc000 

Any thoughts on either the general concept or a solution is greatly appreciated

P.S.
Here is the output of lshw as it pertains to the wireless interface
*-network
                description: Wireless interface
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:25:64:4e:37:35
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn


thanks again!

Kevin

---

