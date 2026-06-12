---
title: "NetGear USB 300 [WNA3100]"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by ciaopaulo on 2011-04-18
Hi Guys,

Can anyone help me get this usb wireless network dongle going before I take it back and get a Belkin one?

It works fine under WIn7.

I've tried the following already:

install via ndisgtk

         Driver is installed OK but there's nothing actually connecting in network manager

Install via ndiswrapper

         Same as above (expected really)

         Eg:

```
paulo@paulo-desktop:~$ ndiswrapper -l
bcmwlhigh6 : driver installed
device (0846:9020) present

```I installed the broadcom package "bcmwl-kernel-source" from SPM.

I installed the "firmware-b43-lpphy-installer" package

I've tried power cycling between updates, although this is just wishful thinking that the fairies will come and visit between the computer being off and back on again.

Here's the usual useful data:

```
paulo@paulo-desktop:~$ lsusb
Bus 009 Device 002: ID 046d:0804 Logitech, Inc. Webcam C250
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 03f0:0004 Hewlett-Packard DeskJet 895c
Bus 003 Device 002: ID 046d:c529 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 015: ID 07d1:3c09 D-Link System DWA-140 RangeBooster N Adapter(rev.B1) [Ralink RT2870]
Bus 002 Device 002: ID 0846:9020 NetGear, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
paulo@paulo-desktop:~$ 

``````
paulo@paulo-desktop:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:91:54:6f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:47 ioport:ce00(size=256) memory:fbcff000-fbcfffff memory:fbcf8000-fbcfbfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5a:09:8c:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.100 multicast=yes wireless=Ralink STA
```

Short of doing a recompile of ndiswrapper [as seems to be suggested by sourceforge]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100"), I'm at a loss. And from what I've read here no one else has needed to do that.

Will it be easier if I just take it back and get a Belkin one?

---

### Post by ciaopaulo on 2011-04-23
So yeah....

I took it back and got a Belkin.

---

