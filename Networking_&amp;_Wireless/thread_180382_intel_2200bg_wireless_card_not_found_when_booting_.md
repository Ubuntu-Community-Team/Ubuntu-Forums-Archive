---
title: "intel 2200bg wireless card not found when booting from new kernel"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by ponkan on 2006-05-22
I did a compile of the new 2.6.16.17 kernel over at kernel.org, running which I could not use my intel 2200 b/g wireless card. I used the vanilla sources from kernel.org, with the exception of the unionfs patch. I followed the instructios found in Documents/networking/README.ipw2200, which consisted of downloading the ipw-2.4 firmware files and unpacking them into /lib/hotplug/firmware.

Booting the new kernel works, though the network card apparently isn't seen by the kernel, it doesn't appear in GNOME's device manager. This happened both with the driver configured as a module, or built-in, which is the current status. The config for my kernel is included if anybody thinks it'll help.

Any help on the matter would be much appreciated, thanks.

---

### Post by ponkan on 2006-05-22
I just found this snippet in /var/log/kern.log, does anyone know what "Reason -2" means?

[SIZE="1"]```
May 22 13:49:41 localhost kernel: [17179597.324000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, git-1.0.8
May 22 13:49:41 localhost kernel: [17179597.324000] ipw2200: Copyright(c) 2003-2005 Intel Corporation
May 22 13:49:41 localhost kernel: [17179597.328000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 17
May 22 13:49:41 localhost kernel: [17179597.328000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May 22 13:49:41 localhost kernel: [17179597.432000] ipw2200: ipw-2.4-boot.fw load failed: Reason -2
May 22 13:49:41 localhost kernel: [17179597.432000] ipw2200: Unable to load firmware: -2
May 22 13:49:41 localhost kernel: [17179597.432000] ipw2200: failed to register network device
May 22 13:49:41 localhost kernel: [17179597.432000] ACPI: PCI interrupt for device 0000:01:05.0 disabled
May 22 13:49:41 localhost kernel: [17179597.432000] ipw2200: probe of 0000:01:05.0 failed with error -5
May 22 13:49:41 localhost kernel: [17179598.412000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800031e712f]

```[/SIZE]

From what I can figure out, the firmware isn't being loaded properly, but that's about it. I thought that maybe /lib/hotplug/firmware was too unstandard (the README used /lib/firmware for its example), so I tries symlinking firmware to hotplug/firmware, same result. Could it be that the hotplug driver/device/service/whatever isn't working properly? If so, how can I diagnose/solve the problem?

---

