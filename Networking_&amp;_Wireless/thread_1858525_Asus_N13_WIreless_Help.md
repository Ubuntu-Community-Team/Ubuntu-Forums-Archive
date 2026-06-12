---
title: "Asus N13 WIreless Help"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by SauceJohnson on 2011-10-12
I've been trying to get my Asus N13 adapter to work for a couple weeks now. I'm trying to get it to work on BT5. The BT5 forums are useless and takes months to get a forum post approved. I've already read the post on here of the guy who also had a problem with the Asus N13, but he ran into some other problems that don't help me. I know in the commands that I'm suppose to leave out "sudo". When I type in lsmod | grep -e rt2 -e rt3 and then lsusb, I can see the computer recognizes it. Another problem is, I'm a noob, and I can't install the rt3070 drive. I have the 2800 on the black list also. But I need this because I'm taking a whole class on Unix/Linux, but the only thing we've been doing are the basics; documents, scripts, etc.. Any help for once would be awesome. :D

---

### Post by josephmills on 2011-10-12
HI there and welcome to Ubuntu forums :) 

could we please see alittle more info about your machine please open terminal (ctrl+alt+t) then type in 
```

lspci -nn
lsmod
lsusb
rfkill list all 
cat /etc/modprobe.d/blacklist.conf
lshw -c network 

```

thanks and welcome to ubuntu forums again

---

### Post by SauceJohnson on 2011-10-12
Alright on the last command I got .. 

root@bt:~# lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:d3100000-d3103fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c1
       serial: c8:0a:a9:a4:35:b4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.107 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:42 memory:d3000000-d303ffff ioport:6000(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan1
       serial: f4:6d:04:b1:fc:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=2.6.38 firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bgn

---

### Post by josephmills on 2011-10-12
um..... that is not all the commands that I asked for.... If you want help you might want to think about doing what the person is asking you to and not what you think is right. pretty hard for us to answer you when you wont answer us!

---

### Post by chili555 on 2011-10-12
Joseph--

Please see PM.

---

