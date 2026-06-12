---
title: "Wireless not working on lenovo 3000 G430"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by Anja K on 2009-08-13
Hi, just got a new lenovo 3000 g430, but can't get the wireless to work.  The laptop is simply not recognising the wireless network in the list of networks. I am using ubuntu 9.04.  It seems to work fine for everybody else who has to use the same network, both on ubuntu and windows.  Any help greatly appreciated - I have a little knowledge but basically am still very new.... Thank you so much. Anja

---

### Post by VelkoMK on 2009-08-13
Well I kinda got the same Issue, solved it. Can you tell us the Brand name and Model of your Wireless card?

---

### Post by Anja K on 2009-08-13
Hi, its a bcm 4312.

---

### Post by Anja K on 2009-08-13
I have added the Broadcom STA wireless driver now, hoping that would help, but the problem is still there... :(

---

### Post by superprash2003 on 2009-08-13
post output of
1)lshw -C network
2)iwconfig
3)sudo iwlist scanning

---

### Post by Anja K on 2009-08-14
Dear Superprash2003,

Here's what it says - and thanks a lot for your help. Hope it's resolvable :)
Anja

[U]lshw -C network
[/U]WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:ec:74:c1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:be:a3:58
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.1.141 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:16:b4:42:96:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

[U]iwconfig
[/U]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions

[U]sudo iwlist scanning 
[/U][sudo] password for cis5: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

pan0      Interface doesn't support scanning.

---

### Post by superprash2003 on 2009-08-14
it could be the wifi switch is OFF , laptops come with a wifi switch , make sure its ON..
for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by Anja K on 2009-08-15
Hi, I had already checked that, and the switch is on... Any other ideas what might be happening?

---

