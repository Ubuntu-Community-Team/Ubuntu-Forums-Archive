---
title: "No wireless after upgrade to 11.10"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by PatrickZ on 2011-10-14
Hi

After upgrading to 11.10 my wireless connection stopped working. The wired connection still works even if clicking on the network manager icon will tell you "device not managed" for that too. 
I messed about with the libnss3 package trying to follow the instructions i found online, which were for a beta version of 11.10 i think - that didn't work. That might have led to that when i try to reinstall libnss3 in synaptic i get "E: Internal Error, No file name for libnss3".
Long story short, I don't know what to do and obviously i shouldn't just try things at random...
Oh, and I'm running a 64 bit system (w/ ubuntu studio).

All help is greatly appreciated!

Patrick

---

### Post by PatrickZ on 2011-10-14
When i click on the network manager icon it states "device not managed" for both wired and wireless connections. The wired connection works though.

---

### Post by Xenoty on 2011-10-14
Hi, 

I have the same problem since I have upgraded to 11.10, yesterday nothing wanted to work and the computer didn't find any wireless network and today after updating my system the wireless section on the right top had totally disappear, only the wired still appear . And of course the wireless on my key board stay orange like when it's off and nothing happens when i push on it.

---

### Post by derxen on 2011-10-14
Same here with a Linksys WUSB100N. After upgrading to 11.10 no more wifi: the module (rt2870.sta) is missing.

derxen

---

### Post by jawilljr on 2011-10-14
> **derxen said:**
> Same here with a Linksys WUSB100N. After upgrading to 11.10 no more wifi: the module (rt2870.sta) is missing.

derxen

The Ralink staging drivers have been removed from kernel version,s 3.0 and greater.

What you need to do is unblacklist the rt2* drivers from '/etc/modprobe.d/blacklist.conf'

Anyway you can always try this:

```
sudo modprobe rt2800usb
```

Jerry

---

### Post by Tony512 on 2011-10-15
I'm having the same issue. 

There were no rt2* drivers in '/etc/modprobe.d/blacklist.conf'.
```
sudo modprobe rt2800usb
``` didn't work. Though I haven't restarted, shouldn't need that should I?

ifconfig only gives me information for eth0 and lo.

The dropdown in the top right shows nothing about wireless.

Network settings shows Wired and Network Proxy.

MacBook 3.1, upgraded from Ubuntu 11.04

---

### Post by derxen on 2011-10-15
Thanks Jerry, that solved it.

---

### Post by peepingtom on 2011-10-15
tony512, restarting would be unnecessary. What type of USB wireless device are you trying to use?

---

### Post by Tony512 on 2011-10-15
peepingtom, 
Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)

```
sudo modprobe b43
```
^ This worked for me. Same concept but modified for a different device. Wireless immediately turned on and connected (had been previously configured in 11.04). Thanks Jerry.

---

### Post by Tony512 on 2011-10-15
PatrickZ and Xenoty, I imagine the solution to your issue is centered around the type of device you have as well.

Try:
```
lspci
```
and find the line for Network Controller, what is it? 
Post the whole thing if you want.

---

### Post by derxen on 2011-10-15
One update on my situation: wireless works, but it takes two full minutes to find a network configuration at start up, then only comes on as I log on to the desktop.

derxen

---

### Post by PatrickZ on 2011-10-15
lspci gives:

#00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)
02:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller#

---

### Post by Blakiefingers on 2011-10-15
I'm having the same problem with this router, 04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01. 

Please be gentle as I'm new to Linux and fairly stupid overall

blake

---

### Post by PatrickZ on 2011-10-15
...and another thing: my computer (a laptop) stopped going to sleep after "closing the lid". What is that about?

---

### Post by derxen on 2011-10-16
My slow start up is solved: there was some old stuff left in the /etc/network/interfaces that got in the way.

derxen

---

### Post by henryp on 2011-10-16
I have an HP DV5000 with broadcom B43** wireless. During upgrade to 11.10 I had "failed to load installer for wireless firmware".
 After much searching, found through Software Centre, I put "B43" in search box which then showed 4 B43.. items, the last not activated (legacy installer) I selected that and 20 secs later was up and running.

---

### Post by PatrickZ on 2011-10-17
Still no wireless. Hints/tips, anything? Computer says both wired and wireless are "unmanaged", the wired works though, the wireless does not.

---

### Post by PatrickZ on 2011-10-18
Somebody? Or do I have to do a clean installation? I'm seriously thinking about it...

---

### Post by miracleworker on 2011-10-19
Same here.  After upgrading to 11.10, wireless and wired both show in network panel applet as 'device not managed', however wired connection works.  Previously wireless worked out of the box with 11.04.

> $ lsusb | grep 802
Bus 001 Device 006: ID 13b1:0024 Linksys WUSBF54G v1.1 802.11bg

$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

---

### Post by miracleworker on 2011-10-19
Found a workaround: used Ubuntu Software Center to install wicd, which was able to find the available wireless networks.  Network panel applet still shows 'device not managed', but wireless is automatically connected on startup.

This is a pretty nasty upgrade path!

---

