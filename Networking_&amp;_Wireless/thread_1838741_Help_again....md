---
title: "Help again..."
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by piedog98 on 2011-09-04
i just wiped ny computer and installed kubuntu. when i go into networking, it wont even let me click on the wireless tab in the window. tried getting b43 & ndiswrapper. im also a total n00b, so i don't know what to do.
(p.s. i have a 4311 chipset):confused:

---

### Post by praseodym on 2011-09-04
Hi,

do you have a cable connection? Then you have to install the firmware for the b43 module. Ndiswrapper has to be uninstalled completely for that:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo apt-get install b43-fwcutter firmware-b43-installer
```
You system is up-to-date? KDE 4.7 had some problems in the beginning, which obviously were solved with the updates.

---

### Post by piedog98 on 2011-09-04
did that... what next?

---

### Post by IWantFroyo on 2011-09-04
Plug your computer into an ethernet cable, and run this:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by piedog98 on 2011-09-04
already did the:
sudo apt-get install b43-fwcutter firmware-b43-installer

do i restarrt?

---

### Post by praseodym on 2011-09-04
Yes, reboot and show:

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
dmesg | grep b43
sudo iwlist scan
```

---

### Post by wildmanne39 on 2011-09-04
Hi, after you run the command suggest by IWantFroyo if you still have problems run these commands and post the results here please:
```
lspci -nn | grep 0280
```
```
sudo iwlist scan
```
```
dmesg | egrep 'b43|firm'
```
```
lsmod | grep b43
```
```
sudo lshw -C network
```
```
iwconfig
```
Thank you

---

### Post by piedog98 on 2011-09-04
ok. did all of them:

robin@robin-HP-Pavilion-dv6000-RP297UA-ABA:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
robin@robin-HP-Pavilion-dv6000-RP297UA-ABA:~$ sudo iwlist scan
[sudo] password for robin: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

robin@robin-HP-Pavilion-dv6000-RP297UA-ABA:~$ dmesg | egrep 'b43|firm'
robin@robin-HP-Pavilion-dv6000-RP297UA-ABA:~$ lsmod | grep b43
robin@robin-HP-Pavilion-dv6000-RP297UA-ABA:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:d3:b8:ad
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.121 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)
robin@robin-HP-Pavilion-dv6000-RP297UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by wildmanne39 on 2011-09-04
Hi, the firmware and driver are stilling missing, did you have a wired connection when you ran the commands to install the driver and firmware?

---

### Post by piedog98 on 2011-09-04
yes

---

### Post by wildmanne39 on 2011-09-04
Run the commands again and post all the out put here from the terminal please.

Also this command too.
```
lsmod
```
Thank you

---

### Post by piedog98 on 2011-09-04
i entered it twice

---

### Post by wildmanne39 on 2011-09-04
Hi, for all the commands I have given you I need you to run them and post the results here by coping and pasting them, they will help us to find out what the problem is.
Thank you

---

### Post by piedog98 on 2011-09-07
someone help...

---

### Post by praseodym on 2011-09-07
Show the output of

```
lsmod
```
Can you load the driver by hand now:

```
sudo modprobe -v b43
```

---

