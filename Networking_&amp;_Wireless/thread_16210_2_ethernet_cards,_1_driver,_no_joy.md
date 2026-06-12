---
title: "2 ethernet cards, 1 driver, no joy"
date: 2005-02-20
forum: Networking &amp; Wireless
---

### Post by PhilJess on 2005-02-20
I downloaded the Warty CD image and installed it on an old PII box that I run as a gateway machine. In it I have 2 almost identical PCI ethernet cards based on the Realtek 8029AS chipset. 
         ```
# lspci -vv
       [SNIP]
       0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
       	    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
		Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- SERR- 
       		Interrupt: pin A routed to IRQ 11
       		Region 0: I/O ports at 6400
       
       0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
       	    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
		Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- SERR- 
       		Interrupt: pin A routed to IRQ 10
       		Region 0: I/O ports at 6800
       [SNIP]
       
``` 
      Their setup seems OK
        ```
# ifconfig
      eth0	  Link encap:Ethernet  HWaddr 00:40:05:3C:A6:AC
      		  inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
      		  inet6 addr: fe80::240:5ff:fe3c:a6ac/64 Scope:Link
      		  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      		  RX packets:28 errors:0 dropped:0 overruns:0 frame:0
      		  TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
      		  collisions:0 txqueuelen:1000
      		  RX bytes:2443 (2.3 KiB)  TX bytes:2745 (2.6 KiB)
      		  Interrupt:11 Base address:0x6400
      
      eth1	  Link encap:Ethernet  HWaddr 00:00:E8:D6:8A:E4
      		  inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
      		  inet6 addr: fe80::200:e8ff:fed6:8ae4/64 Scope:Link
      		  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      		  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      		  TX packets:0 errors:11 dropped:0 overruns:0 carrier:22
      		  collisions:187 txqueuelen:1000
      		  RX bytes:0 (0.0 b)  TX bytes:738 (738.0 b)
      		  Interrupt:10 Base address:0x6800
      [SNIP]
      
``` 
      The driver is identifying them correctly at boot
       ```
# dmesg
     [SNIP]
     ne2k-pci.c:v1.03 9/22/2003 D. Becker/P. Gortmaker
       http://www.scyld.com/network/ne2k-pci.html
     PCI: Found IRQ 11 for device 0000:00:0b.0
     eth0: RealTek RTL-8029 found at 0x6400, IRQ 11, 00:40:05:3C:A6:AC.
     PCI: Found IRQ 10 for device 0000:00:0c.0
     eth1: RealTek RTL-8029 found at 0x6800, IRQ 10, 00:00:E8:D6:8A:E4.
     [SNIP]
     
``` 
      I can't find any interrupt conflicts
       ```
# cat /proc/interrupts
     		   CPU0
       0:	1652217		  XT-PIC  timer
       1:	   1285		  XT-PIC  i8042
       2:		  0		  XT-PIC  cascade
       7:		  0		  XT-PIC  parport0
       8:		  1		  XT-PIC  rtc
      10:		 16		  XT-PIC  eth1
      11:		353		  XT-PIC  eth0
      12:	  61857		  XT-PIC  i8042
      14:	  10574		  XT-PIC  ide0
      15:	  14878		  XT-PIC  ide1
     NMI:		  0
     LOC:	1652315
     ERR:		  0
     MIS:		  0
      
``` 
      And  I/O ports are unique
       ```
# cat /proc/ioports
     0000-001f : dma1
     0020-0021 : pic1
     0040-005f : timer
     0060-006f : keyboard
     0070-0077 : rtc
     0080-008f : dma page reg
     00a0-00a1 : pic2
     00c0-00df : dma2
     00f0-00ff : fpu
     0170-0177 : ide1
     01f0-01f7 : ide0
     02f8-02ff : serial
     0cf8-0cff : PCI conf1
      5800-583f : 0000:00:07.3
      5c00-5c1f : 0000:00:07.3
      6000-601f : 0000:00:07.2
      6400-641f : 0000:00:0b.0
        6400-641f : ne2k-pci
      6800-681f : 0000:00:0c.0
        6800-681f : ne2k-pci
      e000-efff : PCI Bus #01
      f000-f00f : 0000:00:07.1
        f000-f007 : ide0
        f008-f00f : ide1
      
``` 
However, they just will not play nicely together. Whenever both are active neither of them seems to work. All my internal network connections fail and applications like Mozilla and Synaptic are unable to retrieve data from the internet. I investigated a bit further with the ping command and found some very strange things. My ADSL modem is at 192.168.1.1 and it is physically connected to eth0
      ```
# ping -c 5 -I eth0 192.168.1.1
    PING 192.168.1.1 (192.168.1.1) from 192.168.1.100 eth0: 56(84) bytes of data.
    64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.808 ms
    64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.770 ms
    64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.731 ms
    64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.719 ms
    64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.727 ms
    
    --- 192.168.1.1 ping statistics ---
    5 packets transmitted, 5 received, 0% packet loss, time 4002ms
    rtt min/avg/max/mdev = 0.719/0.751/0.808/0.033 ms
     
```
This looks good, but I still can't access the internet. Even stranger, is the difference between the response to these two calls to ping. Note that eth1 does not have any connection to the ADSL modem.
     ```
# ping -c 5 -I eth1 192.168.1.1
   PING 192.168.1.1 (192.168.1.1) from 192.168.1.200 eth1: 56(84) bytes of data.
   From 192.168.1.200 icmp_seq=1 Destination Host Unreachable
   From 192.168.1.200 icmp_seq=2 Destination Host Unreachable
   From 192.168.1.200 icmp_seq=3 Destination Host Unreachable
   From 192.168.1.200 icmp_seq=4 Destination Host Unreachable
   From 192.168.1.200 icmp_seq=5 Destination Host Unreachable
   
``` 
    This is what I expected, but
     ```
# ping -c 5 -I 192.168.1.200 192.168.1.1
   PING 192.168.1.1 (192.168.1.1) from 192.168.1.200 : 56(84) bytes of data.
   64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.38 ms
   64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.723 ms
   64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.743 ms
   64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.752 ms
   64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.740 ms
   
```
   I've looked up the ethernet HOWTO at:
   [http://www.ibiblio.org/mdw/HOWTO/Ethernet-HOWTO.html]("http://www.ibiblio.org/mdw/HOWTO/Ethernet-HOWTO.html")
and thought at first that I needed to edit the /etc/modules.conf file. However, the comments at the top of that file tell me not to edit it directly, but instead to look up the man pages for update-modules. They tell me that update-modules is an obsolete command. And, I'm still none the wiser about solving my problem.
   
 So, my question is this: What has gone wrong with my ethernet cards, how do I fix it, and where is this information documented?
   
Sorry for the length of this post, and thank you for reading it all if you've got this far, but I wanted to make it clear that I've attempted to solve the problem myself.[size=-1][color=#008000]
   [/color][/size]

---

### Post by alastair on 2005-02-20
It's probably worth looking at the routes you have e.g. what it the default route etc. I've had problems with routing when I have 2 active interfaces on the same network (and 2 default routes for instance) i.e. route -n.

Some of this depends on what "can't access the internet" means though - name resolution? traceroute?

Good luck.

---

### Post by PhilJess on 2005-02-21
The hardware looked good because it was good. It was a routing problem. Thanks alastair.

---

