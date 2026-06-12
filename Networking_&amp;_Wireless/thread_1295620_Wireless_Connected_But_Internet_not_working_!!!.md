---
title: "Wireless Connected But Internet not working !!!"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by sgx100 on 2009-10-19
[FONT=Tahoma]**[SIZE=3]Hi All,[/SIZE]**


[/FONT]       [FONT=Tahoma][SIZE=3]I just installed Ubuntu 9.04 on my dell inspiron 1420.[/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]It dual boots with windows 7 RTM installed first .[/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]After the installation the broadcom driver passed the restricted driver test and after that the wireless networks were detected and the laptop connected to the wireless network.[/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]But thats all, even though the laptop is connected to the wireless netowork; I cant surf the internet on it.[/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]This is really annoying me .... Please somebody help me out.[/SIZE]
[/FONT][FONT=Tahoma][SIZE=3]Also I can ping the default gateway[/SIZE][/FONT][FONT=Tahoma]

[/FONT]      [FONT=Tahoma][SIZE=3]Im posting certain details about the laptop  as asked in the forum[/SIZE]

[/FONT]  [FONT=Tahoma][SIZE=3]sgx100@sgx100-laptop:~$ [/SIZE]**[SIZE=3]lspci[/SIZE]**
[/FONT]   [FONT=Tahoma][SIZE=3]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02) [/SIZE]
[/FONT]     [FONT=Tahoma][SIZE=3]0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01) [/SIZE]

