---
title: "rt2500usb wireless - permanent device not ready"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by klosso on 2011-02-21
I had wifi + bluetooth module connected thru usb  (looks like [http://www.komputersklep.com/zd/wifibl/1_wm.jpg](http://www.komputersklep.com/zd/wifibl/1_wm.jpg))

Wifi card is based on RT2571F
Unfortunatlly is stuck as not ready by NW .
This is really strange becouse it say that is HW blocked (somethings like  swith for wifi on laptops was in off position),but there is no any on/off switch on this module .
Of course under win7 it works perfect.

From begining: 
ubuntu 10.10 ,kernel 
```
$ uname -r
2.6.35-25-generic

```Card is recognise as :
```
lsusb |grep -i rt
[COLOR=Blue]Bus 001 Device 007: ID 148f:2570 Ralink Technology, Corp. RT2570 Wireless Adapter[/COLOR]

```and system load rt2500usb modules for this card
```
lsmod |grep -i rt
parport_pc             26058  0 
rt2500usb              18049  0 
[COLOR=Blue]rt2x00usb               9779  1 rt2500usb[/COLOR]
rt2x00lib              27275  2 rt2500usb,rt2x00usb
led_class               2633  1 rt2x00lib
mac80211              231959  2 rt2x00usb,rt2x00lib
cfg80211              144694  2 rt2x00lib,mac80211
agpgart                32011  1 nvidia
parport                31492  3 parport_pc,ppdev,lp

```when I try to up interface it say:
```

 sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill

```**but there is no way to unblock **
```

$ rfkill list 
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    **Hard blocked: yes**
$sudo rfkill unblock all
$sudo rfkill unblock 1
$sudo rfkill list 
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    [COLOR=Red]**Hard blocked: yes**[/COLOR]

```**how I can unblock this ?**

Of course I read similar threads [http://ubuntuforums.org/showthread.php?t=1439568&highlight=rt2500usb](http://ubuntuforums.org/showthread.php?t=1439568&highlight=rt2500usb) but that was not really helpfull

here is print from lshw
```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:25:22:21:86:01
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:21 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  [COLOR=Blue]*-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8.1
       logical name: wlan0
       serial: 00:11:09:4e:2f:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2500usb driverversion=2.6.35-25-generic [COLOR=Red]firmware=N/A [/COLOR]link=no multicast=yes wireless=IEEE 802.11bg[/COLOR]

```Is there any way to unblock Hard blocked in rfkill 
I don't know it is important but * firmware=N/A*
P.S. Sorry for bad english

---

### Post by fladam on 2012-07-15
Hello, I have the same problem with the same card. Did you found some solutions?

---

### Post by klosso on 2012-07-16
Unfortunately no. 
It seems that  should be some pin to HW switch , but I have only module it self , and don't have clue where to connect this .
For now it's leis  in bottom of my shelf full of dust :(
I you have any luck with this please post here

---

