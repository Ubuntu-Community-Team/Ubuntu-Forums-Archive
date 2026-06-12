---
title: "Newbie Wireless Setup Kubuntu 9.04"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by firestormxvii on 2009-05-31
So here is the problem, I have a box that has never had a Linux distro installed, and I want it to have 9.04. I need it to connect to wireless, however I cannot get it setup. I need to both install the driver for the card (I have the driver, I just don't know where to extract it to) and connect it to the wireless network in my home. Fortunately I do not have any protection on my network so the issues about not being able to connect to hidden and password protected networks does not apply to me. 

All  of the step-by-step instructions that i can find are for older versions of Kubuntu, I am not sure what to do from here. I hope that anyone who can help me, point me in the right direction. From what I have read it seems like there is not a working step-by-step for this latest release, however if there is I have not been able to find it and would love a link.

---

### Post by chili555 on 2009-05-31
Let's start by asking the computer what kind of wireless card you have. Open Applications -> Utilities -> Terminal and type in:```
sudo lshw -C network
```You will receive information about both your wireless and your wired ethernet devices. Please post the wireless data here. If in doubt, post it all.

Next, tell us about the driver package you have. Where did you download it? Are you certain there is no native driver that will drive your wireless? Is it a .tar.gz? What is it's name?

---

### Post by jrguliz on 2009-06-12
[SIZE=3]I have a similar problem using an Atheros PCI card on a desktop and pcmia card on a laptop....
Both card and wireless worked in 8.10 

First the desktop:


Here's what I have after using the command mentioned...[/SIZE]
[SIZE=3]
*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:00:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10

  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 8d
       serial: 00:50:8d:6b:86:63
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.104 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:0b:af:61:f7:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/SIZE]


lspci gave me:

00:00.0 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:08.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 8d)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)


iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

What else is needed?

Thanks in advance.

:D

---

### Post by ssands10 on 2009-07-10
Okay, I'm new at this too.  Have a Acer Aspire One netbook and have both a Ubuntu 9.04 on a USB and a Kubuntu 9.04 on a separate USB.  Trying to connect wirelessly to a 2WIRE router.  When I boot the Ubuntu (Gnome) I can set up the connection easily with the ssid and password, but doing the same (checked spelling and caps) in the Kubuntu version doesn't work.  What am I doing wrong?  Thank you.

---

### Post by Wicked Willy on 2009-07-11
Hi there, I have just picked up the same problem as ssands10.  I am running Ubuntu 9.04 on an Acer Aspire laptop which is brilliant.  When I run Kubuntu 9.04 from the live CD I cannot get the wlan to connect.  I can get Ubuntu to connect easily from the live CD.  All spellings and caps have been checked.  Any ideas.  I have always been a fan of the KDE desktop and would like to give it a go.

---

