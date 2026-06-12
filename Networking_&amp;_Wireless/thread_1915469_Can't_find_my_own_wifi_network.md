---
title: "Can't find my own wifi network"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by plfwctt on 2012-01-26
Hi All,

I ahve just re-installed Ubuntu 10.04 and have come across a problem. When  I put the disc in and ran live it found and connected to my home wifi network, now it wont find it. It will find my neighbors networks just fine and the windows xp partition I have connects just fine. 

I assume the wifi adapter is working fine, as like I said it will show my neighbors connections. This is rather annoying as it will find theirs through walls and who knows what distance but wont find mine that is about 8 feet away from the machine.

I have run iwlist wlan0 scan and that wont find it, the other PC and even my phone will connect though.  

Thanks in advance for any help you can give me.

---

### Post by Grenage on 2012-01-26
I assume you've tried quick and easy options, such as restarting the access point; changing the band/mode or other settings are unlikely to make a difference, but I've seen stranger things happen.

---

### Post by kevdog on 2012-01-26
Can we have more info about your wireless card?
lshw -C network
lspci -nn

---

### Post by plfwctt on 2012-01-27
I will try them both kevdog, Will take me a bit though as I will have to save results to txt file and post them from windows. It did start to work last night but has stopped again today.

---

### Post by plfwctt on 2012-01-27
This is what I get when I run the commands 

description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:76:90:6c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device, BCM4320b usb-0000:00:1d.7-1 ip=192.168.0.2 multicast=yes wireless=IEEE 802.11bg


00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) [1002:5940] (rev 01)
05:02.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5782 Gigabit Ethernet [14e4:1696] (rev 03)

I think the problem is the fact that I have two versions of linux I can boot to. one I am pretty sure is 64bit as when I updated firefox I was offered the i686 version, the other could well be 32bit and it is this one that does not connect.

---

### Post by kevdog on 2012-01-27
It would seem that your driver is correctly associated with your usb bcm4320 chipset.  So I don't believe its a driver issue.

Couple things you can try.  Look at dmseg and see if you have any errors related to your usb device.  dmesg is going to have a lot of information in it, so your going to have to scan through the lines to see if anything is related to your device.  Takes a few minutes.

sudo iwlist scan 
That doesn't show anything does it?

---

