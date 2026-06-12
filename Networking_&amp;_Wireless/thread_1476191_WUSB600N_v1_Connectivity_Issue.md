---
title: "WUSB600N v1 Connectivity Issue"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by therjnel on 2010-05-07
I have a wrt160n v3 and a wusb600n v1.  I have installed ubuntu 10 with dual boot to Windows Vista 32bit.  Windows connects just fine, but I am unable to get connected when I boot to ubuntu.  I tried the included troubleshooting steps and a few other commands I've learned, but this is all I get.
 
 
[EMAIL="nelson-parents@nelson-parents-desktop:~$"]nelson-parents@nelson-parents-desktop:~$[/EMAIL] sudo lshw -C network
[sudo] password for nelson-parents: 
  
*-network               
  
description: Ethernet interface
       
product: MCP73 Ethernet
       
vendor: nVidia Corporation
       
physical id: f
       
bus info: [EMAIL="pci@0000:00:0f.0"]pci@0000:00:0f.0[/EMAIL]
       
logical name: eth0
       
version: a2
       
serial: 00:22:68:47:6b:60
       
capacity: 100MB/s
       
width: 32 bits
       
clock: 66MHz
       
capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
resources: irq:28 memory:efffd000-efffdfff ioport:f600(size=8) memory:efffc000-efffc0ff memory:efffb000-efffb00f
  
*-network
       
description: Wireless interface
       
physical id: 1
       
logical name: wlan0
       
serial: 00:1e:e5:da:4c:01
       
capabilities: ethernet physical wireless
       
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abgn

[EMAIL="nelson-parents@nelson-parents-desktop:~$"]nelson-parents@nelson-parents-desktop:~$[/EMAIL] dmesg | grep wlan
[   10.865364] ADDRCONF(NETDEV_UP): wlan0: link is not ready
 

[EMAIL="nelson-parents@nelson-parents-desktop:~$"]nelson-parents@nelson-parents-desktop:~$[/EMAIL] ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:22:68:47:6b:60  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:0 (0.0 B)  
TX bytes:0 (0.0 B)
          
Interrupt:28 
Base address:0x2000 
 
lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  
Metric:1
          
RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:15144 (15.1 KB)  
TX bytes:15144 (15.1 KB)
wlan0     
Link encap:Ethernet  HWaddr 00:1e:e5:da:4c:01  
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:0 (0.0 B)  
TX bytes:0 (0.0 B)
 

Additionally, I am using mac addres filtering and the SSID is not being broadcast with no other security settings.  Thanks for any help or suggestions!

---

