---
title: "Toshiba Satellite L655 wireless enable missing"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by neo1786 on 2011-06-24
Hi, I went through several posts for making the Toshiba wireless working. None of them seemed to work.
The Fn+F8 key is also not working, as with many other ppl
 here is output for sudo lshw -C network
```

neeraj@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz *-network UNCLAIMED
                description: Network controller
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: ioport:7000(size=256) memory:f3100000-f3103fff
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:f3100000-f3103fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c1
       serial: 60:eb:69:f8:ce:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.1.129 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:f3000000-f303ffff ioport:6000(size=128)


```

I also tried the ndiswrapper with xp drivers but somethng went wrong n ndiswrapper didnt compile only

---

### Post by neo1786 on 2011-06-27
Hi, I looked at a lot of suggestions on ubuntuforums....seems like many ppl have this problem.
Most fixes seem to work. In my case, none of them worked. However this link helped me solve my problems

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek)

Now i can connect properly to wifi networks and the connection does not go off intermitently

all you have to do is:

```

sudo add-apt-repository [B]ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install [/B]                 rtl8192ce-dkms               
sudo reboot

```

---

### Post by BeantowneS on 2012-06-03
Had the same problem here and the suggestion worked great.....thank you very much.

---

### Post by Elfy on 2012-06-03
Old thread closed.

---

