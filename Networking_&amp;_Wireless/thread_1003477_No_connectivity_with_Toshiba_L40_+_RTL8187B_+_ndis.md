---
title: "No connectivity with Toshiba L40 + RTL8187B + ndiswrapper"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Meriadok on 2008-12-06
I installed Ubuntu 8.10 on my Toshiba Satellite L40 laptop as second system (first - vista home premium). Just after installation my wlan (onboard RTL8187B) worked well. But i noticed some some problems with radius of connection. So i decided to install ndiswrapper with windows driver from toshiba site.
After reboot there was no available network in list.
There is some information from terminal:
> gelirhil@gelirhil-laptop:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8197) present (alternate driver: rtl8187)
> gelirhil@gelirhil-laptop:~$ sudo lshw -C network
[sudo] password for gelirhil: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:60:f2:87:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:1b:db:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.53+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 32:b2:a4:13:c5:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

> gelirhil@gelirhil-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

After deleting and reinstalling windows driver in ndiswrapper my network appears in list but i still can't connect to it. If using WPA-PSK encryption Ubuntu refuses my password. When i don't use any encryption a message "connection was refused" appears.
In windows all works well but i must turn on wireless card by Fn+F8 every time on startup. All other devices (for example, wm pda) works well too.
How can i make ndiswrapper work properly or restore original non-windows driver?

---

