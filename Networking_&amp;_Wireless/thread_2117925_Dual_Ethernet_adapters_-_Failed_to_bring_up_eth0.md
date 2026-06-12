---
title: "Dual Ethernet adapters - Failed to bring up eth0"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by joelbarnard on 2013-02-19
Gurus of the internet please help. I am trying to configure 2 network adapters, one for local traffic (eth0) and the other for a T1 line to handle incoming requests to apache from the outside world. I am running 12.04 LTS Server.

Here is my /etc/network/interfaces ( I am using x to hide actual addresses )

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface for local traffic

auto eth0
iface eth0 inet static
address 192.168.1.201
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1

# Second NIC for T1

auto eth1
iface eth1 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
dns-nameservers x.x.x.x x.x.x.x

if i run ifconfig -a i get

eth0    Link encap:Ethernet  HWaddr 00:13:3b:0c:1b:12  
          inet addr:192.168.1.201  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:3bff:fe0c:1b12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13716 errors:0 dropped:146 overruns:0 frame:0
          TX packets:1064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1077933 (1.0 MB)  TX bytes:147855 (147.8 KB)
          Interrupt:46 Base address:0x2000 

eth1    Link encap:Ethernet  HWaddr 00:16:76:c2:81:b9  
          inet addr:x.x.x.x  Bcast:x.x.x.x  Mask:x.x.x.x
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:90400000-90420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40004 (40.0 KB)  TX bytes:40004 (40.0 KB)

When I restart the network or reboot I get

ssh start/running, process 2853
RTNETLINK answers: File exists
Failed to bring up eth1.

Please help!

---

### Post by kevdog on 2013-02-20
This seems like a drive issue.  Not really at this point like a configuration issue.

We need to know more about the actual type of hardware and drivers the individual network cards are using.

The eth1 link also looks suspicious.  Don't you want to set the ip address to a local (192.168.1.0/24) address as well?

---

### Post by The Cog on 2013-02-20
Notice that the word RUNNING is absent from the eth1 status (UP just means it is administratively enabled). This normally indicates a hardware problem. I would suggest to check cabling and low-level stuff like that. Swap the cables in eth0, eth1 and see if the problem moves.

---

### Post by joelbarnard on 2013-02-20
> **The Cog said:**
> Notice that the word RUNNING is absent from the eth1 status (UP just means it is administratively enabled). This normally indicates a hardware problem. I would suggest to check cabling and low-level stuff like that. Swap the cables in eth0, eth1 and see if the problem moves.

thanks so much for the reply. I have switched the cards and the opposite happens, the local IP structure works and the T1 does not, the symptom just switches adapters. I'm so lost here.

---

### Post by joelbarnard on 2013-02-20
> **kevdog said:**
> This seems like a drive issue.  Not really at this point like a configuration issue.

We need to know more about the actual type of hardware and drivers the individual network cards are using.

The eth1 link also looks suspicious.  Don't you want to set the ip address to a local (192.168.1.0/24) address as well?

Thank you for your reply... What would you like to know? How do I show you more driver info? Also, I am not sure what you meant in that last part, please clarify...

---

### Post by joelbarnard on 2013-02-20
When I run a lspci I get...

00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q963/Q965 PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q963/Q965 KT Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]

---

### Post by praseodym on 2013-02-20
```
 00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```
Please show:
```

lsmod
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by joelbarnard on 2013-02-20
I am ashamed to say that after 1 hour on hold, I discovered I had been given the wrong IP info from AT&T's IP Flex Team. The configuration works perfectly. Thank you all for your help.

---

