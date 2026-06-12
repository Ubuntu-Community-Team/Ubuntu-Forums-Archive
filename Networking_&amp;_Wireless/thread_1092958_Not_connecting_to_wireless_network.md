---
title: "Not connecting to wireless network"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by karthik_jce on 2009-03-11
Hi Experts,

I Have installed ubuntu (Wubi install on windows XP) and I have a Netgear WG111v3 wireless adapter.

I installed the hardware driver and the adapter got detected correctly. It detects my wireless network correctly and asks for the WEP key which I have enabled on the wireless router.

But when I give the WEP key and connect to the network it is not connecting and repeatedly asks for the WEP key (periodically). 
I have attached the logs along with this post. Please let me know how to proceed with this.

Thanks 
Karthik

---

### Post by karthik_jce on 2009-03-12
Hi,

I tried the following to make my wireless network work but still in vain, Posting the logs hoping suggestion to get this thing to work,

karthik@ubuntu:~$ lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:b7:3b:19
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:2a:bc:f9:53
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg111v3 driverversion=1.53+NETGEAR Inc.,04/23/2007,5.1 multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:1a:a9:5c:94:64
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
karthik@ubuntu:~$ 

karthik@ubuntu:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Shan"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:46:A3:E0:EA   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

karthik@ubuntu:~$ 
karthik@ubuntu:~$ lsusb
Bus 005 Device 002: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
karthik@ubuntu:~$ ndiswrapper -l
wg111v3 : driver installed
	device (0846:4260) present (alternate driver: rtl8187)
karthik@ubuntu:~$ uname -a
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
karthik@ubuntu:~$ 

karthik@ubuntu:~$ dmesg | grep -e ndis -e wlan
[   11.642225] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.153276] ndiswrapper: driver wg111v3 (NETGEAR Inc.,04/23/2007,5.1080.0423.2007) loaded
[   16.928534] wlan0: ethernet device 00:1e:2a:bc:f9:53 using NDIS driver: wg111v3, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:4260.F.conf
[   16.928566] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   16.928627] usbcore: registered new interface driver ndiswrapper
[  173.280012] wlan0: no IPv6 routers present
karthik@ubuntu:~$ 
karthik@ubuntu:~$ sudo ifconfig wlan0 down
[sudo] password for karthik: 
karthik@ubuntu:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:2a:bc:f9:53
Sending on   LPF/wlan0/00:1e:2a:bc:f9:53
Sending on   Socket/fallback
karthik@ubuntu:~$ sudo ifconfig wlan0 up
karthik@ubuntu:~$ sudo iwconfig wlan0 essid "Shan"
karthik@ubuntu:~$ sudo iwconfig wlan0 key 6368616D61
karthik@ubuntu:~$ sudo iwconfig wlan0 key open 
karthik@ubuntu:~$ sudo iwconfig wlan0 mode managed 
karthik@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1e:2a:bc:f9:53
Sending on   LPF/wlan0/00:1e:2a:bc:f9:53
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
karthik@ubuntu:~$ 
karthik@ubuntu:~$ dmesg | grep -e ndis -e wlan
[   11.642225] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.153276] ndiswrapper: driver wg111v3 (NETGEAR Inc.,04/23/2007,5.1080.0423.2007) loaded
[   16.928534] wlan0: ethernet device 00:1e:2a:bc:f9:53 using NDIS driver: wg111v3, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0846:4260.F.conf
[   16.928566] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   16.928627] usbcore: registered new interface driver ndiswrapper
[  173.280012] wlan0: no IPv6 routers present
[  596.375788] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  754.196288] ndiswrapper (add_wep_key:848): adding encryption key 1 failed (C0010015)
[  770.106958] ndiswrapper (add_wep_key:848): adding encryption key 1 failed (C0010015)
[  789.808678] ndiswrapper (add_wep_key:848): adding encryption key 1 failed (C0010015)
[  805.767196] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  816.304016] wlan0: no IPv6 routers present


The logs are saying "adding encryption failed" but the key I added is correct. Not sure what could be the problem.

---

