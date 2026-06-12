---
title: "Strange Intel-Graphic Video Problem"
date: 2011-11-21
forum: Multimedia Software
---

### Post by d4v1dv00 on 2011-11-21
I had this random display issue ever since Ubuntu 11.04 and now running Ubuntu 11.10 and this problem still persist. It is very hard for me to explain, so I uploaded a video ([http://youtu.be/KxevkWbpWzM](http://youtu.be/KxevkWbpWzM)) to elaborate itself.

Before I convert from Windows 7, this issue never happened. The symptom is so random that I cannot reproduce or tell precisely when will this happen again.

My wild guess is, should this be related to driver? Below are my detail system information:

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)

---

