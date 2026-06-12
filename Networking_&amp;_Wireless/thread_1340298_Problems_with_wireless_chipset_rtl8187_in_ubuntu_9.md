---
title: "Problems with wireless chipset rtl8187 in ubuntu 9.10"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by peprex on 2009-11-28
Hi everyone,

I have recently installed the 9.10 ubuntu version, but have problems recognizing my wirless usb device. First I take a look to the lsusb output, here it comes:

Bus 002 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

Then I start getting the windows xp driver from the original cd and get to work with ndiswrapper, here are my steps:

>ndiswrapper -i Netrtuw.inf 
>ndiswrapper -l

netrtuw : driver installed
    device (0BDA:8187) present (alternate driver: rtl8187)

Oh!, then I'll try to remove that alternate driver ...

>modprobe -r rtl8187
>rmmod rtl8187
>lsmod | grep rtl8187
> lsmod | grep *8187

The last two, returned nothing, that looks fine.

>depmod -a
>modprobe ndiswrapper
>dmesg

usbcore: deregistering interface driver rtl8187
[  425.296016] usb 2-3: reset high speed USB device using ehci_hcd and address 2
[  539.457943] Disabling lock debugging due to kernel taint
[  539.462285] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  539.580015] usb 2-3: reset high speed USB device using ehci_hcd and address 2
[  539.715732] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,06/26/2008,5.1314.0626.2009) loaded
[  542.096799] wlan0: ethernet device 00:1a:ef:09:0c:b6 using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8187.F.conf
[  542.096823] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  542.096874] usbcore: registered new interface driver ndiswrapper
[  542.104261] **ADDRCONF(NETDEV_UP): wlan0: link is not ready**

>ndiswrapper -m
>echo "ndiswrapper.conf" | tee -a /etc/modules
>echo "blacklist rtl8187" | tee -a /etc/modprobe.d/blacklist.conf 
>echo "blacklist r8187" | tee -a /etc/modprobe.d/blacklist.conf 
>lshw -C network

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 90:e6:ba:24:56:48
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:d800(size=256) memory:feaff000-feafffff memory:f8ef0000-f8efffff(prefetchable) memory:feac0000-feadffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:ef:09:0c:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netrtuw driverversion=1.55+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g

>shutdown -r 0

OK! At this point I start the system and ... :

**dmesg after _>ifconfig wlan0 up _**

wlan0: ethernet device 00:1a:ef:09:0c:b6 using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8187.F.conf
[   57.544688] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   57.544734] usbcore: registered new interface driver ndiswrapper
**[   57.545101] ADDRCONF(NETDEV_UP): wlan0: link is not ready**

ndiswrapper -l still returns:
netrtuw : driver installed
    device (0BDA:8187) present (alternate driver: rtl8187)

Finally The wireless icon in the Desktop appears to be "disconnected" and there's no way to bring it up, there's even no option to connect or scan wirless networks. And by "connect to a hidden network" option I get nothing ....

Any ideas, please help, I don't know how to continue !
P

---

