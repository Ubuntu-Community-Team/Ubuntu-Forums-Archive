---
title: "Friends laptop won't detect wireless."
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by KruSuPhy on 2011-07-22
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

There's the 'lspci' thing ^^^^
Okay, so I'm at my friends house, and I decided I was finally going to get ubuntu back(i had it for a little while a long time ago, finally decided I wanted it back.)
I showed him ubuntu, and he's like 'ooh, i want it.' so, we got it for him.
However, his laptop won't detect his wireless connection. Mine connected fine.
Also, we have the same laptop, just different models.
So, can you guys help? Is there more information that you need?

---

### Post by KruSuPhy on 2011-07-22
help, please. D:
By the way, he rebooted up to windows 7(he has both on his system, win and ubuntu), and his internet worked fine. so it's got to be something with ubuntu.

---

### Post by chili555 on 2011-07-22
> Network controller: Ralink corp. Device 5390Oooh, fun! It needs a driver that's not natively built-in to Ubuntu because the chipset is quite new. Please check here at post #9 and following. [http://ubuntuforums.org/showthread.php?t=1743525&highlight=5390](http://ubuntuforums.org/showthread.php?t=1743525&highlight=5390)

If you get stuck or don't understand some point, please post back.

---

