---
title: "lost network"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2009-10-21
Can anyone help?

Suddenly I have no LAN or internet connection.

From the command ifconfig I only get info regarding lo.  Nothing refering to Auto eth0 (my regular connection)

Bill Lancaster

Ubuntu 9.04
Gnome 2.26.1

---

### Post by Iowan on 2009-10-21
Check **ifconfig -a** That should show all available interfaces - even inactive ones. If eth0 still doesn't show up, try **lshw -C network** to see if the interface is listed with alias and driver.

---

### Post by bill-lancaster on 2009-10-21
Since I first posted on this issue I checked a few more things.
ifconfig only showed stuff for lo.
In particular I looked in /etc/network/interfaces and found only a reference to lo and nothing for eth0.

I edited the file and added "Auto eth0 and further info.

So, now ifconfig shows a whole lot of stuff including a number of packets sent and received without error.

What now?

Bill

---

### Post by bill-lancaster on 2009-10-21
OK Had trouble with lshw command (my spellin/reading!)

Get a whole lot of data in reposnse including "network disabled"

Bill

---

### Post by bill-lancaster on 2009-10-21
Have used a memory stick to copy respose to ifconfig, here it is:

bill@bill-desktop:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:94:16:56   
          inet addr:192.168.2.0  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::21a:a0ff:fe94:1656/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:735 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:100  
          RX bytes:64269 (64.2 KB)  TX bytes:5575 (5.5 KB) 
          Memory:fdfc0000-fdfe0000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:161953 (161.9 KB)  TX bytes:161953 (161.9 KB) 

and the response to lshw is:

*-network                
       description: Ethernet interface 
       product: 82562V-2 10/100 Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 02 
       serial: 00:1a:a0:94:16:56 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.1-2 ip=192.168.2.0 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 02:e3:24:6a:7e:67 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

Hope this helps

Bill

---

### Post by Iowan on 2009-10-21
> **bill-lancaster said:**
> I edited the file and added "Auto eth0 and further info.  If you use Network Manager to set up your interface, */etc/network/interfaces* contains only the two lines you mentioned. Interfaces defined in */etc/network/interfaces* effectively bypass Network Manager. Sometimes that's necessary to get things to work.  Did you set up dynamic or static address?  If you set up a static address, you may need to manually enter your DNS servers into */etc/resolv.conf*. If you have a DHCP server on your network, you will need to avoid the address range it uses.

---

