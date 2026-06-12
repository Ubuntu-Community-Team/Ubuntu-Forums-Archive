---
title: "Help with USB modem drivers using package eciadsl"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by skt on 2010-08-01
I have a Nokia Siemens Networks C2110 USB IAD LAN modem. The modem is not recognized when connected through USB.

lsusb output is :
```
me@ubuntu:/dev/bus$ lsusb
Bus 002 Device 011: ID 0915:0005 GlobeSpan, Inc. LAN Modem
Bus 002 Device 008: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I installed the eciadsl-usermode package. It installed fine, but doesnt work. The output to the eciadsl-start command is as follows :

```
me@ubuntu:/dev/bus$ eciadsl-start

Warning: couldn't find /etc/eciadsl/eciadsl.conf, default config assumed

[EciAdsl 1/5] Setting up USB support...

FATAL: Module usbcore not found.
Preliminary USB device filesystem is missing... trying to mount
Preliminary USB device filesystem: failed to load
/usr/bin/eciadsl-start: line 263: fatal: command not found
cat: /proc/bus/usb/devices: No such file or directory
Loading UHCI support... Warning: uhci-hcd module doesn't exist

[EciAdsl 2/5] Uploading firmware...

grep: /proc/bus/usb/devices: No such file or directory
grep: /proc/bus/usb/devices: No such file or directory
ERROR: modem not found
```

I tried loading usbcore with modprobe with this result..
```
me@ubuntu:/dev/bus$ sudo modprobe usbcore
FATAL: Module usbcore not found.
```

Please help !!!

---

