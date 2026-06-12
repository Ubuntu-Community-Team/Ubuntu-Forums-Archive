---
title: "&quot;sudo lshw -C network&quot; Can't find my wireless device (card)."
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by jlunse on 2010-08-07
I have a wired connection on the motherboard and a also a card for wireless communication.
Wired connection works fine but my plan is now to setup wireless connection too.

I was advised to use this in order to find installed network devices:

***sudo lshw -C network***

Not sure, but I think it only reports details about the wired device. Is that correct?
How could I get ubuntu to also find my wifi-card?

This is the report I get with *sudo lshw -C network*:
[I]  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:13:d4:1b:67:86
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:26 memory:cfefc000-cfefffff ioport:c800(size=256) memory:cfec0000-cfedffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 5
       bus info: pci@0000:03:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
       resources: memory:cfffc000-cfffdfff
[/I]

*****Updated below*****
Also tried this command on my daughters computer who also have two network devices, one wired (works fine in ubuntu) and one wireless connection (not working). This is what's reported by ***"sudo lshw -C network"*** and I can't find any wireless device in this text, or am I missing something?
  [I]*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:54:92:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:df00(size=256) memory:fdeff000-fdeff0ff memory:fdd00000-fdd0ffff(prefetchable)
[/I]

---

### Post by jlunse on 2010-08-07
I found a graphical tool called **lshw-gtk** and installed it using Package Manager.
Then I have to start it using ***sudo lshw-gtk***
(starting it as a ordinary user might not report all information)

Anyway, it seems like it found my wireless card but with a strange error in the end. This is what's reported:

[I]Network controller
/0/100/1e/5


product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890]
vendor: Intersil Corporation [1260]
bus info: pci@0000:03:05.0
version: 01
width: 32 bits
clock: 33MHz
capabilities:
	Power Management,
	PCI capabilities listing
configuration:
	latency: 64
	maxlatency: 28
	mingnt: 10
resources:
	memory: cfffc000-cfffdfff
**[COLOR="Red"]this device hasn't been claimed[/COLOR]**[/I]

What does this error mean?

---

### Post by bkratz on 2010-08-07
See posts 7 and on in thread report

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265)

Maybe it will help

---

### Post by jlunse on 2010-08-07
> **bkratz said:**
> See posts 7 and on in thread report

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/509265)

Maybe it will help
[COLOR="Red"]Does this mean that's there no driver available for this wifi device? Should I give up at this point?[/COLOR]

Anyway, I also investigated this further by using WinXP and found the following information for ***Wireless PCI 802.11b/g adapter WN4201B***:
**Provider**: *PCTEL Inc.*
**Driver Provider**: *Accton*
**Driver Date**: *2004-11-30*
**Driver Version**: *2.0.2.2*

Also found an "inf file" in WinXP called **WN4201B** (*c:\i386\drv\APP270044\src\WN4201B.inf*)
[COLOR="red"]Could I use this "inf file" in Ubuntu?[/COLOR]

---

### Post by jlunse on 2010-08-07
**Note!** This guideline was really useful for installing my wifi driver: 
[Wi-Fi Card Activation Under Ubuntu Linux Using ndisgtk and Windows Drivers]("http://kimbriggs.com/computers/computer-notes/linux-notes/ubuntu-linux-wi-fi-card.file")

[B]Seems like I was lucky and managed to install the windows driver by using the following steps:
[/B]
1. Install [ndiswrapper]("http://en.wikipedia.org/wiki/NDISwrapper") using Package Manager.

2. Install [ndisgtk]("http://en.wikipedia.org/wiki/Ndisgtk#Graphical_frontends") using Package Manager.

3. Install lshw-gtk using Package Manager.

4. Copied the WinXP folder (c:\i386\drv\APP270044\src) with the wireless driver to Ubuntu.

5. ***sudo ndisgtk*** and installed the driver by selecting the "inf-file": **WN4201B.inf**

6. ***sudo lshw-gtk***

7. Navigate to the PCI adapter and it now shows the following information and _without_ the ugly "this device hasn't been claimed" error:
[I][COLOR="RoyalBlue"]product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890]
vendor: Intersil Corporation [1260]
bus info: pci@0000:03:05.0
logical name: wlan0
version: 01
serial: 00:12:bf:0b:1b:68
width: 32 bits
clock: 33MHz
capabilities:
	Power Management,
	bus mastering,
	PCI capabilities listing,
	ethernet,
	Physical interface,
	Wireless-LAN
configuration:
	broadcast: yes
	driver: ndiswrapper+wn4201b
	driverversion: 1.55+Accton,11/30/2004, 2.0.2.2
	ip: 192.168.1.8
	latency: 56
	link: yes
	maxlatency: 28
	mingnt: 10
	multicast: yes
	wireless: IEEE 802.11g
resources:
	irq: 17
	memory: cfffc000-cfffdfff
[/COLOR][/I]

---

### Post by jlunse on 2010-08-07
Also, configuration of the Wireless Network was successful and I describe it in this thread:

[What are the first basic steps to setup a wireless connection?]("http://ubuntuforums.org/showthread.php?t=1547859")

---

### Post by bkratz on 2010-08-07
Sorry was out, post 9 gives the details of what I wanted to show you, but it looks like you did it fine without it.

You might go to the thread tools and mark as solved in case it helps someone else.

---

### Post by jlunse on 2010-08-08
> **bkratz said:**
> Sorry was out, post 9 gives the details of what I wanted to show you, but it looks like you did it fine without it.


No problem:) Your information is good and I think understand now. An adapter's driver could be installed in two different ways in ubuntu and lubuntu:

[LIST=1]
[*][COLOR="Red"]Using Window XP driver:[/COLOR] **Installed by using Ubuntu's [B]ndiswrapper** and with the windows driver (*.inf file) as described above[/B] (This solved my problem in lubuntu 10.04).
**Note!** Switching between wired/wireless requires a reboot.

[*][COLOR="red"]Using Linux driver: [/COLOR]**Installed by using linux-firmware-nonfree-1.6.** (I also tested this for the same wifi adapter in ubuntu 10.04 and it was also successful).
This works better for me since it seamlessly switches between wired/wireless without having to reboot.
[/LIST]

If non of the above works, then I think you have to replace the physical adapter/device with one having a commercial linux driver.

---

