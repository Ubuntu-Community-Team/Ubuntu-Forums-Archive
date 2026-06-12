---
title: "Ubuntu is disabling my wireless card"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by basha312 on 2010-06-26
Im running Ubuntu 10.04 and Windows 7 on an HP Pavilion dv5. My wireless card works fine in windows but when I boot to ubuntu it becomes disabled and I am unable to re enable from Ubuntu

---

### Post by wilee-nilee on 2010-06-26
> **basha312 said:**
> Im running Ubuntu 10.04 and Windows 7 on an HP Pavilion dv5. My wireless card works fine in windows but when I boot to ubuntu it becomes disabled and I am unable to re enable from Ubuntu

This is a internal card I assume, have you looked in system-admin-hardware drivers to see if a driver is offered for it?

You can also from the Ubuntu terminal run and post the read out to identify hardware. 
```
lspci
```

If it is a external plugin tell us what it is.

---

### Post by basha312 on 2010-06-26
The readout for that command is as follows sorry I wasnt sure which information you needed
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
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
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by wilee-nilee on 2010-06-26
Was any driver offered in the hardware drivers area I said to look?

Can the Ubuntu OS get on the net plugged in with Ethernet?

---

### Post by basha312 on 2010-06-26
no drivers pop up on there and yes it can access the Internet via Ethernet cable

---

### Post by wilee-nilee on 2010-06-26
> **basha312 said:**
> no drivers pop up on there and yes it can access the Internet via Ethernet cable

So the culprit is the broadcom card, I'm not real familiar with these problems so I just go to the net and I found this UF link.
[http://ubuntuforums.org/showthread.php?t=948431](http://ubuntuforums.org/showthread.php?t=948431)

I see threads about these cards I'm not sure how many versions there are.

---

