---
title: "broadcom b43 wifi driver installed but not working"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by rhyz on 2009-05-11
I had ubuntu 8.10 and a buffalo 54g usb wifi fin and all worked fine.

updated to 9.04 still used buffalo 54g wifi usb fin and still works.

I found out i had a built in wifi card and it is a

broadcom corporation BCM4306 802.11b/g wireless lan controller (rev 03)

i have searched google and it seems lots of people have problems with this card and ubuntu i used hardware drivers which said i needed a B43 driver which is installed and activated and it still isnt finding networks.

i have used 2 tutorials on the internet and none of them have worked.

networking and wireless connections are enabled.

if your wondering why i dont use buffalo fin its because if i move i lose connection and it is a bit old!!!

---

### Post by superprash2003 on 2009-05-11
post output of the following
1)sudo iwlist scanning
2)iwconfig
3)lshw -C netowrk

---

### Post by rhyz on 2009-05-12
1.    sudo iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan1     No scan results

pan0      Interface doesn't support scanning.




2.    iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


3.    sudo lshw -C network


 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:b6:df:72
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:0b:6b:48:ad:6c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 7a:0c:6c:57:10:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



HOPE THIS HELPS ???

---

### Post by superprash2003 on 2009-05-14
ensure that you posted these outputs when you had a wifi network around, check to see that if there is any switch in your wlan card..

---

