---
title: "ubuntu 8.10 ethernet problems"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by saisai on 2009-05-27
Hi I have a dell inspiron 1501, it came with windows XP but I completely reformatted it with Ubuntu 8.10 OS. But after I put in the ethernet cable, I dont get internet. Is it suppose to be plug and play? Or am I suppose to install a network driver? But I read in a forum that ethernet cable should work out of the box with 8.10. 

Another thing that's confusing is when i first installed the OS, for a brief few seconds the network manager was able to automatically connect to "auto eth0" for like 2 seconds, and then it never connected again. I did manage to go to a webpage in those seconds, so I dont see why it would be a driver problem. the cable works fine. How would i go about fixing this? 
thanks

---

### Post by saisai on 2009-05-27
Do you think I should just install 9.4 and hope for plug and play?

---

### Post by Iowan on 2009-05-27
*Should* be plug/play... unfortunately, doesn't always work that way.  Post results of **ifconfig -a**, **lshw -C network**, and (since it sounds like you're connecting via DHCP) results of **dhclient eth0**.

Personally, I like Jaunty so far. Whether you choose to troubleshoot Intrepid or install Jaunty (and perhaps begin troubleshooting from there) is kinda up to you.

---

### Post by saisai on 2009-05-28
[INDENT][SIZE="1"]sai@sai:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:c5:d0:55:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18592 (18.5 KB)  TX bytes:18592 (18.5 KB)

pan0      Link encap:Ethernet  HWaddr 66:4c:e2:9b:96:8a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:92:23:b5:51  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-92-23-B5-51-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


sai@sai:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:d0:55:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:23:b5:51
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 66:4c:e2:9b:96:8a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

sai@sai:~$ dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
wmaster0: unknown hardware address type 801
Open a socket for LPF: Operation not permitted
[/SIZE][/INDENT]

I dont know what jaunty or intrepid is...

---

### Post by superprash2003 on 2009-05-28
add a sudo to your dhclient command

---

### Post by saisai on 2009-05-28
sai@sai:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:15:c5:d0:55:bb
Sending on   LPF/eth0/00:15:c5:d0:55:bb
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
sai@sai:~$

---

### Post by saisai on 2009-05-28
someone in another forum said I should check my drivers and see if it is proprietary. So i did: theres only 2 drivers, 1 is activated. its called "wl".. theres no further description but it's license is proprietary.. does it mean anything? the other driver that is deactivated is ATI/AMD proprietary FGLRX graphics driver. I used to run ubuntu and internet worked,, but sometime last week internet just stopped for both Ubuntu and XP partitions.. so I decided to reformat everything to just ubuntu.. but now I cant remember what I did earlier to get internet working, I thought it would be plug and play..

---

### Post by Iowan on 2009-05-28
> **saisai said:**
> 
I dont know what jaunty or intrepid is...Sorry... Intrepid Ibex is Ubuntu version 8.10, Jaunty Jackalope is version 9.04 
(FYI, Karmic Koala will be 9.10)
**lshw -C network** suggests eth0 is associated with a driver -
 whether it's the right one...

I suspect it's pretty empty, but what's in your */etc/network/interfaces*?

---

### Post by saisai on 2009-05-28
Hi I installed **Jaunty 9.04**. now under **wired network** it says **disconnected**.
in the /etc/network/interfaces there are two lines
auto lo
iface lo inet loopback

---

### Post by saisai on 2009-05-28
I also tried this articles advice, I think you helped it 
[http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)
it didnt work.
I have added **lshw -C network** output again: I noticed for logical name:eth2.. would it mean anything? Right now my **wired network** just says **disconnected** but I can view the wireless networks although I cant connect to it..

[SIZE="1"]sai@sai:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       **logical name: eth2**
       version: 01
       serial: 00:1a:92:23:b5:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:d0:55:bb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:d2:19:7f:d2:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/SIZE]

thanks

---

