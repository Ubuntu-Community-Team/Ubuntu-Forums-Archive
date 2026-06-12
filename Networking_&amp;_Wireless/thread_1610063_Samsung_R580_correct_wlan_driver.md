---
title: "Samsung R580 correct wlan driver"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by izzydog on 2010-10-31
Hi everyone,
             I've recently bought a Samsung R580 laptop.   It is now configured as a dual boot system with Ubuntu 10.10 and Windows 7 (64bit).  The wireless network functions correctly under Win7, but I have encountered problems with Ubuntu.   The native drivers do not function and having identified the driver used by Win7 (net819xp.inf) that works, I have tried to install it using ndisgtk, but get the message "incorrect hardware".  I have followed the ndiswrapper howto carefully without being able to get the wireless network going.   Any help would be most appreciated

---

### Post by P4man on 2010-10-31
Are you sure you need ndiswrapper? What wifi card do you have? If unsure, provide the output of

```
lspci
```

If ndiswrapper is the only way to go, make sure you use 64 bit windows drivers for 64 bit ubuntu and 32 bit drivers for 32 bit ubuntu

---

### Post by izzydog on 2010-10-31
Thankyou for your reply.   Here is the output from "lspci" that shows the presence of the Realtek 8192E (rev 01) chip.   I have tried the native ubuntu drivers without success and Realtek emailed me the drivers, they did not work, nor did the wireless drivers provided by Samsung on the recovery disc even though they work when using Win7.
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8059 PCI-E Gigabit Ethernet Controller (rev 11)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Many thanks for your help

---

### Post by P4man on 2010-10-31
Seems to be a rather problematic chipset, but some people have gotten it to work:
[http://ubuntuforums.org/showthread.php?t=1460038](http://ubuntuforums.org/showthread.php?t=1460038)

It seems the 64 bit drivers have more issues than the 32 bit ones. Which version of ubuntu are you using? Thats also relevant for ndiswrapper; like I said you need 32 cf 64 bit (windows) drivers for 32 cf 64 bit ubuntu in ndiswrapper.

---

### Post by izzydog on 2010-10-31
Thanks again for your help.   I will study the thread that you have posted.   From a brief inspection, I know that I have tried some of the suggestions included in the thread and I note that I am not the only sufferer of a driver working successfully under Windows that does not perform in the same manner with Ubuntu.   I have been careful to match up the drivers to the processor in terms of bits, although I dislike Windows I will tolerate using it for the present, whilst I persevere with Ubuntu.   Out of interest I am only using Windows because my granddaughters are obliged to use it for school and university!!!!   Will post a further reply when I have studied the thread carefully.

---

