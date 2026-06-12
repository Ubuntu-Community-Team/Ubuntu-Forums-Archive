---
title: "Wireless card can't see wireless signals"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by DividedSky on 2011-04-27
Hi, recently installed ubuntu netbook remix 10.10.  At first wireless card couldnt be enabled, but using some rfkill unblock command line, it started working and was enabled.  The wireless card then worked and I started using it for the internet, but only lasted until i restarted.  now the wirelss card does not pick up any signals.  i uninstalled all 4 b43 drivers and only sta are active.

This is my lspci -nn:

amymc48@amymc48-HP-Mini-110-1100:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)


nothing came up for dmesg | grep b43 and lsmod | grep b43

thanks!

---

### Post by josephmills on 2011-04-27
hi there could we please see a 
```

uname -r

```
thanks

---

### Post by garvinrick4 on 2011-04-27
BCM-4312 can be installed in Synaptics, give post 2 his answer.

---

### Post by DividedSky on 2011-04-27
> **josephmills said:**
> hi there could we please see a 
```

uname -r

```
thanks

2.6.35-28-generic

thanks for helping:D

---

### Post by DividedSky on 2011-04-27
[IMG]http://i.imgur.com/PPgp0.png[/IMG]

this is my synaptics

---

### Post by josephmills on 2011-04-27
could we please see a ```
rfkill list 
``` thanks

---

### Post by DividedSky on 2011-04-27
> **josephmills said:**
> could we please see a ```
rfkill list 
``` thanks

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by josephmills on 2011-04-27
please take out all ipaddress and hw address  ```
sudo lshw -c Network
```also that looks like 11.04 to me

---

### Post by DividedSky on 2011-04-27
> **josephmills said:**
> please take out all ipaddress and hw address  ```
sudo lshw -c Network
```also that looks like 11.04 to me

PCI (sysfs)  

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:26:55:b9:90:4f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=10.206.139.60 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:febc0000-febfffff ioport:ec80(size=128)

---

### Post by DividedSky on 2011-04-27
how do i take out all ip addresss and hw address?

the iso file i used to make a usb installer is called "ubuntu-10.10-netbook-i386"

---

### Post by josephmills on 2011-04-27
could we please see a 
```

lsb_release -d

```

---

### Post by DividedSky on 2011-04-27
> **josephmills said:**
> could we please see a 
```

lsb_release -d

```

Description:	Ubuntu 10.10

---

### Post by josephmills on 2011-04-27
i would like to see the same

---

### Post by DividedSky on 2011-04-27
> **josephmills said:**
> i would like to see the same

okay, uninstalling broadcom-sta-common
broadcom-sta-source
bcm5700 source

brb

---

### Post by DividedSky on 2011-04-27
this is now me:

[IMG]http://i.imgur.com/ON9cX.png[/IMG]

---

### Post by josephmills on 2011-04-27
In synaptic go to **settings-->repos** then look at pics are they all ticked if you have to tick them then do so. then press the reload button in synaptic then close it. then press 
[b]
ctrl+alt+t
[/b]
then enter 
```

sudo apt-get update

```
then
```

sudo apt-get upgrade 

```
then
```

sudo reboot

```
after rebooting go to
[b]
system-->admin-->additional drivers 
[/b]
can you activate the driver ?

---

### Post by DividedSky on 2011-04-28
> **josephmills said:**
> In synaptic go to **settings-->repos** then look at pics are they all ticked if you have to tick them then do so. then press the reload button in synaptic then close it. then press 
[b]
ctrl+alt+t
[/b]
then enter 
```

sudo apt-get update

```
then
```

sudo apt-get upgrade 

```
then
```

sudo reboot

```
after rebooting go to
[b]
system-->admin-->additional drivers 
[/b]
can you activate the driver ?

hey thanks for the help but im just going to give up on this ubuntu business. going to give jodicloud a whirl

---

