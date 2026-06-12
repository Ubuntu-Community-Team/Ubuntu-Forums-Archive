---
title: "cannot connect with Karmic (RTL8101E/8192E)"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by Acimer on 2010-01-18
Hello!

I'm relatively new to Ubuntu, I've been using Intrepid and recently I've installed Karmic (on a new machine) and I cannot get wireless or wired network to work!
Laptop is Toshiba Satellite L515-s4925 and Karmic x64
the drivers I would need (I guess) are for:

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

can someone point me to the right driver(s) and info how to install them?

Thank you very much!

---

### Post by suseendran.rengabashyam on 2010-01-19
Hi,

Can you post the output of the following commands to troubleshoot your problem:

a) sudo lspci
b) sudo nm-tool
c) sudo ifconfig
d) sudo lshw -c network

---

### Post by Cabs21 on 2010-01-19
**System>Administration>Hardware Drivers**
This is at the top left of your screen.  start there and pick the correct drivers for your hardware.  Make sure you are connected to the Internet by LAN cable when you do this or it will not find any drivers.

---

### Post by Acimer on 2010-01-19
> 
a) sudo lspci
b) sudo nm-tool
c) sudo ifconfig
d) sudo lshw -c network

andrej@nakama:~$ **sudo lspci**
[sudo] password for andrej: 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

andrej@nakama:~$ **sudo nm-tool**

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        00:1E:33:CF:10:3B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off
andrej@nakama:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:cf:10:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

andrej@nakama:~$ **sudo lshw -c network**
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:cf:10:3b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:4000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:d4600000-d4603fff

andrej@nakama:~$ **sudo ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1e:33:cf:10:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by Acimer on 2010-01-19
> **System>Administration>Hardware Drivers**
This is at the top left of your screen.  start there and pick the correct drivers for your hardware.  

I'm not currently at home and here at the university I can connect only with wireless connection, so i'll test it when I get home.

---

### Post by suseendran.rengabashyam on 2010-01-19
Hi,

A lot of users have reported problems with Realtek 8192E on Karmic. Here is a thread related to some of these problems:

[http://ubuntuforums.org/showthread.php?t=1239342](http://ubuntuforums.org/showthread.php?t=1239342)
       
As far as your wired network is concerned, please go to
     
System->Preferences->Network Connections->Auto ethX->Edit->IPv4 Settings
     
There you can select the connection method, Addresses, DNS servers, etc. With the right settings there, your wired interface should come up with the suitable IP address.
     
Let me know if this works for you.

---

### Post by Acimer on 2010-01-19
Thanks for the useful link! I will try to get the wireless connection with the instructions people on that thread posted but since I would first like to make the wired connection operational it like to concentrate on that issue first.

> 
System->Preferences->Network Connections->Auto ethX->Edit->IPv4 Settings



I went to the Network connections as you suggested but firstly I couldn't get to the edit option on the eth0 (it is grayed out as you can see in the picture). Should I make a new connection and then edit that or what?

Secondly can you clarify: 
> There you can select the connection method, Addresses, DNS servers, etc. 
Which are the right settings? What do I put for the connection method? Which address(es)? DNS server is the one that i got on the paper from the ISP? 

Sorry for the newbie questions :)

---

### Post by Acimer on 2010-01-20
update: I've managed to get a wired connection via pppoeconf. So now i have a connection but Network Manager is not showing that there is any connection. 
How do I fix this?

I will now try to get wireless working

---

### Post by suseendran.rengabashyam on 2010-01-20
Hi,


If you have configuration for an interface specified in /etc/network/interfaces, NM does not manage that interface and hence it is not editable in NM. pppoeconf adds entries to /etc/network/interfaces. That may explain the behavior that you see.
       

If you are OK with managing the interface manually through settings in /etc/network/interfaces, your current set up is fine.


       If you want to let NM manage your interface, you can do the following:
       

1) Comment out the lines related to eth0 in /etc/network/interfaces
2) Enter the command: sudo /etc/init.d/networking restart
3) Enter the command: sudo /etc/init.d/network-manager restart
3) Delete the "ifupdown (eth0)" connection in the NM applet if it is present
4) Click on Add
5) Give a suitable Connection name, say "Auto eth0" 
6) Enter your MAC address, in your case it is 00:1e:33:cf:10:3b
7) Click on Apply.
8) Follow instructions at [URL="http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html"]
[/URL][http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html)
 for setting up PPPOE using NM.

---

