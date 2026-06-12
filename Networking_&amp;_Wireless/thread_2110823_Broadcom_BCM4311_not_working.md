---
title: "Broadcom BCM4311 not working"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by Cmarrero75 on 2013-01-31
Ubuntu 12.10


Lenovo 3000 N100


```
PCI (sysfs)  
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0000000-d0003fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:d2:89:b3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.7 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:2000(size=256) memory:d0100000-d01000ff
chris@chris-3000-N100:~$ 
chris@chris-3000-N100:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
chris@chris-3000-N100:~$ uname -r
3.5.0-22-generic
chris@chris-3000-N100:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by bkratz on 2013-01-31
Hook up an ethernet cable and this usually gets the job done for the bcm4311 (in 12.10)-

sudo apt-get update 
sudo apt-get install linux-firmware-nonfree 
sudo modprobe -r b43 && sudo modprobe b43

---

### Post by Cmarrero75 on 2013-01-31
rebooting now.. but this has seem to work.. THANK YOU!!!! ):P

---

### Post by Cmarrero75 on 2013-01-31
so it worked up until the reboot. but I got a crash reported. I am not sure if some update undid what I had just done.

---

### Post by Cmarrero75 on 2013-01-31
I repeated the last command ((sudo modprobe -r b43 && sudo modprobe b43)) and it turned it on again.  it wouldn't be the worst thing in the world if I have to turn it on like that every time.

---

### Post by bkratz on 2013-01-31
> **Cmarrero75 said:**
> I repeated the last command ((sudo modprobe -r b43 && sudo modprobe b43)) and it turned it on again.  it wouldn't be the worst thing in the world if I have to turn it on like that every time.



Let's see if we can make it better---this should cause it to load the correct module at boot time (which doesn't seem to be happening)

```
sudo su
echo b43 >> /etc/modules
exit

```

---

### Post by Cmarrero75 on 2013-01-31
I am thinking that this is solved. I am going to reboot this a couple times, to be sure.. it's not locking up and doing everything people well. 

THANK YOU THANK you.

---

### Post by bkratz on 2013-02-01
> **Cmarrero75 said:**
> I am thinking that this is solved. I am going to reboot this a couple times, to be sure.. it's not locking up and doing everything people well. 

THANK YOU THANK you.


Glad you got it,  enjoy!

---

