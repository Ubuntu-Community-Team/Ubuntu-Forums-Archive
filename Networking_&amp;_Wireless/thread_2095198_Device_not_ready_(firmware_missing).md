---
title: "Device not ready (firmware missing)"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by beginnerfromfinland on 2012-12-16
Hello! I installed Ubuntu 12.04 LTS 32bit to my about 10 years old Fujitsu Siemens Amilo -notebook. The problem is that my wireless connection doesn't work. I am not quite sure, worked it on Windows Xp or not. I've searched google but I can't find answers. I think my card is Realtek RTL-8139
Thanks for your help!

A beginner from Finland

---

### Post by chadk5utc on 2012-12-16
> **beginnerfromfinland said:**
> Hello! I installed Ubuntu 12.04 LTS 32bit to my about 10 years old Fujitsu Siemens Amilo -notebook. The problem is that my wireless connection doesn't work. I am not quite sure, worked it on Windows Xp or not. I've searched google but I can't find answers. I think my card is Realtek RTL-8139
Thanks for your help!

A beginner from Finland

The Realtek RTL-8139 is a very common Network chip usually wired type connect. I did how ever google your Laptop model and came up with a link that may help you
[http://www.ubuntugeek.com/how-to-get-wireless-button-working-on-fujitsu-siemens-amilo-li1718.html](http://www.ubuntugeek.com/how-to-get-wireless-button-working-on-fujitsu-siemens-amilo-li1718.html)
Please read and decide for yourself as I do not know if this is out of date info or will work with your particular PC

---

### Post by GordThompson on 2012-12-16
@beginnerfromfinland:

Does the notebook also have a wired network connection? If so, does that work?

---

### Post by beginnerfromfinland on 2012-12-16
Ok I'll try thanks! But actually that site speaks about wireless button. Does it mean some kind of hardware wlan button? I have tried to find that but it seems that there are not on my device.

---

### Post by beginnerfromfinland on 2012-12-16
> **GordThompson said:**
> @beginnerfromfinland:

Does the notebook also have a wired network connection? If so, does that work?

Yes I it works fine on ethernet.

---

### Post by GordThompson on 2012-12-16
> **beginnerfromfinland said:**
> Yes I it works fine on ethernet.
Good. That will make it much easier to troubleshoot your problem.

Please start by opening a Terminal window, running the following command, and pasting the results into a reply to this thread.

```
sudo lshw -class network
```

---

### Post by beginnerfromfinland on 2012-12-16
> **chadk5utc said:**
> The Realtek RTL-8139 is a very common Network chip usually wired type connect. I did how ever google your Laptop model and came up with a link that may help you
[http://www.ubuntugeek.com/how-to-get-wireless-button-working-on-fujitsu-siemens-amilo-li1718.html](http://www.ubuntugeek.com/how-to-get-wireless-button-working-on-fujitsu-siemens-amilo-li1718.html)
Please read and decide for yourself as I do not know if this is out of date info or will work with your particular PC

It works until downloading acerhk files....

---

### Post by beginnerfromfinland on 2012-12-16
> **GordThompson said:**
> Good. That will make it much easier to troubleshoot your problem.

Please start by opening a Terminal window, running the following command, and pasting the results into a reply to this thread.

```
sudo lshw -class network
```

```
 *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:3b:69:5f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=64 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:d800(size=256) memory:dfffc000-dfffcfff memory:dffc0000-dffdffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfff8000-dfff9fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 10
       serial: 00:10:60:77:2c:68
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.104 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:1c00(size=256) memory:30000000-300001ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:3a:48:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-29-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

---

### Post by GordThompson on 2012-12-16
Okay, so your wireless adapter is a BCM4318. Now please show us the output from

```
lspci -vvnn | grep 14e4
```

---

### Post by beginnerfromfinland on 2012-12-16
> **GordThompson said:**
> Okay, so your wireless adapter is a BCM4318. Now please show us the output from

```
lspci -vvnn | grep 14e4
```

```
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

---

### Post by GordThompson on 2012-12-16
Splendid. With your wired network connection still active, run the following Terminal commands

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```When that is done, restart your notebook and let us know if your wireless adapter is enabled.

---

### Post by beginnerfromfinland on 2012-12-16
> **GordThompson said:**
> Splendid. With your wired network connection still active, run the following Terminal commands

```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```When that is done, restart your notebook and let us know if your wireless adapter is enabled.

Now the text changed. Now it says: "wireless is disabled by hardware switch".  So it has now the firmware but have to find hardware switch. I have tried but no results. Is there any help or something?

---

### Post by Bucky Ball on 2012-12-16
[I]Thread moved to **Networking & Wireless**
[/I]
I think you should also have b43-fwcutter installed:
```

sudo apt-get install b43-fwcutter
```Then restart ...

---

### Post by beginnerfromfinland on 2012-12-16
> **Bucky Ball said:**
> [I]Thread moved to **Networking & Wireless**
[/I]
I think you should also have b43-fwcutter installed:
```

sudo apt-get install b43-fwcutter
```Then restart ...

Something crap before and then this
```
b43-fwcutter is already the newest version.
b43-fwcutter set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
```

---

### Post by Bucky Ball on 2012-12-16
Ok. Run these two commands one after the other. Note: This will NOT upgrade your release to the next, but will upgrade anything you already have installed in the current release:

```
sudo apt-get update
sudo apt-get upgrade
```... then restart. What happened? Maybe then give us the output of:

```
iwconfig
```

---

### Post by beginnerfromfinland on 2012-12-16
You know what. I found the wireless hardware key! It works now and I'm sending this over the air! Thanks a lot for getting the firmware!

So this is now resolved!?

---

### Post by GordThompson on 2012-12-16
> **beginnerfromfinland said:**
> You know what. I found the wireless hardware key! It works now and I'm sending this over the air! Thanks a lot for getting the firmware!
You're welcome.

> **beginnerfromfinland said:**
> So this is now resolved!?
It seems so. Please remember to mark this as [SOLVED] using the "Thread Tools" link near the top of this page.

---

### Post by beginnerfromfinland on 2012-12-16
> **GordThompson said:**
> You're welcome.


It seems so. Please remember to mark this as [SOLVED] using the "Thread Tools" link near the top of this page.

Yes I'll do that. This is great that when someone beginner like me starts using Ubuntu he or she can ask you more experienced users to help. I am seriously going to read this forum and asking more questions when I need help. This is what I haven't found on Windows-world...

---

### Post by Bucky Ball on 2012-12-16
We all started at the beginning. Enjoy the learning curve, the OS and see you round the forums ... ;)

---

