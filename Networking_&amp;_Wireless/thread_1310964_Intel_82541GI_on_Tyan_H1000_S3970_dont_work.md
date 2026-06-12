---
title: "Intel 82541GI on Tyan H1000 S3970 dont work"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by zneider on 2009-11-02
hi.

i have a Tyan H1000 S3970 moterboard with 2 onboard NIC's Intel 82541GI  - running ubuntu 9.10.
2 problems

1.) eth0 will not work...
2.) ubuntu loads old driver after reboot...

eth1 is working correctly. i can set static ip and and get an ip by dhcp. i can ping other machines. 
but eth0 is does nothing on any command like "dhclient eth0 or ping xxx"
i can set the ip by hand but it doesn't change anything

the interface is up
> $ifconfig
eth0   Link encap:Ethernet  HWaddr 00:e0:81:4c:9a:28
          inet addr:xxx.xx.141.114  Bcast:xxx.83.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1   Link encap:Ethernet  HWaddr 00:e0:81:4c:9a:29
          inet addr:xxx.xx.141.113  Bcast:xxx.83.141.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe4c:9a29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:153265 (153.2 KB)  TX bytes:12735 (12.7 KB)
i did a bios update and installed the latest intel network driver 8.0.16
did " sudo modprobe -r e1000" and sudo modprobe e1000" to load the new driver
> "ethtool -i eth0" says that the new driver is loaded.

>  lshw 
*-network:0                                                                                                                                                                         
             description: Ethernet interface                                                                                                                                                
             product: 82541GI Gigabit Ethernet Controller                                                                                                                                   
             vendor: Intel Corporation                                                                                                                                                      
             physical id: 4                                                                                                                                                                 
             bus info: pci@0000:00:04.0                                                                                                                                                     
             logical name: eth0                                                                                                                                                             
             version: 05                                                                                                                                                                    
             serial: 00:e0:81:4c:9a:28                                                                                                                                                      
             width: 32 bits                                                                                                                                                                 
             clock: 66MHz                                                                                                                                                                   
             capabilities: bus_master cap_list rom ethernet physical                                                                                                                        
             configuration: broadcast=yes driver=e1000 driverversion=8.0.16-NAPI firmware=N/A ip=xxx.xx.141.114 latency=64 mingnt=255 multicast=yes                                         
             resources: irq:24 memory:ff680000-ff69ffff memory:ff660000-ff67ffff ioport:dc00(size=64) memory:ff640000-ff65ffff(prefetchable)                                                
        *-network:1                                                                                                                                                                         
             description: Ethernet interface                                                                                                                                                
             product: 82541GI Gigabit Ethernet Controller                                                                                                                                   
             vendor: Intel Corporation                                                                                                                                                      
             physical id: 5                                                                                                                                                                 
             bus info: pci@0000:00:05.0                                                                                                                                                     
             logical name: eth1                                                                                                                                                             
             version: 05                                                                                                                                                                    
             serial: 00:e0:81:4c:9a:29                                                                                                                                                      
             width: 32 bits                                                                                                                                                                 
             clock: 66MHz                                                                                                                                                                   
             capabilities: bus_master cap_list rom ethernet physical                                                                                                                        
             configuration: broadcast=yes driver=e1000 driverversion=8.0.16-NAPI firmware=N/A ip=xxx.xx.141.113 latency=64 mingnt=255 multicast=yes                                         
             resources: irq:25 memory:ff620000-ff63ffff memory:ff600000-ff61ffff ioport:d880(size=64) memory:ff5e0000-ff5fffff(prefetchable)            pings to eth0 and eth1 work !!! 

but when try to ping an other host -it fails 
ping xxx.xx.141.111
PING xxx.xx.141.111 (xxx.xx.141.111) 56(84) bytes of data.
From xxx.xx.141.114 icmp_seq=1 Destination Host Unreachable
From xxx.xx.141.114 icmp_seq=2 Destination Host Unreachable

in my opinion everything is looking fine ?????? i cant understand why eth0 isnt working.

problem 2.) after a restart the old driver 7.x.xx is loaded again. :confused:

someone got an idea ? 
thx

---

### Post by zneider on 2009-11-04
? :confused:

---

### Post by ajt on 2010-07-28
> **zneider said:**
> ? :confused:

Hi,

I'm using the same motherboard with Ubuntu 6.06 LTS, 8.04 LTS and 10.04 LTS without any problems. Try removing *all* entries from:

/etc/udev/rules.d/70-persistent-net.rules

HTH,

  Tony.

---

