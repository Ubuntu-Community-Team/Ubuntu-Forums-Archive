---
title: "can't detect wireless adapter in backtrack 5"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by mirrorx on 2011-08-03
I am using Belkin USB wireless network adaptor. but,its not showing in backtrack 5.


iwconfig nothing

ifconfig nothing

airmong-ng nothing

I tried to install ndiswrapper, but it got stuck after error

make[1]: Leaving directory `/usr/src/linux-source-2.6.35.8'
make: *** [LINUX] Error 2

---

### Post by josephmills on 2011-08-03
I say go with blackbuntu kde but that is just me. Lets look at that usb a little bit open terminal or konsole and type in ```
lsusb
``` then ```
rfkill list all 
``` then ```
sudo lshw -c network
``` then paste here

---

### Post by mirrorx on 2011-08-03
root@bt:~# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@bt:~# rfkill list all
Can't open RFKILL control device: No such file or directory
root@bt:~# sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0c:29:cc:af:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.35 ip=192.168.44.136 latency=64 link=yes maxlatency=255 mingnt=6 multicast=yes
       resources: irq:19 ioport:2000(size=128) memory:dc400000-dc40ffff

---

### Post by aranger on 2011-09-23
Is the Belkin USB adapter compatible with Backtrack? If it is not you may have to load the drivers, find the chipset the adapter uses, then use modprobe and rmmod commands to unload and reload the driver. Check out [www.wirelesshack.org](www.wirelesshack.org) for cards that work well with backtrack.

---

### Post by skiet078 on 2011-09-29
HI
I m using Vmware 
Do u configure wireless adapter on backtrack 5
I m also using Belkin F5D7050
When i write in the terminal lsusb 
it display belkin but doesnot connect to internet through this belkin device 
Pls Tell me I shall be thankful to u

---

