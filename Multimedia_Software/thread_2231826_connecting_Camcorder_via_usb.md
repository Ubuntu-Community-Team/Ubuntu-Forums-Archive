---
title: "connecting Camcorder via usb"
date: 2014-06-28
forum: Multimedia Software
---

### Post by hbrandt on 2014-06-28
I'm using ubuntu 14.04.
I'm trying to connect a canon camcorder via usb to ubuntu:
Linux Carlo 3.13.0-29-generic #52-Ubuntu SMP Wed May 28 12:42:47 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
tail -f /var/log/syslog:
May 25 17:12:00 Carlo kernel: [30420.725880] usb 2-6: new high-speed USB device number 5 using ehci-pci
May 25 17:12:00 Carlo kernel: [30420.863785] usb 2-6: New USB device found, idVendor=04a9, idProduct=328c
May 25 17:12:00 Carlo kernel: [30420.863790] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May 25 17:12:00 Carlo kernel: [30420.863792] usb 2-6: Product: Canon Video Camera
May 25 17:12:00 Carlo kernel: [30420.863794] usb 2-6: Manufacturer: CANON Inc.
May 25 17:12:00 Carlo kernel: [30420.863796] usb 2-6: SerialNumber: C40100000000000000000002C2700300
May 25 17:12:00 Carlo mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-6"
May 25 17:12:00 Carlo mtp-probe: bus: 2, device: 5 was not an MTP device
May 25 17:12:00 Carlo colord: Device added: sysfs-(null)
May 25 17:12:01 Carlo kernel: [30421.708101] delay: estimated 336, actual 96

df shows nothing.

I've tried an other system:
Linux Cera-II 2.6.32-58-generic-pae #121-Ubuntu SMP Fri May 2 21:49:01 UTC 2014 i686 GNU/Linux

May 26 17:19:21 Cera-II kernel: [  120.648019] usb 1-5: new high speed USB device using ehci_hcd and address 5
May 26 17:19:21 Cera-II kernel: [  120.781232] usb 1-5: configuration #1 chosen from 1 choice

works at a glance, but very slow,

How can I get the first system to support my camcorder via usb?

---

### Post by hbrandt on 2014-09-25
The answer is:
Wait until a patch solves the problem:
from dmesg
usb 2-5: new high-speed USB device number 3 using ehci-pci
[  608.123886] usb 2-5: New USB device found, idVendor=04a9, idProduct=328c
[  608.123899] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  608.123906] usb 2-5: Product: Canon Video Camera
[  608.123912] usb 2-5: Manufacturer: CANON Inc.
[  608.123916] usb 2-5: SerialNumber: C40100000000000000000002C2700300

so far everything is o.k.:smile:

---

