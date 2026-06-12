---
title: "iwl3945 Major Failure"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by seurimas on 2009-06-29
I recently updated to hardy from dapper, and while testing some things, I hit my wireless kill switch (fn+F2). I can't get it working again. However, I also might be having some problems with wired connection, as attempting to do anything to either my wired or wireless connection results in similar error messages from network manager. And attempting to connect to a wired connection failed, but I'm not especially certain it would have worked if my computer were in top form.

Unfortunately, this also means I have no means to transfer any logs from my computer to this board. I've poured over a few dozen pages thus far for a fix. The rmmod/modprobe combo does nil (there's some system log messages below) in the long run. I'll do my best to explain some of the system log messages I've gotten thus far...

When hitting the switch, turning wireless off:
> iwl945: Radio Frequency Kill Switch is On:
Kill switch must be turned off for wireless networking to work.No message when turning it on.

When rmmod/modprobe:
> APCI: PCI interrupt for device 0000:0b:00.0 disabled
iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
iwl3945: Copyright(c) 2003-2007 Intel Corporation
ACPI: PCI Interrupt 0000:0b:00.0[a] -> GSI 16 (level, low) -> IRQ 16
iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
udev: renamed network interface wlan0 to eth1
ADDRCONF(NETDEV_UP): eth1: link is not readyIn rare (once among dozens of attempts) occassions, it'll state that link is now ready a few seconds later.

---

