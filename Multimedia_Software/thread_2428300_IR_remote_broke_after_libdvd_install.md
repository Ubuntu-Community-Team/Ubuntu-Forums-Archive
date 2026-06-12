---
title: "IR remote broke after libdvd install"
date: 2019-10-02
forum: Multimedia Software
---

### Post by ryan1209 on 2019-10-02
I have a HTPC running Ubuntu 18.04 with MythTV .29.  My RC 6 ir remote control quite working after I installed libdvd.

Here is what comes up with dmesg:

[    1.924043] usb 1-1.2: new full-speed USB device number 4 using ehci-pci
[    2.004033] usb 1-1.2: device descriptor read/64, error -32
[    2.191975] usb 1-1.2: device descriptor read/64, error -32
[    2.300093] usb 1-1-port2: attempt power cycle
[    2.904019] usb 1-1.2: new full-speed USB device number 5 using ehci-pci
[    3.320036] usb 1-1.2: device not accepting address 5, error -32
[    3.400031] usb 1-1.2: new full-speed USB device number 6 using ehci-pci
[    3.816031] usb 1-1.2: device not accepting address 6, error -32
[    3.816249] usb 1-1-port2: unable to enumerate USB device
[    4.507971] usb 1-1.2: new full-speed USB device number 7 using ehci-pci
[    4.587969] usb 1-1.2: device descriptor read/64, error -32
[    5.103970] usb 1-1.2: new full-speed USB device number 8 using ehci-pci
[    5.848031] usb 1-1.2: device descriptor read/64, error -32
[    6.035972] usb 1-1.2: device descriptor read/64, error -32
[    6.144056] usb 1-1-port2: attempt power cycle
[    6.995971] usb 1-1.2: new full-speed USB device number 9 using ehci-pci
[    7.411978] usb 1-1.2: device not accepting address 9, error -32
[    7.491970] usb 1-1.2: new full-speed USB device number 10 using ehci-pci
[    7.908031] usb 1-1.2: device not accepting address 10, error -32
[    7.908249] usb 1-1-port2: unable to enumerate USB device
[    8.131971] usb 1-1.2: new full-speed USB device number 11 using ehci-pci
[    8.211973] usb 1-1.2: device descriptor read/64, error -32
[    8.975970] usb 1-1.2: new high-speed USB device number 12 using ehci-pci
[    9.068056] usb 1-1-port2: attempt power cycle
[   10.603971] usb 1-1.2: new full-speed USB device number 14 using ehci-pci
[   10.683969] usb 1-1.2: device descriptor read/64, error -32
[   11.535969] usb 1-1.2: device descriptor read/64, error -32
[   11.971970] usb 1-1.2: new high-speed USB device number 15 using ehci-pci
[   12.064057] usb 1-1-port2: attempt power cycle
[   12.668027] usb 1-1.2: new full-speed USB device number 16 using ehci-pci
[   13.084026] usb 1-1.2: device not accepting address 16, error -32
[   13.620027] usb 1-1.2: new full-speed USB device number 17 using ehci-pci
[   14.036040] usb 1-1.2: device not accepting address 17, error -32
[   14.036247] usb 1-1-port2: unable to enumerate USB device
[ 1471.809832] usb 1-1.1: new full-speed USB device number 18 using ehci-pci
[ 1471.889863] usb 1-1.1: device descriptor read/64, error -32
[ 1472.077834] usb 1-1.1: device descriptor read/64, error -32
[ 1472.265840] usb 1-1.1: new full-speed USB device number 19 using ehci-pci
[ 1472.345841] usb 1-1.1: device descriptor read/64, error -32
[ 1472.533808] usb 1-1.1: device descriptor read/64, error -32
[ 1472.641888] usb 1-1-port1: attempt power cycle
[ 1473.245874] usb 1-1.1: new full-speed USB device number 20 using ehci-pci
[ 1473.661880] usb 1-1.1: device not accepting address 20, error -32
[ 1473.741878] usb 1-1.1: new full-speed USB device number 21 using ehci-pci
[ 1474.157852] usb 1-1.1: device not accepting address 21, error -32
[ 1474.158037] usb 1-1-port1: unable to enumerate USB device

Has anyone else experienced this?

---

