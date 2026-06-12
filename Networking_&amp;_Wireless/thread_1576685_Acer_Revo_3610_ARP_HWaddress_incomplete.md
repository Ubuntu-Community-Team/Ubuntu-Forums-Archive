---
title: "Acer Revo 3610 ARP HWaddress incomplete"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by mpk1001 on 2010-09-17
I have two new Acer Revo 3610s.

One has Ubuntu 10.04 installed the other Mybuntu 10.04. Both 32bit and 64bit versions have been tried. I've also tried live versions of 9.10 server and desktop.

Initially both will connect to wired ethernet, obtain an IP address from the DHCP server and have internet access.

After a few minutes both then lose any network access.

The arp table has entries which have a HWaddress shown as (incomplete).

tcpdump shows that neither machine responds to a "who has xxxx" request once network connectivity is lost.

Does anyone have any ideas before I return both machines...

Thanks.

---

### Post by Joe of loath on 2010-09-17
What's the output of ifconfig?

---

### Post by mpk1001 on 2010-09-18
Output from ifconfig:

test@test-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:83:ec:cf  
          inet addr:192.168.200.120  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::92fb:a6ff:fe83:eccf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2146709 (2.1 MB)  TX bytes:267638 (267.6 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3379 (3.3 KB)  TX bytes:3379 (3.3 KB)

test@test-desktop:~$ 


Other things which might be useful!

test@test-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
05:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
test@test-desktop:~$ 


test@test-desktop:~$ dmesg | grep eth
[    1.359815] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.361429] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    1.361448] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.434706] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 90:fb:a6:83:ec:cf
[    1.434716] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[   27.743788] eth0: no IPv6 routers present
test@test-desktop:~$

---

### Post by mpk1001 on 2010-09-18
This is ifconfig after a loss of connection:

eth0      Link encap:Ethernet  HWaddr 90:fb:a6:83:ec:cf  
          inet addr:192.168.200.120  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::92fb:a6ff:fe83:eccf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4315 errors:1 dropped:0 overruns:0 frame:1
          TX packets:3299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4679635 (4.6 MB)  TX bytes:482042 (482.0 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9109 (9.1 KB)  TX bytes:9109 (9.1 KB)

test@test-desktop:~$

This is the arp table after losing the connection:

Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.200.254                  (incomplete)                              eth0
192.168.200.220                  (incomplete)                              eth0
test@test-desktop:~$


Before losing the connection the arp table looked like this:

test@test-desktop:~$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.200.254          ether   00:18:39:2b:fe:16   C                     eth0
192.168.200.220          ether   08:00:27:6d:41:09   C                     eth0

---

