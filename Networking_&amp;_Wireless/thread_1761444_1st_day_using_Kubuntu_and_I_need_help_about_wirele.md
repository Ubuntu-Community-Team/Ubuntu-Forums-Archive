---
title: "1st day using Kubuntu and I need help about wireless"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by cyk016 on 2011-05-18
Im newbie, know nothing about linux and first day using Kubuntu.

Im using 11.04 on my HP 6930p laptop and wireless (Intel Wifi Link 5100) not working after install. **Wireless is working when I try Kubuntu from CD.**

Snapshot 1: Trying Kubuntu from CD, Network Manager show "WLAN not connected"
[http://s510.photobucket.com/albums/s342/cyk016/?action=view&current=snapshot1.png](http://s510.photobucket.com/albums/s342/cyk016/?action=view&current=snapshot1.png)

Snapshot 2: Trying Kubuntu from CD, Im able to add new connection, able to scan wifi, connect and surf net, every thing is perfect.
[http://s510.photobucket.com/albums/s342/cyk016/?action=view&current=snapshot2.png](http://s510.photobucket.com/albums/s342/cyk016/?action=view&current=snapshot2.png)

Im very satisfy with the try run and then I install Kubuntu to my HDD, dual boot without remove my WinXP

Snapshot 3: After install and run from HDD, Network Manager show "Wireless disabled in software"
[http://s510.photobucket.com/albums/s342/cyk016/?action=view&current=snapshot3.png](http://s510.photobucket.com/albums/s342/cyk016/?action=view&current=snapshot3.png)

Snapshot 4: Cant add new connection, scan return 0 result.
[http://s510.photobucket.com/albums/s342/cyk016/?action=view&current=snapshot4.png](http://s510.photobucket.com/albums/s342/cyk016/?action=view&current=snapshot4.png)

I have Google this issue for few days, I get a lot of "similar" topic, but none of them is identical with my problem, and their solution not working for me as well. 

Appreciate that if any one can help you to resolve my problem.

---

### Post by cyk016 on 2011-05-18
I have gather more info and post here. Please ... I need help.

1 ) Machine Brand and Model (PC/Laptop):
HP EliteBook 6930p (Laptop)

2 ) Wireless Brand, Model and Wireless Chipset:
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
02:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300

3 ) check interface:
eth0      Link encap:Ethernet  HWaddr 00:23:7d:97:85:46  
          inet addr:10.228.215.4  Bcast:10.228.215.255  Mask:255.255.255.0
          inet6 addr: fe80::223:7dff:fe97:8546/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:670673 (670.6 KB)  TX bytes:101311 (101.3 KB)
          Interrupt:22 Memory:98800000-98820000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1480 (1.4 KB)  TX bytes:1480 (1.4 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

4 ) Check for modules:
iwlagn                284569  0 
iwlcore               148965  1 iwlagn
mac80211              257001  2 iwlagn,iwlcore
cfg80211              156212  3 iwlagn,iwlcore,mac80211

5 ) Kernel boot messages
[   17.243139] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.243143] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   17.243217] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.243227] iwlagn 0000:02:00.0: setting latency timer to 64
[   17.243262] iwlagn 0000:02:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   17.262650] iwlagn 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   17.262653] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   17.262656] iwlagn 0000:02:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   17.276146] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.276238] iwlagn 0000:02:00.0: irq 47 for MSI/MSI-X
[   17.314586] iwlagn 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[  653.428467] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.

6 ) Network configuration
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:23:7d:97:85:46
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=1.8-3 ip=10.228.215.4 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:98800000-9881ffff memory:98824000-98824fff ioport:70e0(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:8a:09:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:98600000-98601fff

7 ) Scan for networks:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

8 ) Ubuntu Version:
Description:    Ubuntu 11.04

9 ) Kernel/architecture (including 32 vs. 64 bit):
2.6.38-8-generic i686

10 ) Restarting the network:
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

---

### Post by chili555 on 2011-05-18
> [ [COLOR="Red"]653.428467[/COLOR]] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.This timestamp indicates that the wireless switch or key combination was toggled well after boot. Please manipulate the switch and do:```
rfkill list all
```Post the result. Can you get the wireless to not blocked? If so, your wireless should be working.

---

### Post by cyk016 on 2011-05-19
cyk016@cyk016-Kubuntu:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
cyk016@cyk016-Kubuntu:~$ 


Yes, there are all no blocked .... but don know why my wireless still cant work.

Network Manager show "Wireless disabled in software"
[http://s510.photobucket.com/albums/s...=snapshot3.png](http://s510.photobucket.com/albums/s...=snapshot3.png)

Thats why i search a lot of wireless problem with Kubuntu over net and i cant get a single case is similar with my problem.

Most of the problem user face is like cant toggle wifi switch ... driver not working ... etc ....

For my case, i feel very weird,
1) boot from CD wifi is working
2) iwlist scan able to detect my router
3) rfkill shows positive result
4) dmesg also shows positive result

But then Network Manager told me that "Wireless disabled in software" .. ..

:confused: im mad ...

---

### Post by chili555 on 2011-05-19
I must admit, it looks a bit unusual. Please detach the ethernet cable, reboot and run:```
dmesg | grep -e iwl -e wlan
```Post the result here.

---

### Post by cyk016 on 2011-05-20
> **chili555 said:**
> I must admit, it looks a bit unusual. Please detach the ethernet cable, reboot and run:```
dmesg | grep -e iwl -e wlan
```Post the result here.

chili, thanks for helping, here is the requested post.

cyk016@cyk016-Kubuntu:~$ dmesg | grep -e iwl -e wlan
[   17.467914] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.467917] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   17.467988] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.468027] iwlagn 0000:02:00.0: setting latency timer to 64
[   17.468076] iwlagn 0000:02:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   17.490350] iwlagn 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   17.490353] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   17.490355] iwlagn 0000:02:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   17.490756] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.490835] iwlagn 0000:02:00.0: irq 47 for MSI/MSI-X
[   17.518995] iwlagn 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[   17.526991] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
cyk016@cyk016-Kubuntu:~$ rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
cyk016@cyk016-Kubuntu:~$

---

### Post by chili555 on 2011-05-20
It looks perfect! Doesn't your wireless work now, with the ethernet cable detached? I suspect that Network Manager was turning off the wireless as long as wired ethernet was available. That's one of its "features."

---

### Post by apointing on 2011-06-12
> **cyk016 said:**
> chili, thanks for helping, here is the requested post.

cyk016@cyk016-Kubuntu:~$ dmesg | grep -e iwl -e wlan
[   17.467914] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.467917] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   17.467988] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.468027] iwlagn 0000:02:00.0: setting latency timer to 64
[   17.468076] iwlagn 0000:02:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   17.490350] iwlagn 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   17.490353] iwlagn 0000:02:00.0: Device SKU: 0Xb
[   17.490355] iwlagn 0000:02:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   17.490756] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.490835] iwlagn 0000:02:00.0: irq 47 for MSI/MSI-X
[   17.518995] iwlagn 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[   17.526991] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
cyk016@cyk016-Kubuntu:~$ rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
cyk016@cyk016-Kubuntu:~$
I had exactly the same symptoms with a wireless bcm4313 on a lenovo S10-3s.

After many googles and unsuccessful trials I installed Wicd, removed network manager and was able to connect via wireless.

Hope it works for you.

---

