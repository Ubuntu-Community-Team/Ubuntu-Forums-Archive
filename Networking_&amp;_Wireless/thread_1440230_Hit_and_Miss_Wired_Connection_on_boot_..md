---
title: "Hit and Miss Wired Connection on boot ."
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by drifter2502 on 2010-03-27
I have this hit or miss wired connection problem with Ubi 9.10 and Mint 7 unless I boot into recovery mode first and then choose 'Resume Normal Boot' This always guarantees a connection in wicd or Networkmanager. Ubuntu 8.04 under another partition works fine.Because I prefer to use Mint 7 most of the time I find this problem very frustrating. Can anyone help as to what may be my problem please. When the problem occurs I get the following info in terminal...  

tc3-desktop ~ $ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12652 (12.6 KB)  TX bytes:12652 (12.6 KB)

tc3@tc3-desktop ~ $ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 02)
00:1e.0 ISA bridge: ALi Corporation M1575 South Bridge
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8)
00:1f.1 IDE interface: ALi Corporation ULi M5288 SATA (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
03:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
03:10.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
03:11.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
03:11.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
tc3@tc3-desktop ~ $ sudo ethtool eth0
[sudo] password for tc3: 
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available

(If you see a smiley, I don't know how it got there)

---

### Post by Iowan on 2010-03-27
The "8" (of "rev c8") followed by a ")" is interpreted as a "cool" smiley. You can stop that by either checking "Disable smilies in text" or enclosing the text in "code" tags (the # shortcut).
It appears that eth0 gets no IP address (**ifconfig -a** shows all interfaces) - probably since it disappears from the radar (so to speak). Another tool to check would be **sudo lshw -C network**.

---

### Post by drifter2502 on 2010-03-28
Thanks lowan, the problem has not arose today (yet) but I will post the unconnected terminal report using lshw-C network  as soon as I get the next fail. With that in mind I would ask you to re visit occasionally because it may be days rather than hours. Thanks. George.

---

### Post by drifter2502 on 2010-03-29
Here is the result after a failure to connect today......

tc3@tc3-desktop ~ $ lshw -C network 
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth7
       version: 01
       serial: 00:15:f2:c5:cf:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0

    serial: 56:c2:13:be:18:a1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I hope this helps.   

Result in terminal with connection.......
lshw -C network 

WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:15:f2:c5:cf:c5 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.41 latency=0 module=r8169 multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 4 
       logical name: pan0 
       serial: a6:1a:f8:ab:fb:3f 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

Seems to be a change in the logical name but that is all I can understand.  

George.

---

### Post by Iowan on 2010-03-29
Results may be slightly different using **sudo lshw -C network** - but the change in eth# is interesting. You could check */etc/udev/rules.d/70-persistent-net.rules* to see if it has 8 (including eth0) devices defined. That file is editable - but I'm curious why it would change from time to time...

---

### Post by drifter2502 on 2010-03-30
Thanks,I will do as you suggest,however again this will take time. I am out of the country to Friday 2nd April. It failed again this morning but of course I came to recovery to read your message and I am sure I won't get a failure on normal boot for at least a couple of sessions this morning. Many thanks to you. George.

---

### Post by drifter2502 on 2010-04-03
At last here are the results using sudo lshw-C network you so kindly suggested :-

Normal Boot.....network failure.

tc3@tc3-desktop ~ $ sudo lshw -C network 
[sudo] password for tc3: 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 9a:57:e5:42:68:88 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 



Connection via Recovery Menu...Normal boot.


@tc3-desktop ~ $ sudo lshw -C network 
[sudo] password for tc3: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:15:f2:c5:cf:c5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.41 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:01:4e:21:01:33
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

