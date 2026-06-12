---
title: "Intel 5100 won't work after dist-upgrade"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by atcasanova on 2012-03-18
I've just upgraded to 11.10 and my wireless card is not working properly anymore.

```
 dmesg | grep iwl
[   22.101948] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   22.101953] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   22.102025] iwlagn 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.102035] iwlagn 0000:03:00.0: setting latency timer to 64
[   22.102062] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   22.124221] iwlagn 0000:03:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   22.124224] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   22.127777] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   22.127915] iwlagn 0000:03:00.0: irq 47 for MSI/MSI-X
[   22.435246] iwlagn 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[   22.453312] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   65.785062] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 3
[   71.659853] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 7
[   82.666252] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 0
[   88.330188] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 6
[   93.785809] iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because load = 2
[   97.752041] iwlagn 0000:03:00.0: iwlagn_tx_agg_start on ra = 00:26:5a:5a:db:78 tid = 0
[  130.841542] iwlagn 0000:03:00.0: Aggregation not enabled for tid 6 because load = 0
[  314.447807] iwlagn 0000:03:00.0: Aggregation not enabled for tid 6 because load = 2

```

I'm getting these "aggregation not enabled" messages, and i don't have a clue about what that means.

```
lspci -nnk | grep -iA2 network
03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
	Kernel driver in use: iwlagn
```

I made some research and got to install these files: 

linux-headers-3.0.0-0300rc2_3.0.0-0300rc2.201106081532_all.deb
linux-headers-3.0.0-0300rc2-generic_3.0.0-0300rc2.201106081532_i386.deb
linux-image-3.0.0-0300rc2-generic_3.0.0-0300rc2.201106081532_i386.deb

but i've got this problem when installing one of them:

Setting up linux-headers-3.0.0-0300rc2 (3.0.0-0300rc2.201106081532) ...
Setting up linux-headers-3.0.0-0300rc2-generic (3.0.0-0300rc2.201106081532) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-0300rc2-generic /boot/vmlinuz-3.0.0-0300rc2-generic
Error! Could not locate dkms.conf file.
File:  does not exist

---

### Post by praseodym on 2012-03-18
The N-mode of the driver is buggy, deactivate it via

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```

---

### Post by atcasanova on 2012-03-18
i don't know why, but i'm now connected to another router (also N) and things seem alright.

I was connected to a b/g only router before.


$ dmesg | grep iwl
[   21.986043] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   21.986047] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   21.986117] iwlagn 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   21.986128] iwlagn 0000:03:00.0: setting latency timer to 64
[   21.986156] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   22.008154] iwlagn 0000:03:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   22.008158] iwlagn 0000:03:00.0: Device SKU: 0Xb
[   22.008532] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   22.008621] iwlagn 0000:03:00.0: irq 46 for MSI/MSI-X
[   22.515662] iwlagn 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[   22.524449] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

---

### Post by atcasanova on 2012-04-10
any fix for this so far?

---

### Post by atcasanova on 2012-07-02
??? anyone?

---

### Post by praseodym on 2012-07-02
Maybe one of the latest mainline-kernels or the latest driver from "linux-wireless"?

[http://www.linuxwireless.org/](http://www.linuxwireless.org/)

---

