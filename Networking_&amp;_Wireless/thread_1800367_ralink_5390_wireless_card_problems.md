---
title: "ralink 5390 wireless card problems"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by andrewmartz93 on 2011-07-08
i have a compaq presario cq56 dual booting windows 7 and ubuntu, and i cannot get any wireless to work, network connections just shows wired connections. ive done the lspci command and this is what i got 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Ralink corp. Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
if anyone could help me get my wireless connection to work, that would be great.

---

### Post by ratcheer on 2011-07-08
I need to see output of "sudo lspci -v". Just the section of the output for the Ralink card.

Tim

---

### Post by andrewmartz93 on 2011-07-08
02:00.0 Network controller: Ralink corp. Device 5390
    Subsystem: Hewlett-Packard Company Device 1636
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 93500000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-00-2f-e0-4d-fa-9f-88

does that help at all, im a first time ubuntu user, and have no idea what any of that means

---

### Post by ratcheer on 2011-07-09
It does not appear that a driver has been installed for that device. Is it a USB or PCIe device?

The driver and firmware can be downloaded from this page: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

It is likely that your system only needs the driver. But, it should already have it. If you have to install it yourself, it will be some fairly detailed work. I hope someone else can tell you how to fix it in a simpler fashion.

Tim

---

### Post by chili555 on 2011-07-09
I'll be happy to help. Please see: [http://ubuntuforums.org/showthread.php?t=1779005&highlight=5390](http://ubuntuforums.org/showthread.php?t=1779005&highlight=5390)

Although the thread refers to 64-bit, you simply need to omit the x86_64 patch. Be sure you install, through Synaptic, for example, build-essential and linux-headers-generic before you start.

Post back if you need more help.

---

### Post by andrewmartz93 on 2011-07-09
ok, ive tried what you told me, but still no luck, i feel like im missing something, like after doing the work in the terminal, nothing happens
ive tried it twice now, and nothing happened either time

---

### Post by chili555 on 2011-07-09
Let's see if the module got built correctly:```
sudo modprobe rt5390sta
```If nothing comes back, it inserted correctly with no errors. Now check:```
iwconfig
```Did an interface get created, wlan0 perhaps? Now click the Network Manager icon. Do you see networks?

---

### Post by andrewmartz93 on 2011-07-09
i went through it one more time, and this time it worked, got a lot of warnings, but i am successfully online wireless on my machine, thanks for all your help. :)

---

### Post by chili555 on 2011-07-09
Good job! Perhaps you'd like to use thread tools at the top and Mark Solved.

---

### Post by andrewmartz93 on 2011-07-09
the problem was in the code box where you listed the steps, you cannot just copy and paste it all, you have to go step by step, and i didnt know that

---

