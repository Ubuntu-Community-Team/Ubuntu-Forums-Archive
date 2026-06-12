---
title: "ASUS N13 USB Adapter not working; module can't load"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by rfkrocktk on 2012-01-09
I just got an ASUS N13 USB wireless dongle, and unfortunately it's not detected and I can't load it with modprobe:

```
$ sudo modprobe rt2800usb

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting rt2x00usb (/lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko): Invalid argument
WARNING: Error inserting crc_ccitt (/lib/modules/3.0.0-14-generic/kernel/lib/crc-ccitt.ko): Invalid argument
WARNING: Error inserting rt2800lib (/lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko): Invalid argument
FATAL: Error inserting rt2800usb (/lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko): Invalid argument

```

What's the problem here? I read that this works usually out of the box with Ubuntu 11.10? What can I do to fix this? Is there a package I can reinstall to try and fix things?

---

