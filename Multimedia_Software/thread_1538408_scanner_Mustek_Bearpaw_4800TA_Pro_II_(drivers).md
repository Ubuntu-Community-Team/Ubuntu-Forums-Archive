---
title: "scanner Mustek Bearpaw 4800TA Pro II (drivers)"
date: 2010-07-25
forum: Multimedia Software
---

### Post by seba22 on 2010-07-25
Welcome,

Any idea how can i make scanner Mustek BearPaw 4800TA Pro II working on Ubuntu 10.04 ?

I try sane, but i don't want recognize.

Syslog
```
Jul 25 09:08:02 administrator-desktop kernel: [10480.272046] usb 3-2: new high speed USB device using ehci_hcd and address 2
Jul 25 09:08:03 administrator-desktop kernel: [10480.406689] usb 3-2: configuration #1 chosen from 1 choice
```

lsub
```
lsusb
(...)
Bus 003 Device 002: ID 055f:040a Mustek Systems, Inc. 
(...)

```

sane-find-scanner
```
sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x055f [Hewlett-Packard.        ], product=0x040a [USB2.0 Scanner            ], chip=SQ113) at libusb:003:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

```



If anyone have any idea... please post it here...
Regards

---

### Post by ScumCoder on 2012-09-24
The most painless way is to install Virtual Box with XP, and install BearPaw driver on it.
[[img]http://img.by/thumbs/csbXg.png[/img]](http://img.by/?v=csbXg.png)

---

