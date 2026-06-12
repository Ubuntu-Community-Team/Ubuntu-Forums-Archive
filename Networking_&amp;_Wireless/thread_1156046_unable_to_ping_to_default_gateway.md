---
title: "unable to ping to default gateway"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by GreenSmurf on 2009-05-11
Hey all , 

i just install ubuntu 9.04 on my Dell studio 1357 leptop . I'm having a hard time try to connect to my wireless router Edimax SR-6504n . 

according to lspci , my network card is "Broadcom Corporation BCM4312" . witch should work out of the box . 
after the installation was done , i got this message saying that  a third party driver was install for the wireless card . I thought that was o.k since i really got eth1 interface that was my wireless card . 

To make a long story short . I'm able to connect to my router . I see a message saying connection establish on my leptop screen . and i'm able to see the leptop in my router client list . But i'm unable to ping to default gateway since the destination is unreachable . 

i'm posting here some files that might help  . 

ifconfig : 

eth0      Link encap:Ethernet  HWaddr 00:21:70:86:6d:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:70:9b:f8  
          inet addr:192.168.2.126  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe70:9bf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:412275
          TX packets:162 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:15209 (15.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4768 (4.7 KB)  TX bytes:4768 (4.7 KB)

-----------------------------------------------------------------------------
iwconfig :

eth1      IEEE 802.11bg  ESSID:"FuckOff"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: BA:67:D1:71:79:EF   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

-----------------------------------------------------------------------------
70-persistent-net.rules:

# PCI device 0x14e4:0x1698 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:21:70:86:6d:43", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:4d:70:9b:f8", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

-----------------------------------------------------------------------------
interfaces:

auto lo
iface lo inet loopback

-----------------------------------------------------------------------------

route : 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

This happen for every network i'm trying to connect . I'm getting connection establish , but i'm unable to ping to any address but my localhost . 

Also , i dont think it is iptables problem , since i have nothing in it  . 

What do you think ? any idea ? 

One more think  i like to ask is , why is my wireless attach to eth1 and not wlan0 ? does it matter ?

---

### Post by Peter09 on 2009-05-11
What is your routers IP?

---

### Post by Peter09 on 2009-05-11
This looks suspicious

> eth1      Link encap:Ethernet  HWaddr 00:23:4d:70:9b:f8  
          inet addr:192.168.2.126  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe70:9bf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:412275
          TX packets:162 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (

note the TX (transmissons is 162 packets
while
RX is 0

---

### Post by GreenSmurf on 2009-05-11
My router ip address is 192.168.2.1  netmask 255.255.255.0 

What does TX and RX mean ? Is it Transmit and Receive something ? so , i can transmit but i cant receive . :confused:

---

### Post by Peter09 on 2009-05-11
As you guessed for RX and TX.

Can you do
```
lshw -C network
```
as I want to check the drivers being used

---

### Post by superprash2003 on 2009-05-11
post output of **sudo iptables -L** .. do you have firestarter or anything similar?

---

### Post by GreenSmurf on 2009-05-11
Here are the drivers  .. 

lshw -C network 

  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4d:70:9b:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:86:6d:43
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:2f:57:b8:55:25
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

==============================

and iptables -L 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  


==============================

I dont have firestarter install on the system. And nothing similar as far as i know . As i said , it's a clean fresh installation of ubuntu 9.04 . If by default there is no firewall (beside iptables ) , so i have non  . 

Do you think it has something to do with the fact that my wireless card shown as eth1 ? can i change it to wlan0 ? 

I really appreciate your help and your answers . Hope it make sense to you  ... cause i can't figure out whats going on .. :(

---

### Post by Peter09 on 2009-05-11
A lot of people are having a problem with the Wl0 driver. (Which you have).

---

### Post by Peter09 on 2009-05-11
If you want to experiment try blacklisting wl0 and installing fw-cutter

---

