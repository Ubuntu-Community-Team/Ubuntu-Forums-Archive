---
title: "Need to restart to connect to wifi ubuntu 12.04"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by spirals on 2013-01-07
I'm pretty new to linux.. I'm on ubuntu 12.04 and if I disconnect or am disconnected I need to restart the computer to get the wifi connection working again.

I'm using an external wireless adapter at the moment, but do have an internal wifi just cannot get it working- installing drivers made my wifi more unstable and I ended up reinstalling ubuntu to fix it.

Only just learning command line so please be easy on me.  Its a big shock coming to linux after knowing your way around windows and mac!  But I'm liking it so far so would like to get this sorted please so any help would be greatly appreciated.

---

### Post by Bucky Ball on 2013-01-07
*Thread moved to **Networking & Wireless***

Welcome to the forums.

This is easy enough. Open a terminal and copy/paste this:

```
sudo lshw -C network
```... then paste the output back here. 

With the USB dongle plugged in, run this:

```
lsusb
```... and post back. That will give us more info about both cards.

---

### Post by spirals on 2013-01-07
sudo lshw -C network

spirals@laura:~$ sudo lshw -C network
[sudo] password for spirals: 
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: NVIDIA Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:8e:cc:14
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:20 memory:f2487000-f2487fff ioport:30e0(size=8)
  *-network
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 03
       serial: 00:1a:73:90:26:91
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:f2000000-f2003fff memory:f2500000-f25fffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan1
       serial: 00:e0:4c:03:8d:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-35-generic firmware=N/A ip=192.168.0.5 link=yes multicast=yes wireless=IEEE 802.11bgn


lsusb

spirals@laura:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b023 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]

---

### Post by Bucky Ball on 2013-01-07
description: Wireless interface
       product: BCM4321 802.11a/b/g/n

That is the internal card and should work out of the box. You might need to switch off wireless N. That can be problematic and may be why it keeps dropping out (ditto for the USB Realtek RTL8188CUS 802.11n). 

What exactly does the internal card do when it is being unstable? Slow down, drop out? What exactly did you install to get it running (as that doesn't appear to be the correct one listed in your output? What do you have in 'Additional Drivers'? Might be an idea to take the dongle out and try to get the internal Broadcom one stable.

You could try going to Software Centre or Synaptic and installing:

b43-fwcutter
firmware-b43-installer

... then restart. You may need to uninstall whatever else you installed first, though.

---

### Post by spirals on 2013-01-08
Ok..  so after you said it should be working out of the box I reinstalled ubuntu (was a new installation so didn't delete much).

Ethernet (sorry forgot to mention that) and wifi were not working just as before..  so after trying to get drivers working without internet (no linux headers so that was beyond me right now).

I had to reinsert the external wifi card.. tried different wl driver (which is what my research told me I needed- altho I might be wrong) types- removing the old ones as I did and of course restarting.

Nothing worked.  So just to make sure I had not messed anything up I reinstalled ubuntu 12.04..

I'm back to my old situation- having to restart or sometimes reinserting the wifi adapter if I lose connection or disconnect myself.

I would be happy just to get the wifi adapter working..  the guy who sold me the computer said he couldn't get the wifi card to work in windows either but the adapter worked fine.

---

### Post by spirals on 2013-01-08
how do i switch off 'wireless n' and what is it?

---

### Post by praseodym on 2013-01-08
Hi,

please first check the chipset of the card:

```
lspci -nnk | grep -iA2 net #this is one line!
```
If you did not install the "Broadcom-STA" driver via "Additional drivers", try to install the package "b43-fwcutter" and "firmware-b43-installer" via the software-center, as Bucky Ball already mentioned. This will cause no harm.

---

### Post by Bucky Ball on 2013-01-08
If the internal card didn't work in Win either I would be thinking cooked hardware and perhaps you're right, stick to the external dongle (although the internal card does show up fine, just had wrong driver).

You might try having a peek and making sure the antennae wires are correctly attached to it I guess.

---

### Post by spirals on 2013-01-10
OK update- From my research I've found out it might be due to an internal problem with the type of HP Pavillion (dv9000)  turns out lots of these had wifi card problems..

I've disabled the internal wifi card and the wifi from the adapter works great now..  

Just working out how to mark this thread solved.. bear with me ;)

Thanks for your help :-)

---

### Post by Bucky Ball on 2013-01-10
All good. Glad you got one of them working ...

Good luck and enjoy! ;)

---

