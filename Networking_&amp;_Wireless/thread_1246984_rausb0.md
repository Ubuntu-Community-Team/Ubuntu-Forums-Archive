---
title: "rausb0"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by fields2grand on 2009-08-22
I thought I could make the transition to ubuntu without many problems and i have in some regards but here I am, frustrated and ready to revert to xp.  Here it goes, I'm typing on my new ubuntu machine, I have wireless internet through my internal laptop card.  I have a D-link dwl-g122 h/w ver. b1 f/w ver 2.02.  I used this usb device without ANY complications with backtrack to show clients the vulnerabilites in their crappy encryption.  So I decided to install linux so I wouldn't have to boot a live CD.  Now my dlink card which used to show up as rausb0 now shows up as wlan whatever.  I can not connect via wireless w/ my d-link USB and connot place it in monitor mode.  I have downloaded the ralink drivers for the dlink card but have NO idea how to install them.  after countless hours reading and watching youtube videos, I have made no progress (very frustrating).  I read about ndiswrapper but thought (likely wrong) that it will use windows drivers and I won't be able to place in monitor mode.  But even when I tried ndiswrapper it asks for a .inf file which I do not have from the ralink drivers.  So I assume I need to write something in my terminal to install these drivers.  I read the readme from the drivers and it's greek to me.  I don't know what information you gurus need and know that the first reply I may receive will be for more information.  Please remember I am VERY new to linux and will likely need to be walked through this step by step.  I know your time is precious and I will do as you ask.  Thank you for your time folks.  This is the readme info from my ralink drivers.  

ModelName:
===========
RT2500USB

===============================================================================================
Driver lName:
===========
rt2570.ko

===============================================================================================
Ralink Hardware:
===========
Ralink 802.11b/g wireless network card.

===============================================================================================
Description:
=============
This is a linux device driver for Ralink RT2500USB b/g WLAN Card.
This driver implements basic 802.11 function. 
Infrastructure and Ad-hoc mode with open or shared or wpapsk or wpa2psk authentication method.
WEP-40 and WEP-104 or tkip or aes encryption. 


===============================================================================================
Compatibility:
===================
Testing has been done with LinEX kernel 2.6.9, Fedora Core 3.
You may encounter some rough edges when working with recent other Linux kernels branch.


===============================================================================================
FILE LAYOUT:
=============
*.c            : c files
*.h            : header files                   
Makefile.6        :Makefile for kernel 2.6
Makefile.4        :Makefile for kernel 2.4
./LINUX_RACONFIG_Vx.x.x.x  : source code for utility RaConfig2500 version x.x.x.x
./LINUX_RACONFIG_Vx.x.x.x/bin/LINUX/RaConfig2500  : utility RaConfig2500

===============================================================================================
Build Instructions:  
====================
0) $dos2unix *
      $chmod 644 *
      $chmod 755 Configure

1) cp Makefile.x Makefile               // x is your kernel

2) $make
3) $insmod rt2570.ko     # Insert driver module
4) $ifconfig rausb0 up  # Bring up device 
5) $dhclient rausb0  # Get network IP address

  Note: Script functionality:
  Configure       retrive linux version 
6) ./LINUX_RACONFIG_Vx.x.x.x/bin/"Linux"/RaConfig2500

if lack of libstdc++.so.6, cp ./LINUX_RACONFIG_Vx.x.x.x/libstdc++.so.6 /usr/lib

7)Edit(or add the line) in /etc/modules.conf
   alias rausb0 rt2570

8) Create and edit 'ifcfg-rausb0' file in /etc/sysconfig/network-script/
   DEVICE='rausb0'
   ONBOOT='yes'
   BOOTPROTO='dhcp' 



I have no idea what to do with this information other than it needs to be entered via terminal.  I tried to use the /configure option in terminal to execute the driver but I'm sure I did it wrong.  I saved these drivers to my desktop and I don't think terminal knew where to look for the files.

adding more info:

phil@phil-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


and more:

phil@phil-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
phil@phil-laptop:~$ 


and more 

phil@phil-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:26:d6:cc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:ac:ea:ca
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2a:eb:50:bd:6c:c1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:11:95:e9:f7:4c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
phil@phil-laptop:~$ 



and more:

phil@phil-laptop:~$ sudo iwlist scan
[sudo] password for phil: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

wmaster1  Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Network is down

phil@phil-laptop:~$ 


I don't know what any of this crap means but I saw someone else post it and he got a lot of replies.

---

### Post by fields2grand on 2009-08-22
I see there's several views and no replies.  I can see this board is regularly monitored.  If you see this post and feel I'm ignorant or this issue has been hashed out a million times before, I understand. I've looked high and low and have found nothing with over 7 hours of research so if you can help with the info i have given or you can direct me where to get more help (which I doubt they can help me as much as you can) I will appreciate it.

---

### Post by Iowan on 2009-08-22
Several of the views may have been folks like me who'd LOVE to offer some assistance, but after reading the description, have decided that they may not be able to help after all. Perhaps the expert advice is still a few hours from checking in. Good luck! I'd like to see a solution to file away "for next time".

---

### Post by fields2grand on 2009-08-22
OK.  I appreciate your reply.  Thank you mam/sir.

---

### Post by fields2grand on 2009-08-23
i'm posting to keep this article at the forefront for if i can't get this solved, I will likely revert to windows.....and I want to get this solved.  Please give me suggestions.  Thank you.

---

### Post by fields2grand on 2009-08-23
anyone?  Bueller?

---

