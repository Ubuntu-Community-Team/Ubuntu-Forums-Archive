---
title: "Problems with Sennheiser DW Office Headset"
date: 2012-05-10
forum: Multimedia Software
---

### Post by osjoggl on 2012-05-10
Hi! ):P

I have a problem with this Headset.
You can use it as a USB audio Device, but when I connect it somehow seems to send the signal "left mouse button" down.
Sound works however, is there any way where I can block or modify this input from my headset?

I am using Ubuntu 12.04 64-bit.

Syslog Messages when I plug in the headset:
```
kernel: [10900.074897] usb 1-1.5.5: new full-speed USB device number 19 using ehci_hcd
kernel: [10900.197313] input: Sennheiser Communications Sennheiser DECT as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5.5/1-1.5.5:1.0/input/input28
kernel: [10900.198062] generic-usb 0003:1395:740A.000D: input,hiddev0,hidraw5: USB HID v1.11 Device [Sennheiser Communications Sennheiser DECT] on usb-0000:00:1a.0-1.5.5/input0
mtp-probe: checking bus 1, device 19: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5.5"
kernel: [10901.197176] 19:2:1: cannot get freq at ep 0x4
mtp-probe: bus: 1, device: 19 was not an MTP device
kernel: [10902.195618] 19:3:1: cannot get freq at ep 0x83
kernel: [10903.262004] 19:2:1: cannot get freq at ep 0x4
kernel: [10904.284642] 19:3:1: cannot get freq at ep 0x83
kernel: [10905.342946] 19:3:1: cannot get freq at ep 0x83
kernel: [10906.353707] 19:2:1: cannot get freq at ep 0x4
rtkit-daemon[2271]: Successfully made thread 9884 of process 2513 (n/a) owned by '1000' RT at priority 5.
rtkit-daemon[2271]: Supervising 7 threads of 1 processes of 1 users.
kernel: [10907.391883] 19:3:1: cannot get freq at ep 0x83
rtkit-daemon[2271]: Successfully made thread 9897 of process 2513 (n/a) owned by '1000' RT at priority 5.
rtkit-daemon[2271]: Supervising 8 threads of 1 processes of 1 users.
```

Device shows up as
Bus 001 Device 020: ID 1395:740a Sennheiser Communications

Thanks for your help!
Joachim

---

