---
title: "Inspiron 1525 - Wireless 1395 WLAN Mini-Card hardware present : NO"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by crazyvirus on 2010-10-26
**Inspiron 1525 - Wireless 1395 WLAN Mini-Card **

Hi there, 

I passed two days browsing the net looking for a solution to my problem but no way.. Im running ubuntu 10.10 in my inspiron via VirtualBox and my wireless card is not detected by ubuntu.. I installed the bcmwl6.inf driver with the wrapper and it show me in wireless window that the hardware is not present.. So checked that in the terminal by typing : 


```
lshw -C network
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 02
       serial: 08:00:27:0f:5d:59
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=10.0.2.15 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:10 memory:f0000000-f001ffff ioport:d010(size=8)

```Could you please gimme a hand and help me to solve the problem!

lspci : 
```
~# lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0b.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
00:0d.0 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)

```

Cheers.

---

### Post by johnnytm on 2010-10-26
go to system-->administration-->additional drivers with the wired connection plugged in run the scan and add the broadcom sta driver.

---

### Post by crazyvirus on 2010-10-26
Thanks for the quick reply .. 

It show me : No proprietory drivers are in use in this system. and there is only oracle vm with green light.. How can i run the scan?

I downloaded the sta from : 
```
 http://www.broadcom.com/docs/linux_sta/hybrid-portsrc_x86-32_v5.60.246.2.tar.gz
```how i install it please?

PS : bcmwl-kernel-source already installed

---

### Post by crazyvirus on 2010-10-26
OHH MYY GOD!! SORRY BUT IM REALLY PISSED OFF!! PLEASE HELP, a lot of my time wasted and i need the wireless on ubuntu to start workin on a project!!

---

### Post by johnnytm on 2010-10-26
What is the output of ```
sudo lshw -C network
```
and ```
ifconfig
``` and ```
iwconfig
```

---

### Post by crazyvirus on 2010-10-26
Here you go : 

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 02
       serial: 08:00:27:0f:5d:59
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI duplex=full firmware=N/A ip=10.0.2.15 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:10 memory:f0000000-f001ffff ioport:d010(size=8)


```
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:0f:5d:59  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe0f:5d59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1143357 (1.1 MB)  TX bytes:210656 (210.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by johnnytm on 2010-10-26
wireless is not installed, but from the looks of it u can connect via your wired connection right? It should have scanned automatically when u opened the additional drivers utility under system-->administration. But We can try to install it from terminal as well with```
sudo apt-get update
``` and then ```
sudo apt-get --reinstall install bcmwl-kernel-source
```hopefully this takes care of your problem. may require a reboot.

---

### Post by crazyvirus on 2010-10-26
Yes i have a wired connection and i already did this :(  !! My problem that i want to connect a windows client application with a linux server (via sockets)... do know how can i do that with a wired connection... i did some change for the /etc/network/interfaces... but its not working!

---

### Post by crazyvirus on 2010-10-27
i did it again and not working !!

---

### Post by crazyvirus on 2010-10-27
Ouff Well i fixed the problem of (client/server) connection by playing with the network option of virtual machine .. but the wireless card still not detected!!

---

### Post by johnnytm on 2010-10-27
Can you post the output of ```
lsmod | grep 'wl'
``` and ```
lspci -nn | grep 'Broadcom'
``` if no broadcom is present on second command try ```
[FONT=Arial][SIZE=2]sudo rmmod -f dell-laptop[/SIZE][/FONT]
``` then see if the wireless card enables if it does u can use ```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
``` to add to startup

---

### Post by crazyvirus on 2010-10-27
No input for every command..

---

### Post by johnnytm on 2010-10-27
There should have only been for the f the first 2 anyhow, but the fact that you say there wasn't tells me that not only is your card missing from the install, but the driver is not there either. However the drivers you downloaded are not very hard to install, but you have to build first. if you right click on the file you downloaded there should be an option to extract here. Use that and it will create a new folder in the current folder you are in. Open that and find the read me file. Complete instructions for install are in there. You may need to install build-essential so your wired network may be needed. If you don't like changing directories so  many times( it annoys me) terminal can be installed inside folders so all the commands can be run from where ever you are browsing. See post 5 here [http://ubuntuforums.org/showthread.php?t=1598309](http://ubuntuforums.org/showthread.php?t=1598309) for how to set that up.

---

