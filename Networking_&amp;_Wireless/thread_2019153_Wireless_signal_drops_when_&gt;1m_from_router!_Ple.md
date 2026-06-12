---
title: "Wireless signal drops when &gt;1m from router! Please help!"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by Pipps on 2012-07-07
Wifi works when I am within 1 meter of the router, but it drops as soon as I move to the other side of the room. What could be the problem?

I have a new installation of Ubuntu 12.04 on a Dell Netbook, and a new Netgear DGN1000SP modem router.

The same problem exists, regardless of whether I use WEP security or no wireless security protocol.

By contrast, my Android smartphone gets perfect wireless signal all around the house. This seems to confirm that it is not a router issue.

Also, with previous modem routers and previous versions of Ubuntu, I have received perfect wireless signal all around the house with this same netbook.

Please help.

---

### Post by Pipps on 2012-07-07
Is this more likely to be a problem with Ubuntu 12 specifically, or with the new modem instead? 

Should I try using any different security protocol?

---

### Post by Pipps on 2012-07-08
I can confirm, that my other laptop (from the office) which is running Windows Vista Enterprise, connects to the new Netgear modem router immediately with no problems.

It gets full wifi signal anywhere within the house.

Why does my Ubuntu netbook not do this since 12.04?

---

### Post by 23senick on 2012-07-08
When I've had this type of problem it's the wireless driver.  Do you know what type of wireless hardware your machine has? If not open a terminal and type 

                                  [FONT=DejaVu Sans Mono][SIZE=2]lshw -C network[/SIZE][/FONT]  

Wait a bit and it will tell you what type you have, and what driver it's using.  Broadcom (especially 4313) cause problems but they seem fixable!  Once you know that, search this forum for that specific model, there are often step-by-step solutions.  

I went through problems with this on 11.10.  When I did a fresh install of 12.04, I let it do updates while installing and it seemed to automatically activate the proprietary drivers.

---

### Post by Pipps on 2012-07-09
Thanks for the help.

The command returned the following:

```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 01
       serial: 70:1a:04:6d:7d:73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.4 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:f2:9e:9a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff

```

However, this problem arose after the same Broadcom driver installation was already working perfectly with the cable modem router at my previous house.

Since receiving this new modem router, all my other wireless devices still work fine - but not the Ubuntu 12,04 installation. Or the 11.10 installation either now.

What could be the problem?

EDIT: The latest Broadcom drivers are installed now on 11.10 - and the problem is still exactly the same! :(

---

### Post by andyhelloween on 2012-07-09
Hello there,
 
Ok.. I had the same problem with an HP DV6 7032, although the specific wireless was BCM4313 instead of BCM4312. Wireless was working constantly at 70%, which might be the same as < 1M from the access point.
 
The solution I found is [here]("http://ubuntuforums.org/showpost.php?p=12016636&postcount=7"). Before that, I also found trouble trying to connect wirelessly. The issue was the driver itself, and a workaround was to change the channel on the router. More information [here]("http://ubuntuforums.org/showpost.php?p=12011479&postcount=5").
 
Also, check this [thread]("http://ubuntuforums.org/showthread.php?t=1604868") if none of the above works for you.
 
Cheers!

---

### Post by 23senick on 2012-07-10
It's worth trying different drivers for your Broadcom wireless - try searching the forum for  BCM4312. I think the how-to instructions will be different to mine (4313).

---

### Post by Pipps on 2012-07-11
I have tried the low-power BCM4312 driver installation, following the advice at [this]("http://ubuntuforums.org/showpost.php?p=12009028&postcount=584") thread.

In fact, the terminal returned the command saying that the low-power driver had in fact been replaced by 'firmware-b43-lpphy-installer'.

It works perfectly at all ranges! Thank you :D

---

