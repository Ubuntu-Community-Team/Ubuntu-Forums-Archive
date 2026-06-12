---
title: "Ubuntu 11.10 64-bit Dell laptop wireless problem"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by onurozcelik on 2012-03-31
Hi guys,

I have a Dell Laptop 14z N411z laptop. It comes with Windows 7 64-bit OS .
Also I installed Ubuntu 11.10 64-bit edition.
My laptop sees wireless networks bu can't connect to them. It gives wrong password error even if I make the network unsafe.
When I tried with Ubuntu 11.10 32-bit edition it successfully connects wireless networks.
Below is the lspci output.

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
04:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)

How can I solve it?

---

### Post by praseodym on 2012-03-31
Hi,

deactivate the N-mode of the driver:

> echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
and reboot.

---

### Post by onurozcelik on 2012-03-31
Hi,

I tried your suggestion but not worked for me.
Same error again.:(

---

