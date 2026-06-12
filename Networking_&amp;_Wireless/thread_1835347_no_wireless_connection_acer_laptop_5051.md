---
title: "no wireless connection acer laptop 5051"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by FrankBuBu on 2011-08-29
Hi there,

I have installed Ubuntu 11.04, but I can't use my wireless router, no wireless connections I think the reason is that the wireless interface is disabled. How can I get the device working? I use an Acer laptop Aspire 5051AWXMi (AMD processor).

I tried the command sudo lshw -C network
It sais that the wireless interface is DISABLED. I learned that it means the device is not on. So I used the network button on my laptop. But... still DISABLED when I use sudo lshw -C network again.
When I try to wake up the wireless interface like this:

sudo ip link set wlan0 up 
It sais:
RTNETLINK answers: No such file or directory 
Below you can read the results of the commands
lspci
sudo lshw -C network
iwconfig

Hope you can help me!

PS: I’d rather not use ndiswrapper (voor windows driver), cause Ubuntu recognizes the hardware (Broadcom 802.11g Wireless LAN Controller). Otherwise it would have said UNCLAIMED or something like that with the command sudo lshw -C network, I guess?


Command used: lspci
Result:
..
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
08:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

Command use:sudo lshw -C network 
Result:

  *-network:0              
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 2 
       bus info: pci@0000:08:02.0 
       logical name: eth0 
       version: 10 
       serial: 00:16:36:94:ab:31 
       size: 10Mbit/s 
       capacity: 100Mbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s 
       resources: irq:20 ioport:a000(size=256) memory:b0203c00-b0203cff 
  *-network:1 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 4 
       bus info: pci@0000:08:04.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 
       resources: irq:21 memory:b0200000-b0201fff 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:16:cf:91:58:2d 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

Command used: iwconfig
Result:

lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off

---

### Post by praseodym on 2011-08-29
Hi,

you have to install the firmware for this device:

```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Check:

```
iwconfig
rfkill list
lsmod
dmesg | grep b43
```

---

### Post by FrankBuBu on 2011-08-29
dear praseodym, it worked! Thanx a lot!:guitar:

---

### Post by mebunto on 2011-10-27
that also worked on my BCM4306 wireless. Thanks.

---

