---
title: "Getting network-manager to work on boot"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by Stew822 on 2012-07-27
Hello everybody,

I have a new (second hand) PC that I've installed a minimal version of ubuntu 12(.04? The latest, anyway) on. The original drivers [I think they were ath5k] weren't working for wireless connections (no encrpytion) so I tried following a guide to installing the wg133v3 ndiswrapper "solution." Turns out I seem to have a different networking card than the NetGear Wireless-G PCE adaptor (WG311V3) that the box states - from lspci -nn:
```
03:06.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)

```

So. I then tried installing the MadWiFi drivers using this guide over here: [http://pharos.ece.utexas.edu/wiki/index.php/How_to_Install_MadWiFi_Wireless_Drivers_on_Ubuntu_10.04](http://pharos.ece.utexas.edu/wiki/index.php/How_to_Install_MadWiFi_Wireless_Drivers_on_Ubuntu_10.04)

Well. WELL. I followed all the directions, but somehow (I have no idea how) I've ended up with a blank /etc/modules and a blank /etc/network/interfaces.

The network loading thing at boot hangs, then tells me it's going to wait 60 seconds for the network to configure itself. I figure this is a problem with the blank files.

Here's some outputs of commands I've found around the web:

sudo lshw -class network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:11:80:08
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:de00(size=256) memory:fdbff000-fdbfffff memory:fdbe0000-fdbeffff memory:fdb00000-fdb0ffff
  *-network
       description: Wireless interface
       product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 01
       serial: 00:25:86:be:60:af
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-27-generic firmware=N/A ip=192.168.1.2 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:fdde0000-fddeffff

```

ndiswrapper -l
```
wg311v3 : driver installed
	device (168C:001A) present (alternate driver: ath5k)

```
(I tried installing some 64bit drivers I found when I thought I had the wg311v3)

So when I finally get into my custom session (which runs nm-applet), nm-applet says that no network manager is running. So I run "sudo start network-manager" and then both the wireless and wired connections work fine.

Does anyone know how I can make it so the boot doesn't hang, and the network manager automatically starts? I did try to do "start network-manager" in the file that contains all the apps for the custom desktop, but it needs root privlidegs (plus there's still the hanging at boot problem).

Does anyone have any ideas, or can anyone point me to an article that might help?

Thanks

---

### Post by Stew822 on 2012-07-28
GOOD NEWS, EVERYONE!!!

I fixed it.

I opened /etc/udev/rules.d/70-persistent-net.rules and saw that there were two listing of the wireless card - I started the Network Manager, had a looky-see of which driver was running (ath5k) and so deleted the ath_pci version of the listing of the wireless card.

Yay. :D

---

