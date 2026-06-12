---
title: "Wireless conections do not appear in network settings"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by Spik on 2009-01-16
Hey!
I cannot use any wireless conection cuz my laptop does not recognized wireless servers! In network settings the wireless conections disapeared. When i was using the the previous version of ubuntu everything was fine, but now it just doesn't work.
Thanks for you atention

---

### Post by superprash2003 on 2009-01-16
go to the terminal and post output of the following commands
1)lshw -C network
2)iwconfig

---

### Post by Spik on 2009-01-16
hei thanks for answering!
I did what you told me but i couldn't fix the problem!
what should i do next?

---

### Post by b747pete on 2009-01-16
The 2 terminal commands are only going to show you the configuration, not actually repair it.

The first will show you the installed/recognized network adapters, the second the status of your wireless connection.
------------------------------:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"The Green"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:97:8B:6A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=78/127  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-----------------:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:c1:23:e9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wmaster0
       version: 01
       serial: 00:04:e2:63:64:b3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=prism54pci ip=192.168.1.106 latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11g

Good luck

---

### Post by superprash2003 on 2009-01-18
right.. as mentioned above.. go to the terminal(application->accessories) and then type those commands. you would get an output.. post that here..

---

