---
title: "Cannot establish Wireless Connection"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by Lancastrian on 2009-04-17
Hi,
I am a relative beginner and wish to explore whether Ubuntu is a better option for me than Vista or XP.
I know little about ubuntu but am getting disillusioned with Microsoft.
Vista has given me a lot of problems since I purchased the laptop just over 12 months ago.
I am currently using an older HP laptop( which I kept as a spare)  with XP Home Edition.
 The newer HP laptop with Vista is failing to boot up ( blank black screen )  and I think there is a problem with the hard drive.
The 2 laptops are connected to a home network - just the 2 computers.
I have booted up Ubuntu on the XP model from the CD I downloaded.
I am up & running with an internet connection on the XP via a cable to my Wireless Router but I cannot establish a wireless connection.
Enable Network and enable wireless are ticked.
I need the wireless connection so I can take the laptop to another room.
I have noticed that when I switch from XP to the ubuntu CD the Wireless Assistant blue light just above the keyboard does not come on whereas it does come on when I am booted up on XP.

---

### Post by Michael.Godawski on 2009-04-17
hi Lancastrian,

welcome to Ubuntu first.
Wireless can be a tricky issue, but sometimes few steps are required to activate it. (Sometimes more ;) than few)

So you haven't installed Ubuntu to the hard drive yet? You are only running it from the Live CD?

Can you please post the output of these terminal commands:
```
lshw -C network
lspci
```

---

### Post by Lancastrian on 2009-04-17
Hi Michael,
Yes I haven't installed yet I  am running it from the live  CD.
I do want to try dual boot but I am not very experienced and don't want to mess XP up as my Vista computer is down at the moment.
I have got the results you asked for but can't see how to copy and paste the results in here - the options don't seem available.
I am probably missing something obvious !!

---

### Post by superprash2003 on 2009-04-17
copy pasting is similar to copy pasting from 1 page to the other.. just highlight the output from the terminal, right click on copy.. and then create a new post in this thread and right click and click on paste..

---

### Post by Lancastrian on 2009-04-17
Thanks superprash,
I was missing the obvious.
Below is the pasting of the result. 

o run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:b9:52:4a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.37 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:f8:ef:e3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 62:75:c2:29:7f:8a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
ubuntu@ubuntu:~$

---

### Post by dnguyen1963 on 2009-04-17
Try this link...I have had success with Broadcom wi-fi card using this procedure.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Duy

---

