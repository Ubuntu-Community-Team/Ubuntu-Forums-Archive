---
title: "Dell Studio 15 No Internet"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by Bbman90 on 2009-05-28
I've used Ubuntu in the past, but only on my desktop. Now that I have a laptop I want to move it here and not fool with my desktop anymore. I installed Ubuntu 9.04 at a friend's house and everything was working perfect except for my fingerprint scanner, which I'll work on. Even Bluetooth was working fine. But now that I'm home I can't get on the internet. I don't know what setup my friend has, but I connect to a Linksys Wireless-N router. I saw drivers on the internet for getting wireless to work on this laptop, but I didn't need them before. I downloaded them on Windows and got them with Linux, but it won't make. If anyone knows what I can do it'd be greatly appreciated. The drivers I tried to make were hybrid-portscr-x86-_64-v5_10_91_9. I dual boot Vista Home Premium, and I'm 64 bit. I ran the command 'lspci -v | less' and it popped up some things:

00:00.0 Host bridge: Intel Corporation Mobile 4 SeriesChipset Memory Controller Hub (rev 07)
Subsystem: Dell Device 029f
Flags: bus master, fast devsel, latency 0
Capabilities: [e0] Vendor Specific Information <?>
Kernel driver in use: aggpart-intel
Kernel modules: intel-agp


Anything else you need to know please ask.

---

### Post by Boondoklife on 2009-05-28
can you please post back the results of lspci and lsusb

---

### Post by Bbman90 on 2009-05-28
Quite happy to. Here's lspci...

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

...and here's lsusb.

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:63fa Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Boondoklife on 2009-05-28
can you post iwconfig and also you may want to look into this

---

### Post by Bbman90 on 2009-05-28
Alright. iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"rogersnet"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

And look into what?

By the way, those faces are a colon followed by the letter o.  : + o

---

### Post by Boondoklife on 2009-05-28
well looks like your card is seen, what happens when you click the network icon on the toolbar?

---

### Post by Bbman90 on 2009-05-28
It shows the available networks, detects them all fine, and mine (rogersnet) is shown with full strength. But it simply won't connect to it.

---

### Post by Boondoklife on 2009-05-28
What type of setup do you have on the router? WEP WPA WPA2 Nada?

---

### Post by Bbman90 on 2009-05-28
I believe it is WPA2. I just remembered that I used an Easy Install thing on a USB drive that the program Linksys Network Advisor or something like that created on my dad's computer, which the router is on. I ran it on Windows and it connected. Is something like that REQUIRED for my Router, in which case I'm screwed? And can SAMBA actually be used to get on the internet? I have no experience with it.

---

### Post by Boondoklife on 2009-05-28
Samba is used for file sharing, not connection sharing.

If the router is setup as WPA2 then you will need to check that in the connection when it tries to connect and input any passwords for it. This is REQUIRED as it is part of the WPA2 protection. I use just WPA and know a couple people having issues with WPA2 so not sure.

---

### Post by Bbman90 on 2009-05-28
I just tried connecting to a couple of unsecured networks and I couldn't get on them either. Maybe I need to ask a better question. Here's the driver I downloaded but couldn't make. [http://www.linlap.com/wiki/dell+studio+15](http://www.linlap.com/wiki/dell+studio+15) It's right there in the wireless section. Could you see if you could use make on it? Mine claims there's no Makefile even though there is. Maybe getting that driver installed would let me out.

---

### Post by Bbman90 on 2009-05-28
Ugh. Someone who knows how please report this guy for spam or whatever.

---

### Post by dmizer on 2009-05-28
> **Bbman90 said:**
> Ugh. Someone who knows how please report this guy for spam or whatever.

Use the report post button: [img]http://ubuntuforums.org/images/buttons/report.gif[/img] :)

---

