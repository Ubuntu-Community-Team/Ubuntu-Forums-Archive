---
title: "Dell Studio 1536 x36 Wireless"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by Kaisermage16 on 2010-02-18
I recently installed Ubuntu/Linux system on my laptop. I bought it refurbished and it has a(n) AMD Turion dual core processor. I am unable to find my wireless card and the Wi-Fi is active. Is there a place I can download it?

I looked in my Command Prompt for Windows 7, it said DELL Wireless 1397 WLAN Mini-Card.

Any clue as what that is?

---

### Post by Crafty Kisses on 2010-02-18
Hello, I need a bit more information about the chipset that's currently in your laptop. So what you can do for me is go into the terminal **(Applications->Accessories->Terminal)** and then copy and paste these commands one by one in the terminal:
```
lspci
lsusb
lshw -C network
```
That will just tell me a bit of information on your current network setup and the chipsets that you have. Once you give me the results of those commands, I can point you in the right direction so we can get your wireless working! Remember to use the /code brackets when posting the results, it's easier for me and other forum users to read the results. Thanks!

---

### Post by Kaisermage16 on 2010-02-18
Ok, I input, this is all I got from it.

john@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

john@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 12d1:1413 Huawei Technologies Co., Ltd. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 05ca:18a1 Ricoh Co., Ltd 

john@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f7cfc000-f7cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:81:17:90
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.09 latency=0 multicast=yes
       resources: irq:28 memory:f7bf0000-f7bfffff

I don't know if that's of any use or not.


Fixed

---

### Post by Crafty Kisses on 2010-02-18
According to **"lspci"** you have the following card:
```
Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
So what I think I'm going to do is have you go the ndiswrapper route. Now, this is quite easy if you follow my directions, some people find it complicated, but it's really fairly simple. So the first thing you want to do is install ndiswrapper of course, so run the following:
```
apt-get install ndiswrapper-common
```
Once you have ndiswrapper installed you need the drivers for your BCM4312, so you can download that right **[here.]("http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/WLAN_Intel_12.1.0.14_XPx86.zip?acerid=633701164795352753&Step1=Netbook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=PA_6")** Now you are going to need to extract that file, so you can run:
```
tar -xvzf WLAN*
```
Then once you have done that, and it's extracted into a folder, enter the folder and then you need to run:
```
ndiswrapper -i filename.inf
```
Once you have done that, (now remember where it says filename.inf, replace it with the actual .inf file name) now make sure ndiswrapper is installed correctly, so run:
```
ndiswrapper -l
```
You should get a message saying the driver is present. You now need to run these commands:
```
depmod -a
ndiswrapper -m
```
Now once you have done that, load the ndiswrapper module:
```
modprobe ndiswrapper
```
Then see if your card is working. Now that is method A, now method B is quite simpler but might not work, some folks have had success by reinstalling the following package:
```
apt-get reinstall bcmwl-kernel-source
```
Then reboot and see if your wireless card works, now of course that is a method you might want to try before ndiswrapper, now method C would be compiling the official Broadcom drivers from source and installing them that way, first thing you want to do is have build-essential, so run:
```
apt-get install build-essential
```
Now that you have that, you can get the official driver right **[here.]("http://www.broadcom.com/support/802.11/linux_sta.php")** Once you have that, you can start compiling, so run:
```
tar -xvzf hybrid*
```
Now you need to start compiling/making the file, so run:
```
make -C /lib/modules/`uname -r`/build
```
Now that you have made and compiled the drivers, you need to load the following modules:
```
modprobe lib80211_crypt_tkip
modprobe wl
```
Once you have done that, you need to run:
```
depmod -a
```
Then your wireless card should be working, now those are 3 methods that can get this card working, now method 2 might not work, but method 1 and 3 should work perfectly.

---

### Post by northd_tech on 2010-02-18
I have bumped a few of the Broadcom 4312 threads- a lot of people (or Karmic 9.10 perhaps) are having trouble with the 4312 and wireless lately.

A forum search or looking at one of those recent threads in this sub-forum tagged with "4312" should help too- there will be links where one can download the "STA" driver directly from Broadcom too.

Ndiswrapper was the first thing that I used to get Broadcom wireless (but that was years ago now).

---

### Post by Kaisermage16 on 2010-02-19
Still isn't working.

---

### Post by bkratz on 2010-02-19
> **Kaisermage16 said:**
> Still isn't working.

which of the three methods mentioned did you finally try to use? What are you seeing now?

---

### Post by Kaisermage16 on 2010-02-19
> **bkratz said:**
> which of the three methods mentioned did you finally try to use? What are you seeing now?

I tried them all, none of them seemed to work.

---

### Post by bkratz on 2010-02-19
Could you post the output of 

lsmod

(that is LSMOD in lowercase) so we can see which modules are loaded --they are probably conflicting with each other.
If you use the "code" tags in the listing it will shorten it up a lot and make it easier to read. If you can't figure out how to do this just copy/paste the whole thing here anyway. We probably will have to blacklist or remove some modules.


You might to add the output of

iwconfig

also.

---

### Post by cjwolfer on 2010-04-01
well i have a dell studio 1536 laptop to. well i had the exact same problem but my friend whos pretty good with ubuntu said hook up to a ethernet cable to install everything and to go System->Administration->Hardware Drivers and to check for anything wireless card related well low and behold there was one called Broadcom STA wireless driver that is made specificly for the dell 1536 minicard so try that to save urself alot of time

---

