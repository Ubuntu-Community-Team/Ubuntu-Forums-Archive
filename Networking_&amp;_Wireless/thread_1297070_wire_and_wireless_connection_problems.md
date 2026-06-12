---
title: "wire and wireless connection problems"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by yliu on 2009-10-21
Hello all,

I am using Ubuntu 9.04 and the desktop is Dell Optiplex 960. I lost my Internet connection all of a sudden. I use the wire connection and never use the wireless after I installed it about one month ago. Now, two ethernet card and wireless all don't work. The following information is what I get when run ifconfig. 

eth0      Link encap:Ethernet  HWaddr 00:10:18:4e:d8:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:24:e8:3a:e2:80  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfe0000-fe000000 

eth0:avahi Link encap:Ethernet  HWaddr 00:10:18:4e:d8:32  
          inet addr:169.254.5.133  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

eth1:avahi Link encap:Ethernet  HWaddr 00:24:e8:3a:e2:80  
          inet addr:169.254.8.171  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Memory:fdfe0000-fe000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178644 (178.6 KB)  TX bytes:178644 (178.6 KB)

pan0      Link encap:Ethernet  HWaddr 82:42:2d:63:f7:cb  
          inet6 addr: fe80::8042:2dff:fe63:f7cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

Do you know how to make wire or wireless work? I have very short experience with Ubuntu. Please help. Thank you very much!

-Ying

---

### Post by yliu on 2009-10-21
Here are the devices information by command 'lspci -v':

00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
    Subsystem: Dell Device 0276
    Flags: bus master, fast devsel, latency 0, IRQ 2294
    Memory at fdfe0000 (32-bit, non-prefetchable) [size=128K]
    Memory at fdfd9000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ecc0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 21)
    Subsystem: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express
    Flags: bus master, fast devsel, latency 0, IRQ 2293
    Memory at f9ef0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3


Thanks,
-Ying

---

### Post by yliu on 2009-10-21
I kind of feel this problem is caused after I update the system. By 'uname -a', I got the following info:

Linux XXXXX 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

by 'lshw -C network', I got the following info:

 *-network
       description: Ethernet interface
       product: 82567LM-3 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 02
       serial: 00:24:e8:3a:e2:80
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.5-3 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5721 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 21
       serial: 00:10:18:4e:d8:32
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5721-v3.48a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:42:2d:63:f7:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I have no idea how to solve the problem. Do you think reinstall the driver will help? How Can I reinstall the Ethernet driver? 

Thank you!
-Ying

---

### Post by hoboy on 2009-10-21
I have the same problem.

---

### Post by jward3010 on 2009-10-21
Ok, you're adapters are picking up APIPA addresses, as if there's no DHCP server around to give out addresses. Your router usually acts as a DHCP server, has anyone messed with, changed configuration? First thing, try a restart of your router.

---

### Post by yliu on 2009-10-21
Thanks for your reply.

My desktop is connected to a socket on the wall. It's connected to the University network. I couldn't restart the router. 

Thanks,
Ying

---

### Post by Iowan on 2009-10-21
I doubt [this]("http://ubuntuforums.org/showthread.php?t=1156441") will help, but worth a check.

---

### Post by yliu on 2009-10-21
Thanks Iowan. But It doesn't solve my problem. 

First of all, my two Ethernet cards don't blink at all. How can I know it is not a hardware problem? I just use this computer for less than two months and I just use one Ethernet card. 

I comment the rfc3442 and its request references. Reboot but doesn't help. 

I run 'iwconfig', got:

l0 no wireless extensions.
eth0 no wireless extensions.
eth0 no wireless extensions.
pan0 no wireless extensions. 

run 'dhclient eth0' and 'dhclient eth1', no dhcpoffers received. 

From my previous post lspci information, I also don't find a wireless brand name. This computer should have a wireless card. (not 100% sure about this. ) 

Thank you !

-Ying

---

### Post by yliu on 2009-10-22
I am still working on this. Still no connection. This is really not fun!

$cat /etc/network/interfaces
auto lo
iface lo inet looopback

---

### Post by yliu on 2009-10-22
If there is no blinks of the Ethernet card after I reboot the computer, can I say this is a hardware problem? 

But the 'ifconfig -a' command can show me the eth0 and eth1 information. At the right upper conner, when I click the Internet icon, it has the MAC address: 00:24:E8:3A:E2:80, and MTU is automatic. Under IPv4 Settings, the method uses 'Automatic (DHCP)', can the DHCP Client ID is empty.  

Thanks,
-Ying

---

### Post by yliu on 2009-10-22
After changed the Internet socket on the wall, the Ethernet is blinking now. But still no wire  connection. At least, the Ethernet card is not dead. I also uncomment the dhclient.conf file which I commented on option rfc3442 and its request reference. But, still no connection. 

Thanks,
-Ying

---

### Post by pricetech on 2009-10-22
Did you try replacing your network cable ??

---

### Post by jward3010 on 2009-10-22
Possibly even a faulty cable if you ain't getting any lights - cheapest route to try next, replacement cable. Network ports usually have two lights - one green to say thats it's connected to a powered device and another orange usually activity light. If you get a green, your cable is working and your machine is basically plugged into something powered on it's other end (a switch most likely), a blinky orange would suggest data is travelling down the cable. 

What do you have?

---

### Post by jward3010 on 2009-10-22
> **pricetech said:**
> Did you try replacing your network cable ??
Sorry pricetech, somehow I ended up on the first page and your post was not in site.

---

### Post by pricetech on 2009-10-22
No problem.  OP added something while I was reading.  Seems he had the jack replaced and now has physical connectivity.

To the OP:

Run ifconfig again and post your output.

---

### Post by yliu on 2009-10-22
I am back connected to the Internet :-)

-Ying

---

### Post by yliu on 2009-10-22
Thank you guys!

My computer was compromised and I was shut down by the network security.

Cheers,
-Ying

---

### Post by jward3010 on 2009-10-23
Interesting, can you give details of the compromise? It's not like Ubuntu to get compromised.

---

