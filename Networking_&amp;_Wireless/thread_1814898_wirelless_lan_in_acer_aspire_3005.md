---
title: "wirelless lan in acer aspire 3005"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by kmisad on 2011-07-30
Hi, 
 I am having problems to make wirelles LAN work in my Acer Aspire 3005 WLMi.
With my little knowledge I tried many solutions I ve found in different forums.
Is there any simplified way...I am happy with ubuntu and I do not want to return to Windows anymore.
 Or is there any other linux distribution where the driver probleme is not excisting?

 Thanks

---

### Post by Idefix82 on 2011-07-30
Please open the terminal, type in
```

lspci
lshw -C network

```
and paste the output from both commands here, enclosing them in "[CODE]" tags (click on the # symbol when you compile your post).

---

### Post by kmisad on 2011-08-01
Thanks, I hope Idid it ok.

> **Idefix82 said:**
> Please open the terminal, type in
```

lspci
lshw -C network

```and paste the output from both commands here, enclosing them in "[CODE]" tags (click on the # symbol when you compile your post).
#kmisad@kmisad-Aspire-3000:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
kmisad@kmisad-Aspire-3000:~$ kmisad@kmisad-Aspire-3000:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:2e:4f:ae
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.2 latency=173 maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:48000000-4801ffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
       resources: memory:e2000000-e2001fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
#

---

### Post by Idefix82 on 2011-08-01
Thank you. Please open the terminal again and type in
```

sudo apt-get install b43-fwcutter firmware-b43-installer

```
I am assuming that you have Ubuntu 11.04. If not, then leave out "firmware-b43-installer". Make sure you have internet access when you run this command. You will be asked for your password, but when you type it in, there will be no stars or anything like that. Just type in your password and hit enter.

After that, go to System > Administration > Hardware/Additional Drivers in the menu and activate the b43 driver. You might have to restart the computer after that. Let us know how it goes.

---

### Post by kmisad on 2011-08-04
> **Idefix82 said:**
> Thank you. Please open the terminal again and type in
```

sudo apt-get install b43-fwcutter firmware-b43-installer

```I am assuming that you have Ubuntu 11.04. If not, then leave out "firmware-b43-installer". Make sure you have internet access when you run this command. You will be asked for your password, but when you type it in, there will be no stars or anything like that. Just type in your password and hit enter.

After that, go to System > Administration > Hardware/Additional Drivers in the menu and activate the b43 driver. You might have to restart the computer after that. Let us know how it goes.

  


   Well, I copy paste the exact response that I am getting, but when I go to the drivers there is nothing there.
I remember when I had the 10.10 it came very easily, but since the update to 11.04 I have no wirelless...
 Once more thank you and I would be glad to help if I can by giving you informations that could help you...
 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libcdt4 libgvc5 libmagickcore3-extra libgraph4 libpathplan4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