[/FONT]      [FONT=Tahoma][SIZE=3]sgx100@sgx100-laptop:~$** lshw -class network **[/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]WARNING: you should run this program as super-user. [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]  *-network               [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       description: Wireless interface [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       product: BCM4312 802.11a/b/g [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       vendor: Broadcom Corporation [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       physical id: 0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       bus info: pci@0000:0c:00.0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       logical name: eth1 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       version: 01 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       serial: 00:1f:e1:c4:ce:7d [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       width: 32 bits [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       clock: 33MHz [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       capabilities: bus_master cap_list ethernet physical wireless [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=10.118.1.56 latency=0 module=wl multicast=yes wireless=IEEE 802.11 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]  *-network [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       description: Ethernet interface [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       product: NetLink BCM5906M Fast Ethernet PCI Express [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       vendor: Broadcom Corporation [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       physical id: 0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       bus info: pci@0000:09:00.0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       logical name: eth0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       version: 02 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       serial: 00:21:70:fe:b1:04 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       width: 64 bits [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       clock: 33MHz [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       capabilities: bus_master cap_list ethernet physical [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]  *-network DISABLED [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       description: Ethernet interface [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       physical id: 2 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       logical name: pan0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       serial: 02:a0:6d:93:2d:ae [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]       capabilities: ethernet physical [/SIZE]
[/FONT]     [FONT=Tahoma][SIZE=3]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes [/SIZE]

[/FONT]      [FONT=Tahoma][SIZE=3]sgx100@sgx100-laptop:~$ **ifconfig **[/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]eth0      Link encap:Ethernet  HWaddr 00:21:70:fe:b1:04  [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          UP BROADCAST MULTICAST  MTU:1500  Metric:1 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          collisions:0 txqueuelen:1000 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          Interrupt:17 [/SIZE]

[/FONT]      [FONT=Tahoma][SIZE=3]eth1      Link encap:Ethernet  HWaddr 00:1f:e1:c4:ce:7d  [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          inet addr:10.118.1.56  Bcast:10.255.255.255  Mask:255.0.0.0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          inet6 addr: fe80::21f:e1ff:fec4:ce7d/64 Scope:Link [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          RX packets:6761 errors:0 dropped:0 overruns:0 frame:813 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          TX packets:93 errors:6 dropped:0 overruns:0 carrier:0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          collisions:0 txqueuelen:1000 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          RX bytes:507914 (507.9 KB)  TX bytes:9573 (9.5 KB) [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          Interrupt:17 Base address:0xc000 [/SIZE]

[/FONT]      [FONT=Tahoma][SIZE=3]lo        Link encap:Local Loopback  [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          inet addr:127.0.0.1  Mask:255.0.0.0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          inet6 addr: ::1/128 Scope:Host [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          UP LOOPBACK RUNNING  MTU:16436  Metric:1 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          collisions:0 txqueuelen:0 [/SIZE]
[/FONT]     [FONT=Tahoma][SIZE=3]          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) [/SIZE]

[/FONT]      [FONT=Tahoma][SIZE=3]sgx100@sgx100-laptop:~$ **iwconfig **[/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]lo        no wireless extensions. [/SIZE]

[/FONT]      [FONT=Tahoma][SIZE=3]eth0      no wireless extensions. [/SIZE]

[/FONT]      [FONT=Tahoma][SIZE=3]eth1      IEEE 802.11  Nickname:"" [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          Access Point: Not-Associated   [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          Link Quality:5  Signal level:208  Noise level:161 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 [/SIZE]

[/FONT]        [FONT=Tahoma][SIZE=3]pan0      no wireless extensions[/SIZE]

[/FONT]      [FONT=Tahoma][SIZE=3]sgx100@sgx100-laptop:~$ **route -n **[/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]Kernel IP routing table [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1 [/SIZE]
[/FONT]   [FONT=Tahoma][SIZE=3]10.0.0.0        0.0.0.0         255.0.0.0       U     2      0        0 eth1 [/SIZE]
[/FONT]     [FONT=Tahoma][SIZE=3]0.0.0.0         10.102.1.1      0.0.0.0         UG    0      0        0 eth1 [/SIZE]


[/FONT]         [FONT=Tahoma][SIZE=3] Please somebody help me out.[/SIZE]
[/FONT] [FONT=Tahoma][SIZE=3]Thanks in advance[/SIZE]


[/FONT]   [FONT=Tahoma][SIZE=3]SGX100 :)
[/SIZE][/FONT]

---

### Post by Iowan on 2009-10-19
I presume the laptop can **ping** the router - how about the internet? Can it ping by IP address?

---

### Post by sgx100 on 2009-10-20
> **Iowan said:**
> I presume the laptop can **ping** the router - how about the internet? Can it ping by IP address?

Yes mate pretty much
The system can ping the router but not any internet address

Here are the terminal results :

   sgx100@sgx100-laptop:~$ ping -c 5 10.102.1.1 (my gateway address)

  
  PING 10.102.1.1 (10.102.1.1) 56(84) bytes of data.
  
  64 bytes from 10.102.1.1: icmp_seq=1 ttl=255 time=9.86 ms
  
  64 bytes from 10.102.1.1: icmp_seq=2 ttl=255 time=2.45 ms
  
  64 bytes from 10.102.1.1: icmp_seq=3 ttl=255 time=2.65 ms
  
  64 bytes from 10.102.1.1: icmp_seq=4 ttl=255 time=2.85 ms
  
  64 bytes from 10.102.1.1: icmp_seq=5 ttl=255 time=2.77 ms
  
   
   
  --- 10.102.1.1 ping statistics ---
  
  5 packets transmitted, 5 received, 0% packet loss, time 4006ms
  
  rtt min/avg/max/mdev = 2.450/4.122/9.869/2.877 ms
  
  sgx100@sgx100-laptop:~$ ping -c 5 [www.google.com](www.google.com)
  
  ping: unknown host [www.google.com](www.google.com)
  
  sgx100@sgx100-laptop:~$ 
  
  sgx100@sgx100-laptop:~$ ping -c 5 [www.opendns.com](www.opendns.com)
  
  ping: unknown host [www.opendns.com](www.opendns.com)
  
  sgx100@sgx100-laptop:~$ 





What could be the problem buddy


Please geeks....come forward and help me out...Or this is just the melancholic end of my remotely impossible Ubuntu Dreams :(


Thanks
SGX100

---

### Post by Iowan on 2009-10-20
Can you ping internet by address (74.125.45.100)?
What's in */etc/resolv.conf*?

---

