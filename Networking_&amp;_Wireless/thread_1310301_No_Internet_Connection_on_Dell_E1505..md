---
title: "No Internet Connection on Dell E1505."
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by LifesonFan2112 on 2009-11-01
I ran Ubuntu off the install disc to test it. Everything was fine. Wireless internet up and running so I did a clean install.

Now I cannot connect at all--not even when using Ethernet straight from my modem.

When I go to Hardware Drivers, it shows Broadcom STA Wireless Driver, and below it says "This driver is not activated." When I press the Activate button, a box appears for about two seconds saying "installing drivers", and then disappears. A popup appears at the top right saying "disconnected - you are now offline."

Any suggestions?

---

### Post by LifesonFan2112 on 2009-11-01
Do I need internet connection to obtain the Broadcom drivers or are they preinstalled in the OS? Is there a way to manually install the drivers? 

I downloaded the 32-bit driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Burned it onto a disc and tried to install it but this is unlike Windows where you just double click an .exe file. If this OS is this much of a headache just to manually install drivers then it is not for me.

---

### Post by LifesonFan2112 on 2009-11-01
Ok, I can get a wired connection. I reinstalled Ubuntu and the drivers for my network card must have installed correctly this time.

Still cannot get wireless to work. 


darren@darren-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:04:96:be  
          inet addr:76.90.246.250  Bcast:76.90.246.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe04:96be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67105762 (67.1 MB)  TX bytes:3125448 (3.1 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)






darren@darren-laptop:~$ sudo lshw -c network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:dfdfc000-dfdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:04:96:be
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=76.90.246.250 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:df9fe000-df9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:34:22:4a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by RedSingularity-mistake on 2009-11-01
What is your "lspci" output?

---

### Post by LifesonFan2112 on 2009-11-01
DOn't know if I didn this right. I just typed lspci the terminal and this is what it spit out:


darren@darren-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
darren@darren-laptop:~$

---

### Post by LifesonFan2112 on 2009-11-01
Why does it work temporary when I boot from the LiveCD? I say temporary because after it connects wirelessly, it locksup and I have to restart by holding the power button.

---

### Post by mbr78 on 2009-11-02
I got wireless working with Broadcom drivers. I searched the USB stick I used to install 9.10 for "bcmwl-kernel-source". I then right clicked the package and reinstalled it. Then after a reboot my wireless worked.

---

### Post by LifesonFan2112 on 2009-11-02
YES! It works!!

I followed the directions found here [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

I was THIS close to going out and buying Windows 7.

---

