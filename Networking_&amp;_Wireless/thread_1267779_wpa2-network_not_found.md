---
title: "wpa2-network not found"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by Nanimatti on 2009-09-16
Hey guys,

this is my first thread ever. im a linux-noob and starting to discover it all.
i already fixed some problems as  my boxes didnt work out of the box or the internet connection only worked with the power supply on, so im pretty proud o f myself:)
but now ive got a problem with my wifi network i cant fix. 
 my netbook (compaq mini 701 eg) doesnt find a wpa2 wireless connection in my home and i was wondering if there is any method to solve this problem, because im using my internet through a cable which is very anoying!!
didnt find any thread regarding this problem.

hope you can help me

thanks!

---

### Post by Cuba71 on 2009-09-16
Is the router set to broadcast the SSID?

Does it work under Windows?

---

### Post by Nanimatti on 2009-09-21
yes it works under windows, and its set to work under ssid.

---

### Post by kevdog on 2009-09-21
What driver are you using since its highly going to be denpendent on driver type

---

### Post by Nanimatti on 2009-09-22
iwconfig:

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:168
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

lspci:

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

ifconfig:

eth0      Link encap:Ethernet  Hardware Adresse 00:22:64:74:75:72  
          inet Adresse:192.168.178.23  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::222:64ff:fe74:7572/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:3504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3729 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:3179506 (3.1 MB)  TX bytes:622979 (622.9 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  Hardware Adresse 00:23:4e:ba:55:09  
          inet6-Adresse: fe80::223:4eff:feba:5509/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Basisadresse:0xc000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

i isntalled WICD, but it didnt help....

---

### Post by kevdog on 2009-09-22
Can you post

lspci -nnm
lshw -C network

---

### Post by Nanimatti on 2009-09-22
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:ba:55:09
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:22:64:74:75:72
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.178.23 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c6:9a:44:0d:64:03
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

lspci -nnm

00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 945GME Express Memory Controller Hub [27ac]" -r03 "Hewlett-Packard Company [103c]" "Device [361a]"
00:02.0 "VGA compatible controller [0300]" "Intel Corporation [8086]" "Mobile 945GME Express Integrated Graphics Controller [27ae]" -r03 "Hewlett-Packard Company [103c]" "Device [361a]"
00:02.1 "Display controller [0380]" "Intel Corporation [8086]" "Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [27a6]" -r03 "Hewlett-Packard Company [103c]" "Device [361a]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801G (ICH7 Family) High Definition Audio Controller [27d8]" -r02 "Hewlett-Packard Company [103c]" "Device [361a]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 1 [27d0]" -r02 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801G (ICH7 Family) PCI Express Port 2 [27d2]" -r02 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #1 [27c8]" -r02 "Hewlett-Packard Company [103c]" "Device [361a]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #2 [27c9]" -r02 "Hewlett-Packard Company [103c]" "Device [361a]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #3 [27ca]" -r02 "Hewlett-Packard Company [103c]" "Device [361a]"
00:1d.3 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB UHCI Controller #4 [27cb]" -r02 "Hewlett-Packard Company [103c]" "Device [361a]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801G (ICH7 Family) USB2 EHCI Controller [27cc]" -r02 -p20 "Hewlett-Packard Company [103c]" "Device [361a]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -re2 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "82801GBM (ICH7-M) LPC Interface Bridge [27b9]" -r02 "Hewlett-Packard Company [103c]" "Device [361a]"
00:1f.1 "IDE interface [0101]" "Intel Corporation [8086]" "82801G (ICH7 Family) IDE Controller [27df]" -r02 -p8a "Hewlett-Packard Company [103c]" "Device [361a]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801G (ICH7 Family) SMBus Controller [27da]" -r02 "Hewlett-Packard Company [103c]" "Device [361a]"
01:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11b/g [4315]" -r01 "Hewlett-Packard Company [103c]" "Device [1508]"
02:00.0 "Ethernet controller [0200]" "Marvell Technology Group Ltd. [11ab]" "88E8040 PCI-E Fast Ethernet Controller [4354]" "Hewlett-Packard Company [103c]" "Device [361a]"

---

