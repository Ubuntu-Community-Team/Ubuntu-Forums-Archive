---
title: "RT3290 issue on 12.04"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by laci37 on 2013-04-26
I have just bought an HP laptop with Ralink RT3290 wi-fi card. Yesterday I have managed to install the 3.8.8 kernel and the wi-fi worked, but today it says "Device not ready". Here is what I found in dmesg:


mero@meroPavilion:~$ dmesg | grep rt2
[   21.957797] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
[   23.554853] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
[   23.554864] phy0 -> rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5).
[   25.586956] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
[   27.183967] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
[   27.183974] phy0 -> rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5).
[   28.796975] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
[   30.393920] phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068].
[   30.393924] phy0 -> rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5).

The only thing that changed is that I tried to install AMD Catalyst, and had to revert to defaults. Somewhy I can't install graphics drivers from "Additional drivers".
The wi-fi card has a launchpad bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

Any ideas? I read on launchpad that it works with 3.6.6 kernel. Should I revert?

---

