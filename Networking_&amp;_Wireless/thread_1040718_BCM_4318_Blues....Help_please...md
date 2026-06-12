---
title: "BCM 4318 Blues....Help please.."
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by Rinai on 2009-01-15
Ok, I have followed every tutorial I could find on installing the bcm 4318 airforce 54g card with ndiswrapper and even went as far as doing one of them that had a shell file to do it for me with no results.

I wanted to use the driver that is in the restricted drivers that is native but have no way of getting an ethernet cable so it can download.

Is there any way I can get a direct download of it on my windows partition and stick it on my Flash drive and install it on Ubuntu partition?


Any help is appreciated.

-Dalton Matheson

---

### Post by superprash2003 on 2009-01-16
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) .. choose your ubuntu version..and it gives commands like wget ... with a link to the drivers.. download that seperately and install

---

### Post by Rinai on 2009-01-16
> **superprash2003 said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) .. choose your ubuntu version..and it gives commands like wget ... with a link to the drivers.. download that seperately and install

Aye im using Intrepid Ibex which isnt down there..

I did lshw -C network and got
```

dalton@serverworkstation:~$ lshw -C network
WARNING: 
you should run this program as super-user.
  
*-network               
       
description: Ethernet interface
       
product: 82562V-2 10/100 Network Connection
      
 vendor: Intel Corporation
       
physical id: 19
       
bus info: pci@0000:00:19.0
       
logical name: eth0
       
version: 02
       
serial: 00:1d:09:8e:63:ed
       
width: 32 bits
       
clock: 33MHz
       
capabilities: bus_master cap_list ethernet physical
     
configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 module=e1000e 
multicast=yes
  *-network
  

description: Network controller
      
 product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
      
 vendor: Broadcom Corporation
      
 physical id: 0
      
 bus info: pci@0000:02:00.0
       
version: 02
      
 width: 32 bits
      
 clock: 33MHz
     
  capabilities: bus_master
       
configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       
```

So it recognizes the card but its trying to use a pci-bridge as the driver and it isnt recognized as wlan0 for some reason

---

### Post by Ayuthia on 2009-01-16
You can try this link if you have a 4318 card:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

It provides instructions on what to download to allow you to use the native b43 module.

---

### Post by acimmarusti on 2009-01-22
This worked well for me:

[http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318](http://ubuntuforums.org/showthread.php?t=1047297&highlight=4318)

Let me know if it works for ya

---

### Post by sampbar on 2009-01-24
Or... if you wish to use ndiswrapper you could try my guide: [http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html]("http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html")

If you need any more help just reply to this thread!

Samuel

---

