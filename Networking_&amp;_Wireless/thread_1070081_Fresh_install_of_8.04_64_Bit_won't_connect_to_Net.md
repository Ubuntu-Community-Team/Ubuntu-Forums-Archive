---
title: "Fresh install of 8.04 64 Bit won't connect to Net"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by dishbert on 2009-02-14
I just upgraded to an Asus M3N78-EM mother board with an AMD X2 6000+ CPU.  I installed the 64 bit version of my favorite OS (Ubuntu 8.04) on some unused hard drive space, and kept my 32 bit version.

The grub boot load screen is a little crowded, the new install boots up, but won't connect to anything.  XP connects fine so the hardware is OK.  The install disk wouldn't connect in Live mode either.

ifconfig gives this:

chris@Ubuntu8:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:a4:c4:30  
          inet6 addr: fe80::223:54ff:fea4:c430/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5733 (5.5 KB)
          Interrupt:251 Base address:0x8000 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:54:a4:c4:30  
          inet addr:169.254.6.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:251 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29025 (28.3 KB)  TX bytes:29025 (28.3 KB)

---

### Post by dishbert on 2009-02-14
I tried a couple more things I found elsewhere:

chris@Ubuntu8:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:23:54:a4:c4:30
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.2 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes


I checked the back and there is an steady orange light beside the network cable, and the Asus guide says this means there is a 100 mbps link.

I tried to set up the connection using a terminal command I found with no luck:

chris@Ubuntu8:~$ sudo ifconfig eth0 add 192.168.1.2 netmask 255.255.255.0 up
SIOCSIFNETMASK: Cannot assign requested address

I also tried configuring it using the Network Settings GUI for a Wired Connection using the same data I get from running ipconfig at a DOS prompt on the XP side, but still no joy.

When I ping 192.168.1.2 there is a response.  When I ping 192.168.1.1 there is no response.

---

### Post by superprash2003 on 2009-02-15
in network manager set eth0 back to dhcp or roaming mode.. then go to the terminal and type **sudo dhclient eth0** and then post output of **ifconfig**

---

### Post by dishbert on 2009-02-15
Thanks for giving me hope superprash2003.

chris@Ubuntu8:~$ sudo dhclient eth0
[sudo] password for chris: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:23:54:a4:c4:30
Sending on   LPF/eth0/00:23:54:a4:c4:30
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

chris@Ubuntu8:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:a4:c4:30  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7787 (7.6 KB)
          Interrupt:251 Base address:0x6000 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:54:a4:c4:30  
          inet addr:169.254.6.184  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:251 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15772 (15.4 KB)  TX bytes:15772 (15.4 KB)

I noticed ping 192.168.1.2 had no response now.  

I noticed a message on the top panel that briefly showed "Requesting an address from wired network" when I booted. 

I also tried a USB ethernet adapter I had lying around last night.  Linux found it, but still no connection.

---

### Post by superprash2003 on 2009-02-16
well it doesnt seem to be getting an ip address..try disabling ipv6 and then try the dhclient command again .. [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by dishbert on 2009-02-17
Sorry for the late reply, there was a power spike that took out my wireless internet connection.  The ISP guy just came this morning to replace the radio.

I tried disabling ipv6 using the method at the link you gave, but no change.

I did succeed in getting my previous 32 bit version of 8.04 working, and it connects just fine, (although Firestarter says that eth0 is not ready).  I'll install 8.10 64 bit and see if it works.

Thanks for your help.

---

### Post by dishbert on 2009-02-18
Well I can't get a 8.10 version installed because I can't seem to burn a disc that doesn't report "Errors found in 10 files".  (I've got a thread going on this issue in the installation forum.)

Since I can connect using the 32 bit version of 8.04, but not the newly installed 64 bit version of the same OS, are there some files or settings I could copy across from the working version?

---

### Post by dishbert on 2009-02-20
I installed 8.10 64 bit and it connects fine.

I have no idea what was wrong with the 8.04 version, but I'm happy to at least have one 64 bit OS to play with on my new motherboard.

Thanks for your responses superprash2003.

---

