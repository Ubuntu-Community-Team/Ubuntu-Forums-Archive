---
title: "How to Revive Wired Internet and Setup Wireless?"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by RedStarYellowSun on 2013-05-12
I'm trying to salvage a laptop long-abandoned by its owner and, just recently, given to me. Things were so messed-up that I just had to wipe the slate clean by replacing everything with Ubuntu 13.04.

In its post-installation state, it couldn't use wireless Internet, only wired. I checked the "Software and Updates" window's "Additional Drivers" tab to find this:
```
- Broadcom Corporation: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
This device is not working.
    (-) Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)
    ( ) Do not use the device
- Unknown: Unknown
This device is not working.
    ( ) Using Non-free firmware for Linux kernel drivers from linux-firmware-nonfree (proprietary)
    ( ) Continue using a manually installed driver
    (-) Do not use the device
```
As can be seen, I had the Broadcom driver installed.

The problem is that the installation has frozen at 80%. I'm thinking that the installation might need some information online to continue, but the laptop has lost its ability to sense the wired Internet it is already connected to. How can I make it re-sense the wired Internet?

Here is the current data on the laptop's state:
Ifconfig
```
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:267301 (267.3 KB)  TX bytes:267301 (267.3 KB)
```
sudo lshw -C network
```
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:dfdfc000-dfdfdfff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=wl latency=64
       resources: irq:17 memory:dfdfe000-dfdfffff
```
lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
I hope this helps.

As to the second device, I am not sure what it is, but the "Continue using..." seems to imply that the driver is already there ready to be used, so I am thinking of choosing the second option after the first problem is resolved. Would you guys agree?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by Hadaka on 2013-05-12
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
#boot then while wire connected do..
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modpeobe b43
 
```
thanks

---

### Post by RedStarYellowSun on 2013-05-12
Thaks for the speedy response!

> **Hadaka said:**
> Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
#boot then while wire connected do..
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modpeobe b43
 
```
thanks

I don't quite get the 2nd line of the code. Just to be clear, I am to use to put that whole code in Terminal, right?

Or did that mean that I am to use...
```
sudo apt-get remove --purge bcmwl-kernel-source
```

Then, boot the computer and, then, (while the laptop is wired to the Internet) use...
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modpeobe b43
```?

---

### Post by Hadaka on 2013-05-12
Hi, yes that is correct..with linux a " # " is used as a comment.
so please do..

```
sudo apt-get remove --purge bcmwl-kernel-source
```
then boot.
your wired connection should now be working.
then do...
```
 sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modpeobe b43
```

---

### Post by RedStarYellowSun on 2013-05-12
> **Hadaka said:**
> Hi, yes that is correct..with linux a " # " is used as a comment.
so please do..

```
sudo apt-get remove --purge bcmwl-kernel-source
```
then boot.
your wired connection should now be working.
then do...
```
 sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modpeobe b43
```

It worked!
Thank you so much!

Sincerely,
RedStarYellowSun

P.S.: Hmmm... Ubuntu Forums has changed a lot since last time I was here. How do I mark this "solved" with this new setup?

---

### Post by Hadaka on 2013-05-12
Glad that worked for you, to mark solved go here....

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by RedStarYellowSun on 2013-05-12
> **Hadaka said:**
> Glad that worked for you, to mark solved go here....

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks again!

Take care,
Red StarYellowSun

---

