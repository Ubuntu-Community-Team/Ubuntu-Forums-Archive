---
title: "Wi-fi dead?"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by ownasaur on 2011-06-18
Hello,

I'm having trouble with my Wi-fi connection. The machine in question is a Gateway P-6831 FX. 

I recently installed 11.04 (replacing 10.04) and was browsing/downloading software I needed when suddenly the wireless stopped working. The wi-fi light also turned off, and it seems I can't get wireless anymore. 

This laptop comes with a Wireless switch, and it's ON. Turning it off makes the blue-tooth icon go away, once ON the icon returns but no wi-fi whatsoever.

I ran the following: "sudo lshw -html > your-file-name.html" and the wi-fi card is detected but outlined in pink.

Screenshot here [http://img811.imageshack.us/img811/8922/screenshoths.png](http://img811.imageshack.us/img811/8922/screenshoths.png)

id:network
                   description: Wireless interface                 product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection                 vendor: Intel Corporation                 physical id: 0
                 bus info: pci@0000:02:00.0
                 logical name: wlan0
                 version: 61                 serial: 00:1d:e0:8b:52:ab                 width: 64 bits                 clock: 33MHz                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                  configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn                 resources: irq:48 memory:f4000000-f4001fff


Wi-fi won't work in windows either. Does this mean the wi-fi card is fried? Or is there something else wrong? Any help would be greatly appreciated!

Posting with a wired connection :(

---

### Post by ownasaur on 2011-06-18
Seems I forgot to RTFM...

Gateway P6831 FX


02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

$ sudo lshw -C network
[sudo] password for : 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:8b:52:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:f4000000-f4001fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:72:1c:6b:8a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:4000(size=256) memory:f4200000-f4200fff memory:c0400000-c041ffff

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down


$ lsb_release -d
Description:    Ubuntu 11.04


$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by superduperlinuxperson on 2011-06-18
$ sudo lshw -C network
[sudo] password for : 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       
the DISABLED part is your problem. all you need to do is this (in terminal):
sudo NetworkManager
it will then tell its pid, then type in this (replace pid with what ti told you):
sudo kill pid
sudo NetworkManager
go to the network icon and check enable wireless

hope this helps!

---

### Post by ownasaur on 2011-06-19
> **superduperlinuxperson said:**
> $ sudo lshw -C network
[sudo] password for : 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       
the DISABLED part is your problem. all you need to do is this (in terminal):
sudo NetworkManager
it will then tell its pid, then type in this (replace pid with what ti told you):
sudo kill pid
sudo NetworkManager
go to the network icon and check enable wireless

hope this helps!


Just tried it, and I saw it restarted the wired connection but there was no change to wifi

[http://img87.imageshack.us/img87/1853/screenshot1znx.png](http://img87.imageshack.us/img87/1853/screenshot1znx.png)

Any more suggestions/ideas?

Thanks

---

### Post by nbound on 2011-06-19
Probably off the mark with this one... but there isnt a second switch for wifi? (incl Fn/Function key + F1,F2,F3,Fx etc.)

---

### Post by ownasaur on 2011-06-19
> **nbound said:**
> Probably off the mark with this one... but there isnt a second switch for wifi? (incl Fn/Function key + F1,F2,F3,Fx etc.)


There is but nothing happens.

---

### Post by ownasaur on 2011-06-20
Well I decided to take a look at the hardware itself by taking out the card and checking the antenna connections, plugged it back in and now it works! 

Thanks for the help!

---

