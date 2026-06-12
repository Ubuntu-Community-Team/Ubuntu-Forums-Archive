---
title: "problem with wicd... plz help...."
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Hantan on 2009-06-24
[B]hi all.... i am a newbie to linux and ubuntu... currently running 8.10 intrepid.... my problem is that i replaced n/w manager with wicd to see if it would detect my wireless n/w but it doesn't... windows detects it smoothly..... what could the reason be?? it says no wireless networks in range.... also when i tried scanning it gives the below msg....
[/B]
[I]ananth@ananth-zzzzz:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

[/I][B]i have almost visited every other forum with a similar problem but none seem to help..... the output of lshw is below....
[/B]
[I]ananth@ananth-zzzzz:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:ad:36:e2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.3 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:46:dc:0d:8c:94
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
[/I][B]
plz help me out...... :( i want my wireless connection.... :(
[/B]

---

### Post by Hantan on 2009-06-24
hello?? plz help... trying this for the past 3 days.... :(

---

### Post by Manthis on 2009-07-03
You have a atheros chipset AR242x which requires ath5k module...

Can you post the result of this command:
lsmod | grep ath5k

If this doesn't return anything, then you must install this module. 

Regards

---

### Post by superprash2003 on 2009-07-04
try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

