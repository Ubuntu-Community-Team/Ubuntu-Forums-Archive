---
title: "invalid access point wireless"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by tommynz1975 on 2009-01-18
Hi folks 
I think with my luck my problem is common but I am lost reading the other threads.

The machine I am on is a compaq presario c500 laptop with built in wireless
The blue wireless light is on
I am running Hardy 8.04 upgraded from 6.06
after install Hardy found the wireless drivers

I am not able to get my wireless card working, interface wlan0
eth0 seems to work fine

The password type is wpa-psk

I get aliases like wlano:avahi appearing that I did not creates
Please if I could be walked through getting the wireless connected and
any aliases un-needed removed, I would be most happy

Please let me know what other information is needed
can aliases like wlano:avahi upset things?

the command  iwconfig ap any 
returns
access point invalid

~$ sudo lshw -C network
```

*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:bc:36:05
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.2 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:26:d8:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11
```contents of 
/etc/network/interf```
aces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
address 10.0.0.9
netmask 255.255.255.0
gateway 10.0.0.1
wpa-psk series of numbers and letters appeared here
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid NETGEAR
```$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```$ ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:bc:36:05  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:febc:3605/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:251532 (245.6 KB)  TX bytes:62663 (61.1 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77956 (76.1 KB)  TX bytes:77956 (76.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:26:d8:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-26-D8-5F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by tommynz1975 on 2009-01-19
I have upset something someplace as when I boot with the cd ubuntu 8.04.1 
it comes up with Hardware drivers Icon top right of the screen

asking me to install b43 and its firmware.
reading other threads I have run these commands
I hope this may help some-one give me a solution...

Many many thanks


ls /lib/firmware/
dmesg | grep -e wlan -e adio
 sudo iwlist scan
 lspci -nn

ls /lib/firmware/
2.6.15-53-386  2.6.24-23-386  b43  b43legacy

dmesg | grep -e wlan -e adio
[   69.574464] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   72.283956] Registered led device: b43-phy0:radio
[   75.044843] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.623650] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   83.292837] Registered led device: b43-phy0:radio
[   83.332743] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   84.870734] Registered led device: b43-phy0:radio
[   84.871084] ADDRCONF(NETDEV_UP): wlan0: link is not ready

 sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:5A:01:B6
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=93/100  Signal level=-41 dBm  Noise level=-69 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000262c3ef862

 lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

---

### Post by tommynz1975 on 2009-01-20
solved using the commands

sudo modprobe ndiswrapper
sudo gedit /etc/modules added ndiswrappser


>  Ubuntuforums user brynjarh
have no idea what happened but I restarted the computer and did sudo modprobe ndiswrapper and it worked, going to try to restart again and see what happens.
...
[ 86.697604] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 100.045884] NET: Registered protocol family 17
[ 105.253552] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 119.985852] wlan0: no IPv6 routers present

*EDIT*
It works every time now when I do sudo modprobe ndiswrapper, I think the problem was that wlan0 doesn't go "up" until I have actually connected it, so it started working after I set in the password for my wireless router, now the only problem is that I have to do modprobe every time I reboot, how do I get it to load on boot?

*EDIT*
Works now perfectly after I added "ndiswrapper" without the quotes to brynjarh
have no idea what happened but I restarted the computer and did sudo modprobe ndiswrapper and it worked, going to try to restart again and see what happens.
...
[ 86.697604] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 100.045884] NET: Registered protocol family 17
[ 105.253552] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 119.985852] wlan0: no IPv6 routers present

*EDIT*
It works every time now when I do sudo modprobe ndiswrapper, I think the problem was that wlan0 doesn't go "up" until I have actually connected it, so it started working after I set in the password for my wireless router, now the only problem is that I have to do modprobe every time I reboot, how do I get it to load on boot?

*EDIT*
/etc/modulesThis has happily fixed the problem.

---

