---
title: "Broadcom 4322 Problem Wifi, Please Help"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2011-05-08
hi, I have a broadcom 4322 and haven't successfully got it working yet. the hard drive failed in this laptop and i took it out. i am using a bootable flash drive with ubuntu on it installed. not the live edition. i am trying to find out if somehow since the hard drive is not in the laptop, if that could have anything to do with runnin off the usb flash drive it boots? i have a wired connection using the 8gb flash drive. since there are drivers for usb wifi devices which i know are different, is it possible that the wifi card is looking somewhere else instead of the usb port?

lsusb (i know i have a flash drive not a wifi usb card but this commands still shows this and ndiswrapper -l doesn't show nothing but blank next line to type on. i have tried alot of stuff

  *-network DISABLED      
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:39:81:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:cc:3a:30:55
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.117 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:a000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff


Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



* i notice how the location of the wifi is eth1, is that right or should that say wlan?
bit newer to linux so just bear with me guys

---

### Post by westie457 on 2011-05-09
Hello, installing Ubuntu to an external hard drive or a Flash drive should not make any difference to the networking. T he only idea that I have is a problem with the wireless driver. Have you clicked on the 'additional drivers' icon to activate the Broadcom driver?

---

### Post by slixz85 on 2011-05-10
yeah i seen where it said disabled too but it is activated. 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

i have blacklisted b43 b43 legacy and ssb as broadcom website also says too

---

### Post by josephmills on 2011-05-10
please see post number 44 thanks [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by westie457 on 2011-05-11
> **josephmills said:**
> please see post number 44 thanks [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)
Hi I stumbled across this particular thread and had a look at the the link you posted.

It showed me in detail what I had fixed previously by trial and error.

I have posted your link in the original thread I had looked at here

[http://ubuntuforums.org/showthread.php?p=10798975#post10798975](http://ubuntuforums.org/showthread.php?p=10798975#post10798975)

so others may see it.

A big THANK YOU to 'josephmills'

---

### Post by slixz85 on 2011-05-11
yes it works awesome. and thanks joseph. a simple rfkill command was my problem. it has a soft block on it.

unfortunately i have a minor problem, sometimes after i reboot a few times the wifi is working but i had to put the rfkill unblock all command in a couple times already. so it is just not saving what i did correctly for some reason.

---

### Post by josephmills on 2011-05-11
> **slixz85 said:**
> yes it works awesome. and thanks joseph. a simple rfkill command was my problem. it has a soft block on it.

unfortunately i have a minor problem, sometimes after i reboot a few times the wifi is working but i had to put the rfkill unblock all command in a couple times already. so it is just not saving what i did correctly for some reason.

watch the dmesg when this happens and then post the error here thanks

---

