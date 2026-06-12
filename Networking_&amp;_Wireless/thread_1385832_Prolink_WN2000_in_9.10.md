---
title: "Prolink WN2000 in 9.10"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by psycho5 on 2010-01-20
Hi boys and girls! 

I just installed a fresh copy of 9.10 32bit and I'm trying to get this wireless adapter to work. The website provides a driver for linux for the wireless adapter. I installed it, but I don't know if its not working or is it just network manager that can't see the wireless network. 

The driver ( **RT2870USB(RT2870/RT2770)** )provided by the manufacturer's website is here: 

[http://www.prolink2u.com/new/support/download.php?q=WN2000&submit=Okay](http://www.prolink2u.com/new/support/download.php?q=WN2000&submit=Okay)

and its version 2.1.0. I checked for a newer version of that driver and its provided by Ralink (?) at version 2.2.0. Regardless, I can't get the dongle to connect. 

lsusb thinks the dongle is D-link, which is weird to me. 

```

$ lsusb
Bus 001 Device 002: ID 07b8:3071 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
oj@oj-desktop:~$ 


```

In network tools I can see eth0 (no problems here), wlan0 which is Active and multicast enabled, then there is unknown interface wmaster0 also Active but multicast disabled. 

I click the network connections tab there is Wireless Connections option with disconnected and both of them are grayed out. What do I do from here? 

Using the driver cd, I tried using ndiswrapper but in windows I can't find the .inf file, only .sys in device manager > view driver files.


here is some more info about the wireless, it seems to be recognized 

```

sudo lshw -C network
[sudo] password for oj: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:18:f3:10:92:ba
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:ee00(size=256) memory:fdcff000-fdcfffff memory:fdd00000-fdd1ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:0e:b7:7c:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn
oj@oj-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by psycho5 on 2010-05-28
*bump* help plz on this topic.

---

### Post by nonotdh on 2010-07-24
Try to use driver for RT3070USB,
I use it on my ubuntu 10.04.
You can download it from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
It works.

---

