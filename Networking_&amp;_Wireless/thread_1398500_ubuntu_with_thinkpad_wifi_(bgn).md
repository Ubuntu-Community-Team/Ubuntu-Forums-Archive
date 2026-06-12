---
title: "ubuntu with thinkpad wifi (bgn)"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by outlaw350 on 2010-02-04
i have a thinkpad t500 laptop and for some reason i cant get my wireless internet set up. i think it might be because of my wireless card, even though im just using my factory one. i have looked everywhere for a solution and cant seem to find one. any help would be nice. my card is a  thinkpad wifi (bgn) (thats how it was listed when i ordered the computer)

---

### Post by gordintoronto on 2010-02-04
If you run Accessories/Terminal, then enter the command 
lspci

it will show you the PCI devices, which probably include the wireless adapter.  This will tell you the real name of the device, and you can Google "<devicename> ubuntu" to see how to make it work.  (If it's a USB device, use lsusb instead of lspci.)

---

### Post by outlaw350 on 2010-02-04
alright. i will try that out

---

### Post by outlaw350 on 2010-02-04
this is what i got back
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

---

### Post by outlaw350 on 2010-02-04
i also got this
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:22:68:18:d5:d7
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-3 ip=192.168.0.108 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:fc600000-fc61ffff memory:fc625000-fc625fff ioport:1840(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by gordintoronto on 2010-02-04
> **outlaw350 said:**
> 
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
11)

Wow, that is more devices than on most computers.  I'm pretty sure the Realtek 8172 is your wireless adapter.

If you are using 64-bit Ubuntu, a post from mrgoose in this thread:
[http://forum.novatech.co.uk/showthread.php?p=197789](http://forum.novatech.co.uk/showthread.php?p=197789) 
might solve your problem.

I assume you know how to connect by right-clicking the network manager icon, then providing the router's ID, encryption type and password.

Also see:
[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

---

### Post by chili555 on 2010-02-04
Please let us see:```
lspci -nn | grep Network
``` We are wondering if this is your device: 10ec:8172. If so, we will go here:

[http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II)

---

### Post by outlaw350 on 2010-02-04
i ran that last terminal and got
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)

---

### Post by outlaw350 on 2010-02-04
i think i almost got it. im stuck on this step

[LIST]
[*] Unpack the driver and open up an console and go to the directory you unpacked the driver to.
[*] Compile the drivers using the following commands:
[/LIST]

---

### Post by chili555 on 2010-02-04
If it is on your desktop, right click it and select 'Extract Here.' Then open a terminal and do:```
sudo apt-get install linux-headers-`uname -r` build-essential
cd Desktop/2009 
```Press Tab and it will fill in for you.```
sudo su
make 
make install
```Post back if you get stuck.

---

### Post by outlaw350 on 2010-02-04
i love linux its just not my thing lol. i extracted it to my desktop and when i put it the first command i get this back
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.31-14-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 200 not upgraded.

---

### Post by chili555 on 2010-02-04
That's perfect! That means those things are already installed! Please proceed!

---

### Post by outlaw350 on 2010-02-04
so right now im trying to see how to find my router and how to connect...i know how to add a connection to the network connections i think. im just lost with all this lol

---

### Post by outlaw350 on 2010-02-04
i also got this on the last command of the link you gave me 
 modprobe r8192se_pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'Reading'
WARNING: /etc/modprobe.d/blacklist line 2: ignoring bad line starting with 'Building'
WARNING: /etc/modprobe.d/blacklist line 3: ignoring bad line starting with 'Reading'
FATAL: Module r8192se_pci not found.

---

### Post by chili555 on 2010-02-04
There is an icon for Network Manager at the upper right of your desktop. Click it and see your network. Select it and supply any WEP or WPA details and connect. Please see attached.

---

### Post by chili555 on 2010-02-04
> WARNING: /etc/modprobe.d/blacklistWe can ignore these for now and we'll fix them later. 

Did 'make' and 'make install' go without any errors? Warnings we can live with, but no errors?

---

### Post by outlaw350 on 2010-02-04
its only showing my wired connection
got no errors

---

### Post by chili555 on 2010-02-04
Does the readme.txt by chance say you have to reboot? Did you?

---

### Post by outlaw350 on 2010-02-04
no it doesnt but i will

---

### Post by chili555 on 2010-02-04
> no it doesntIt doesn't? Which readme.txt do you have?  Mine says:> Runing the scripts accomplish all operations including building up modules 
from the source code, installing driver to the kernel and starting up the nic.
	1. Build up the drivers from the source code
	  make

	2. Install the driver to the kernel
          make install
          reboot

---

### Post by outlaw350 on 2010-02-04
im dual booting in windows 7 x64 with wubi running in vista compatiabilty. when i rebooted it crashed the whole ubuntu set up

---

### Post by chili555 on 2010-02-04
I don't know what to tell you. Me no speaka da winDowz. I don't know wubi. I know how to compile wireless drivers.

If it won't restart, I guess I'd try to find a wubi thread.

FWIW, I downloaded, did make and make install with the packages in the link I sent without errors or warnings.

---

### Post by outlaw350 on 2010-02-04
lol. i dont know. i will figure something out. im pronanly going to reinstall tomorrow and try again.  thanks alot

---

