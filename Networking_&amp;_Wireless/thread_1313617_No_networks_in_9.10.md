---
title: "No networks in 9.10"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by nuvan on 2009-11-03
I have just upgraded my laptop to 9.10 from 9.04, and it now has no network connectivity. It was working fine in 9.04.

I tried a clean install, same result.

Both the Broadcom BCM5784M ethernet and the Atheros AR928X wireless controller say *-network UNCLAIMED in lshw.

checking dmesg, I found this for the atheros, couldn't find anything for the broadcom...

```
ath9k: Driver unloaded
ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low0 -> IRQ 16
ath9k 0000:02:00.0: setting latency timer to 64
ath9k: timeout (100000 us) on reg 0x7044: 0x2ecd55bd & 0x0000000f != 0x00000002
ath9k: Couldn't reset chip
ath9k: Unable to attach hardware; HAL status -5
ath9k: 0000:02:00.0: PCI INT A disabled
```

Please help!

---

### Post by nuvan on 2009-11-04
new info: wlan0 and eth0 are present if I boot with acpi=off

---

### Post by nuvan on 2009-11-09
further update: if I boot with acpi=off, I can get online using eth0, but wlan0 will not see any networks, and I cannot force it to connect by entering the SSID...

---

### Post by echo6 on 2010-01-24
I have similar with a device reported as AR5008 rev01

> [  446.480440] ath9k 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  446.480455] ath9k 0000:06:00.0: setting latency timer to 64
[  446.582176] ath9k: timeout (100000 us) on reg 0x7044: 0x127a3270 & 0x0000000f != 0x00000002
[  446.582186] ath9k: Couldn't reset chip
[  446.582190] ath9k: Unable to initialize hardware; initialization status: -5
[  446.582262] ath9k 0000:06:00.0: failed to initialize device
[  446.582292] ath9k 0000:06:00.0: PCI INT A disabled
[  446.582308] ath9k: probe of 0000:06:00.0 failed with error -5

---

