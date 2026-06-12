---
title: "Network Driver"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by mikeyfg on 2010-10-14
Hey all this is my first post and my first time using Ubuntu i love the OS but i cannot understand how to install .tar.gz files.... I got the Ndiswrapper installed but when i go to windows driver install i dont know where the .inf file is i downloaded e1000e-1.2.10.tar.gz from intels site i placed it on my desktop but what do i do with this .tar.gz windows driver installer wont install it and i cant get my internet to work at all. Im lost can anyone help me??

---

### Post by pricetech on 2010-10-14
If it's a .tar.gz file, it's probably a driver for Linux, not for windows.  A windows driver will usually be either an exe or a zip file.

If you right click on the .tar.gz file, you should get an option to open in Archive Manager.  Do that and extract it wherever you want to and see if there's a readme file somewhere in the archive.  It should tell you how to install.

---

### Post by johnnytm on 2010-10-14
If the readme file wont open in gedit right click on it and open it with open office. All the instructions for build and install are in there

---

### Post by mikeyfg on 2010-10-15
> **johnnytm said:**
> If the readme file wont open in gedit right click on it and open it with open office. All the instructions for build and install are in there
 
I got far last night man all the way up until the readme file told me to create an ip address i got stuck i input the command i think it was ifconfig<IP_Address> but i didnt know if it wanted me to input a real IP like 192.168.1.1 or actually "IP_Address" but i got an error message im really stuck here at this point what should i do?

---

### Post by pricetech on 2010-10-15
Try ifconfig by itself to see is your NIC is working.

You'll need to use sudo if your assigning an IP.

---

### Post by xbobby_bobx on 2010-10-15
> **mikeyfg said:**
> Hey all this is my first post and my first time using Ubuntu i love the OS but i cannot understand how to install .tar.gz files.... I got the Ndiswrapper installed but when i go to windows driver install i dont know where the .inf file is i downloaded e1000e-1.2.10.tar.gz from intels site i placed it on my desktop but what do i do with this .tar.gz windows driver installer wont install it and i cant get my internet to work at all. Im lost can anyone help me??

What is your wireless card? go the terminal and type lspci then scroll down you will find your wirless card post it here and I will try my best to help. :)

---

### Post by chili555 on 2010-10-15
The module e1000e has been built in to the kernel for many years. If it's not loading or driving your device, either you are trying to use the wrong driver, or something else is wrong. Please post:```
lspci
```as xbobby_bobx requested. I think he will also want to see:```
dmesg | grep e100
```

---

### Post by xbobby_bobx on 2010-10-15
Yup! if I'm able to know the exact serial number of it I will be able to solve his problem.

---

### Post by mikeyfg on 2010-10-16
> **xbobby_bobx said:**
> Yup! if I'm able to know the exact serial number of it I will be able to solve his problem.

Hey guys thanks for all your help here are the outputs of what you requested

mikey@Michael:~$ dmesg | grep e1000
[    0.892721] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
[    0.892725] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
[    0.892765] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.892774] e1000e 0000:00:19.0: setting latency timer to 64
[    0.892865] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    1.164409] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:21:70:4f:31:b6
[    1.164412] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.164433] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: ffffff-0ff
[   20.480222] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   20.537066] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   22.321859] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   22.321863] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3702.961119] e1000e: eth0 NIC Link is Down
[ 3715.593856] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 3715.593860] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3719.409117] e1000e: eth0 NIC Link is Down
[ 3721.189856] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 3721.189859] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3721.401118] e1000e: eth0 NIC Link is Down
[ 3723.109856] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 3723.109859] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3739.777118] e1000e: eth0 NIC Link is Down
[ 3741.473862] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 3741.473865] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 3741.769118] e1000e: eth0 NIC Link is Down
[ 3743.477862] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 3743.477865] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
mikey@Michael:~$ 






mikey@Michael:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.6 Signal processing controller: Intel Corporation 82801JI (ICH10 Family) Thermal Subsystem
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:06.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:06.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
mikey@Michael:~$ ^C

---

### Post by xbobby_bobx on 2010-10-16
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03) cool I know how to activate it for you without the NDISWRAPPER first do you have the live disk?

---

### Post by mikeyfg on 2010-10-16
> **xbobby_bobx said:**
> 03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03) cool I know how to activate it for you without the NDISWRAPPER first do you have the live disk?

Yea i downloaded it from the home page and saved it as an .iso i believe to a CD i already have ndiswrapper installed i believe if that matters

---

### Post by xbobby_bobx on 2010-10-16
Listen Uninstall the NDISWRAPPER completely then follow this thread [http://ubuntuforums.org/showthread.php?t=1597909](http://ubuntuforums.org/showthread.php?t=1597909)
It will show you how to install the leagl driver for Ubuntu if you have any problems just replay ok? I hope that will help

---

### Post by mikeyfg on 2010-10-16
> **xbobby_bobx said:**
> Listen Uninstall the NDISWRAPPER completely then follow this thread [http://ubuntuforums.org/showthread.php?t=1597909](http://ubuntuforums.org/showthread.php?t=1597909)
It will show you how to install the leagl driver for Ubuntu if you have any problems just replay ok? I hope that will help

How would i uninstall ndiswrapper?

---

### Post by xbobby_bobx on 2010-10-16
Go to administration>Synaptic> now go to the search and type ndiswraper then you will find it check it as complete removal if it says unintall ndisgtk too don't worry press ok and the go to the search again and the type ndisgtk and uninstall it too then restart now you will follow my old thread is that ok with you or you need me to make a video about it? again I'm here to help :)

---

### Post by mikeyfg on 2010-10-16
> **xbobby_bobx said:**
> Go to administration>Synaptic> now go to the search and type ndiswraper then you will find it check it as complete removal if it says unintall ndisgtk too don't worry press ok and the go to the search again and the type ndisgtk and uninstall it too then restart now you will follow my old thread is that ok with you or you need me to make a video about it? again I'm here to help :)

Dude there are like 1540 files to download OMG is there an easier way? A video would be awesome though

---

### Post by xbobby_bobx on 2010-10-16
Ok well I'm not on my computer now I will do it tonight and post it on youtube can you wait for one day? if so that will be great and I will explain everything however why it would download something? O.o this is weird but don't worry video will do it :D.

---

### Post by mikeyfg on 2010-10-16
> **xbobby_bobx said:**
> Ok well I'm not on my computer now I will do it tonight and post it on youtube can you wait for one day? if so that will be great and I will explain everything however why it would download something? O.o this is weird but don't worry video will do it :D.

Yes sir i can wait a day id greatly appreciate it thanks a million

---

### Post by xbobby_bobx on 2010-10-16
You are very welcome!.

---

### Post by xbobby_bobx on 2010-10-17
Ok I just found out you don't have to remove the NDISWRAPPER if you didn't install the windows driver well try to use my other thread that I posted if it didn't work please contact me ok?

---

### Post by mikeyfg on 2010-12-15
Hey guys im back i got this installed dont really know what it is... I think its the driver!!! But it still wont connect what do i do now? Here are screenshots from my EVO i hope they are clear enough...

---

### Post by xbobby_bobx on 2010-12-16
Hello again I know you have been trying so hard to fix this problem but what I suggest you is to install the real BCM card which it's in the live disk try to google it about how to do it if it's still not working I will help you through it.

---

