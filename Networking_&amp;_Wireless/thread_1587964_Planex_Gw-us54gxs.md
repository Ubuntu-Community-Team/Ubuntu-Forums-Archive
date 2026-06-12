---
title: "Planex Gw-us54gxs"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by basilwatson on 2010-10-04
Bus 002 Device 010: ID 2019:5303 PLANEX GW-US54GXS 802.11bg

Hi all 

Sorry but I have no Idea how to get this usb lan adapter working

Ive been hunting the net and this forum , but I am lost ,,, could someone point me in the right direction?

The usb lan is not being recognised , possibly due to the driver 

kind regards Stephen

ps outputs        physical id: 1
       bus info: scsi@8
       logical name: scsi8
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:cf:36:c5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
s@s-desktop:~$ sudo iwconfig
[sudo] password for s: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

s@s-desktop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:45:e7:f1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:b800(size=256) memory:ffdff000-ffdfffff memory:ffdc0000-ffddffff(prefetchable)
  ***-network DISABLED**
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:cf:36:c5:21
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
s@s-desktop:~$

---

### Post by bryanyou on 2010-12-25
A solution(maybe)
[http://blog.goo.ne.jp/saitosatoru/e/ef05d7b3cc10c70d578fa9ecd1f68c73](http://blog.goo.ne.jp/saitosatoru/e/ef05d7b3cc10c70d578fa9ecd1f68c73)

---

