---
title: "USB external drive not recognised since 2.6.37-12"
date: 2011-03-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ubername on 2011-03-01
Hi all

Since kernel 2.6.37.12 I get (when I switch on my USB drive)

> Mar  1 23:52:16 localhost kernel: [85842.560033] usb 2-4: new high speed USB device using ehci_hcd and address 8
Mar  1 23:52:16 localhost kernel: [85842.772661] scsi8 : usb-storage 2-4:1.0
Mar  1 23:52:24 localhost kernel: [85849.985966] scsi 8:0:0:0: Direct-Access     USB-HS   ST3320620A       0.01 PQ: 0 ANSI: 0
Mar  1 23:52:24 localhost kernel: [85849.986912] sd 8:0:0:0: Attached scsi generic sg6 type 0
Mar  1 23:52:24 localhost kernel: [85849.990423] sd 8:0:0:0: [sdf] 625142448 512-byte logical blocks: (320 GB/298 GiB)
Mar  1 23:52:24 localhost kernel: [85849.992056] sd 8:0:0:0: [sdf] Write Protect is off
Mar  1 23:52:24 localhost kernel: [85849.992062] sd 8:0:0:0: [sdf] Mode Sense: 0b 00 00 08
Mar  1 23:52:24 localhost kernel: [85850.120050] usb 2-4: reset high speed USB device using ehci_hcd and address 8
Mar  1 23:52:39 localhost kernel: [85865.240040] usb 2-4: device descriptor read/64, error -110

in my message logs, and can not see my external USB drive. It works fine on 2.6.37-12 and earlier. Googling tells me that earler versions could be fixed with

```
modprobe -r ehci_hcd
```

but this doesn't work any more (the following bug describes it, but it's a long time ago - way before 2.6.37-12)

[https://lists.ubuntu.com/archives/kernel-bugs/2010-May/099192.html](https://lists.ubuntu.com/archives/kernel-bugs/2010-May/099192.html)

Any clues?

---

