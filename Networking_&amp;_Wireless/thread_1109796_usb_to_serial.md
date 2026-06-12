---
title: "usb to serial"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by binary_dreamer on 2009-03-29
Hi. i am running 8.10 desktop in my laptop and i would like to connect to a cisco router via a usb to serial converter. the problem is that when in minicom i cannot see the outcome.
here is the output of lsusb:
binary@ubuntu:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 006 Device 003: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
binary@ubuntu:~$ 


my question is which device is the usb to serial attached to and how do i find it?

---

### Post by namaku0 on 2009-03-29
There is a possibility the device node is /dev/ttyUSB0,
but it could be others.

Look at **dmesg** output just right after you plug
the converter.

---

### Post by sanderj on 2009-03-29
Make sure the ftdi module is loaded: check with 

```
lsmod  | grep ftdi
```


Then: "The serial ports should install as /dev/ttyUSBx devices", so check /dev/ttyUSB0, /dev/ttyUSB1, etc.

HTH

---

