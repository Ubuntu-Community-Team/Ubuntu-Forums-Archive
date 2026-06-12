---
title: "After update Ubuntu 11.04 wlan0 disappeared"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by drapeko on 2011-05-29
Hi guys,

Couple of weeks ago I managed to upgrade my system from 10.10 to 11.04 - I had lot's of ugly issues however Wireless worked very well. 

Yesterday I checked the Update Manager, that offered me to update tens of the packages. I decided to update all of them. Right after I update had finished my wireless manager became inadequate however I saw the interface with the help of ```
ifconfig
``` and wifi worked. Once I restarted my computer, wireless card disappeared forever. Now I don't see it with the help of 

```
ifconfig
```or 
```
iwconfig
drapeko-HP:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

```or
```
drapeko-HP:~$ lspci | grep Network
```All is empty.

I tried to install drivers with ndiswrapper (however I did not need  to do it before):
```

drapeko-HP:~$ sudo ndiswrapper -l
netathw : driver installed
netathwx : driver installed

```but it does not recognize the device. 

I also tried to replace prism54 with p54pci in blacklist.conf:

```

# replaced by p54pci
#blacklist prism54
blacklist p54pci

```I have Ubuntu 11.04 installed. My laptop is HP G56 and, apparently, Atheros Wireless Lan.

Any help would very be appreciated!

---

### Post by josephmills on 2011-05-29
hi there I have to go to work soon but could we all see a ```
lspci -nn
``` and a ```
rfkill list all
``` thanks

---

### Post by drapeko on 2011-05-29
Hi Joseph,

output for lscpi -nn 

```


00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)


```Output for rfkill list all is blank

---

### Post by josephmills on 2011-05-29
```
sudo lshw -C network 
``` and ```
lsusb
```thanks

---

### Post by drapeko on 2011-05-30
[FONT=monospace]sudo lshw -C network:[/FONT]

```


PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 64:31:50:5c:47:53
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff


```


lsusb:

```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05c8:0213 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by drapeko on 2011-06-02
still have not found a solution, anyone had the same issue?

---

### Post by edmccann on 2011-06-13
I am having the same problem, although I'm not sure exactly when it started.

Wlan0 is not available with ifconfig or iwconfig.  This (wireless) was working even under 11.04 but I had to reinstall my card's driver.  Now it's not working at all.

ed@greensun:/$ lspci -nn

...
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

---

### Post by zulware on 2011-08-19
i have the problem with this too..
anyone can help??

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 78:ac:c0:47:bf:37
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz

---

### Post by nm_geo on 2011-08-19
> **zulware said:**
> i have the problem with this too..
anyone can help??

  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 78:ac:c0:47:bf:37
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz

Copy and paste this in terminal

```
lspci -nn

```Copy and post results in thread..

---

