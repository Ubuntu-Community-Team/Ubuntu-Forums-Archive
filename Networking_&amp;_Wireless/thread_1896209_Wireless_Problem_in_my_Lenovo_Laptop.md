---
title: "Wireless Problem in my Lenovo Laptop"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by afesheir on 2011-12-16
Dear all,

I've bought Lenovo B560 Laptop with Broadcom 802.11n wireless adaptor ..  I've installed Ubuntu 11.10 linux on it and I see the (Enable Wireless)  option at the upper right corner of the screen (near battery icon and  data/time), but it's dimmed option and a message (Wireless is disabled by hardware switch) !!

Actually I can't scan for wireless networks in range !!

the following package is installed:
** bcmwl-kernel-source 5.100.82.38+bdcom-0ubuntu4**

and from (Additional Drivers), it says that my adaptor is OK and ready for work, which isn't the case !!

The output of **lcpsi** is:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```
The output of **rfkill list** all is:
```

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```I've issued **rfkill unblock all** command, but in vain !!


Please help & great thanks in advance :grin:

---

### Post by praseodym on 2011-12-16
Any buttons/switches/keys/key combianations? Checked the BIOS settings? BIOS reset?

---

### Post by afesheir on 2011-12-17
key combinations (Fu + F5) works perfectly on Windows 7 !! Wireless is disabled on Ubuntu only but seems fine on Windows 7

---

### Post by praseodym on 2011-12-17
Does Windows shut off the card in its default settings? Is there sth. like "last state" for wireless in the BIOS settings?

---

### Post by afesheir on 2011-12-17
how to check this issue in BIOS ? how to check whether windows disables the adapter after shutdown as well ?

---

### Post by praseodym on 2011-12-17
Somewhere in the Windows network settings. Try F1 to reach the BIOS during boot-up, F9 to reset the BIOS and F10 to save&exit. After that press the Power button for 10 seconds if the Lenovo screen appears to shut off. Switch it on after that again

---

### Post by afesheir on 2011-12-17
aha .. I was asking from Windows and now I'm online from Ubuntu !! I actually don't know what happened but it worked fine now !!! I'm really amazed !!!

Anyway thanks for your interest and help offers :D

---

