---
title: "Wireless Trouble"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by tallbus1 on 2009-06-02
Hey guys!

So, I'm having some trouble, right now I am running an old Compaq Presario V2000, with Jaunty (9.04 I believe).  This computer has a little blue button that I believe shows the internet card is on, as it turns on and off my internet in Windows. In ubuntu I can't connect to my wireless network and my little blue button wont turn on.

In windows when i go into Network Adapters under device manger these three things are there:
1394 Net Adapter
Broadcam 802.11b/g WLAN
Realtek RTL8139/810x Family Fast Ethernet NIC

I have been hearing alot about b43 driver or something (have no idea)

And I was told in my other thread to do

```
sudo apt-get install b43-fwcutter
```

Ubuntu said it couldnt find the package I am COMPLETELY new, and COMPLETELY LOST


Lastly I was told to put in a couple commands and this is what was returned I hope this help:

```
ashton@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extension

ashton@ubuntu:~$ sudo lshw -C network
[sudo] password for ashton: 
  *-network:0      C          
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:a5:6c:2e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:ef:a3:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:f6:94:eb:02:e0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


```

---

### Post by tallbus1 on 2009-06-02
bump

---

### Post by Ayuthia on 2009-06-02
If you have a working internet connection, please try the following:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
It will update the repository list in your system so Ubuntu should be able to find it.

Hope that helps.

---

