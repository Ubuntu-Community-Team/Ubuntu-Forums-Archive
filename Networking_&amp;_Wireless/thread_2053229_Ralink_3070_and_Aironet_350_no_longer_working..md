---
title: "Ralink 3070 and Aironet 350 no longer working."
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by ahil925 on 2012-09-04
I just upgraded from 10.04 to 12.04 and found that Ubuntu is now giving me issues with wireless on my IBM T40.

For my internal Aironet 350 adaptor I'm unable to connect to open access points.  I can see them and attempt to connect but it never actually does.  The access points I'm attempting to connect to were ones I was able to before.

My usb Ralink 3070 adaptor isn't even showing up on the network app.

Both these devices worked previously on 10.04, but after the upgrade I'm now forced to use an ethernet connection.

I've reviewed a few threads on this forum with similar issues, but my attempts to fix this problem have been frustrating to say the least.  I figure its best to start from scratch and just make my own thread.  Thank you all in advance for your help.

---

### Post by ahil925 on 2012-09-05
Just an update,  I attempted the instructions found here: [http://askubuntu.com/questions/148767/help-do-i-install-the-ralink-rt3070-wireless-driver](http://askubuntu.com/questions/148767/help-do-i-install-the-ralink-rt3070-wireless-driver) .

My Ralink still doesn't show up on the network manager. 

I ran ```
sudo lshw -class network
```  here is its output:

ahil925@MobileWeapon:~$ sudo lshw -class network
[sudo] password for ahil925: 
  *-network:0             
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: Cisco Aironet Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 00
       serial: 00:02:8a:dc:43:b5
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom logical wireless ethernet physical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0200000-c0203fff memory:c0400000-c07fffff memory:e8000000-e81fffff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:7e:f0:0a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=172.31.46.90 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:c0204000-c0204fff ioport:8400(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA


I'm guessing I may need to enable the Ralink, but I'm unsure how, if that even what I need to do.  Sidenote, my Aironet is still refusing to access ANY open wifi points.

---

### Post by ahil925 on 2012-09-07
Still having wireless issues...

---

### Post by ahil925 on 2012-09-07
Alright, I followed the instructions I found here: [http://ubuntuforums.org/showpost.php?p=11807030&postcount=1  ]("http://ubuntuforums.org/showpost.php?p=11807030&postcount=1")and it seems to have gotten my Ralink 3070 working.   

Still working on the Aironet 350 issue.
[]("http://ubuntuforums.org/showpost.php?p=11807030&postcount=1")

---

