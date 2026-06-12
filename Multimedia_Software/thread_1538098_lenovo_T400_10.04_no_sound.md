---
title: "lenovo T400 10.04 no sound"
date: 2010-07-24
forum: Multimedia Software
---

### Post by ntrgc89 on 2010-07-24
Something's wrong with my sound (or lack thereof)

Going to System > Prefs > Sound > Hardware tab does not list any devices.

lspci gives the following:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)**
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 11)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)

```

and aplay -l gives:

```
aplay: device_list:223: no soundcards found...

```

Any ideas? Any more info I can give??

---

### Post by Yellow Pasque on 2010-07-24
Maybe dmesg will show exactly why the kernel module isn't loading:
```
dmesg
```

---

### Post by ntrgc89 on 2010-08-08
So, I ended up having to reinstall ubuntu for other reasons, and now the sound works. It's a shame we couldn't resolve the issue, but if I have problems again I'll just try to revert to this thread.

---

### Post by alphacrucis2 on 2010-08-08
> **ntrgc89 said:**
> So, I ended up having to reinstall ubuntu for other reasons, and now the sound works. It's a shame we couldn't resolve the issue, but if I have problems again I'll just try to revert to this thread.

I am running 10.04 on a T400 and have no sound problems but it was also a fresh install. Perhaps the issue pertains to upgrading from previous versions?

---

### Post by simosx on 2010-08-09
> **alphacrucis2 said:**
> I am running 10.04 on a T400 and have no sound problems but it was also a fresh install. Perhaps the issue pertains to upgrading from previous versions?

It could be an upgrade issue; many users perform drastic modifications in their installation and upgrades tend to become a nightmare.
The typical advice is to use separate partitions for / and /home, so that you always re-format the root partition when you install the new version of Ubuntu. You can keep the /home partition as is.

---

