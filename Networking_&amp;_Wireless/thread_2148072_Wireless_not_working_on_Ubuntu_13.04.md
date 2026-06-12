---
title: "Wireless not working on Ubuntu 13.04"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by Beckett1249 on 2013-05-23
I recently installed Ubuntu 13.04 on my Asus U56e laptop and the wireless is not working.
I've read multiple threads on this problem over the past few weeks and still can't find a solution. Wired connection works fine and I can see all of the available networks but when i try to connect to them it thinks for a minute and then says Disconnected- you are now offline. :confused:

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Networking & Wireless**.*

Please provide the output, from a terminal, of these two commands, one after the other:

```
iwconfig
sudo lshw -C network
```

---

### Post by Beckett1249 on 2013-05-23
wmx0      no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by Bucky Ball on 2013-05-23
And now this:

```
sudo lshw -C network
```

Welcome to the forums, BTW. ;)

---

### Post by Beckett1249 on 2013-05-23
*-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:c3:ff:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-21-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:51 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: c8:60:00:40:d3:2b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:54 memory:dd400000-dd43ffff ioport:a000(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: wmx0
       serial: 64:d4:da:6c:8f:51
       capabilities: ethernet physical
       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no

---

### Post by Bucky Ball on 2013-05-23
Just wondering if the wireless N has anything to do with this. Is you router N capable? You may need to switch N off at the local machine. 

Also, if you right click the network icon>Edit Connections>Wireless>IPv4, do you have 'Method = Automatic (DHCP)'? Or are you attempting to use a static IP?

You have a driver installed and all else seems to be working. You're just not associated/linked with the router/access point, consequently nor with a network.

---

### Post by Beckett1249 on 2013-05-23
Im not entirely sure. I've been using this router for a year when I had windows 7 installed and it works fine on the other devices in my house.
And I looked at my IPv4 and it is on Automatic (DHCP). I don't really know that much about routers but how would I switch it off?

---

### Post by Beckett1249 on 2013-05-23
[http://wikidevi.com/wiki/ClearAccess_Smart_RG_SR300NE](http://wikidevi.com/wiki/ClearAccess_Smart_RG_SR300NE)

this is the router

---

### Post by Bucky Ball on 2013-05-23
You don't. You want 'Automatic (DHCP)' and not 'Manual'. Was just checking.

Okay, I just had a look at the router. Get to the router configuration page (put the router's IP address into the address bar of Firefox and hit enter) and check to see if you have wireless N mode off or on.

I'm no expert on this but throwing in some ideas and as everything else seems to be okay, N seems a logical issue (as it can be often).

---

