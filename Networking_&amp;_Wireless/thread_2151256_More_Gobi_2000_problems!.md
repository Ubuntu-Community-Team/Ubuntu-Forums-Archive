---
title: "More Gobi 2000 problems!"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by NomadAU on 2013-06-03
Hi,

I've been trying to diagnose networking problems with my Gobi 2000 under Ubuntu 12.04 LTS for some time now without much progresss ([http://ubuntuforums.org/showthread.php?t=2131762&highlight=gobi+2000](http://ubuntuforums.org/showthread.php?t=2131762&highlight=gobi+2000)).

The problem has now got to the point where I can no longer use my 3G, even after a reboot.  I'm posting what I hope is some relevant diagnostic information here, hoping that someone will spot what is going wrong, or advise on further diagnostics that I should provide.

Looking through many similar posts, the sort of information that is often asked for is as follows.

lsmod | grep qcserial
```

qcserial               12822  1
usb_wwan               20491  1 qcserial
usbserial              47077  4 qcserial,usb_wwan

```

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 004: ID 17ef:480f Lenovo Integrated Webcam [R5U877]
Bus 003 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 64MB QDI U2 DISK
Bus 002 Device 004: ID 05c6:9204 Qualcomm, Inc. 
Bus 002 Device 007: ID 04b3:3107 IBM Corp. ThinkPad 800dpi Optical Travel Mouse

```

I have no entry for the Gobi 2000 in /lib/udev/rules.d/40-usb_modeswitch.rules.

I have the following relevant entry in vi /lib/udev/rules.d/60-gobi.rules.
```

ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="9204", RUN+="gobi_loader -2000 $env{DEVNAME} /lib/firmware/gobi"

```

After reboot, the Gobi entry is not visible in the Network Manager pulldown and the syslog contains the following relevant information.

```

Jun  4 12:27:17 taroona kernel: [   25.233540] usbcore: registered new interface driver usbserial
Jun  4 12:27:17 taroona kernel: [   25.233553] USB Serial support registered for generic
Jun  4 12:27:17 taroona kernel: [   25.233592] usbcore: registered new interface driver usbserial_generic
Jun  4 12:27:17 taroona kernel: [   25.233594] usbserial: USB Serial Driver core
Jun  4 12:27:17 taroona kernel: [   25.284486] USB Serial support registered for Qualcomm USB modem
Jun  4 12:27:17 taroona kernel: [   25.284543] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
Jun  4 12:27:17 taroona kernel: [   25.284821] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
Jun  4 12:27:17 taroona kernel: [   25.284866] usbcore: registered new interface driver qcserial

```

and 
```

Jun  4 12:28:16 taroona udevd[483]: timeout 'gobi_loader /dev/ttyUSB0 /lib/firmware/gobi'
Jun  4 12:28:17 taroona udevd[483]: timeout: killing 'gobi_loader /dev/ttyUSB0 /lib/firmware/gobi' [840]
Jun  4 12:28:17 taroona udevd[483]: 'gobi_loader /dev/ttyUSB0 /lib/firmware/gobi' [840] terminated by signal 9 (Killed)

```

This last extract doesn't look good... why is the gobi_loader timing out?  
There are no previous entries for udevd[483] prior to this action...


Can anyone help me out here...?  Is there any other diagnostic data that would help nail this problem?
Thanks in advance!

---

### Post by NomadAU on 2013-06-04
Hi,

This problem seems to keep 'moving' around making it very difficult to diagnose.  I've just rebooted my TP (warm restart) and lo and behold, the gobi_loader is executing succesfully!  The Gobi entry is now appearing in my Network Manager pulldown, but...when I select it, it fails to establish a connection.  Here's some snippets from syslog and some large chunks of syslog, if anyone is interested in taking a look :-)

qcserial running...
```

Jun  5 10:16:18 taroona kernel: [   30.091376] usbcore: registered new interface driver usbserial_generic
Jun  5 10:16:18 taroona kernel: [   30.091378] usbserial: USB Serial Driver core
Jun  5 10:16:18 taroona kernel: [   30.093660] USB Serial support registered for Qualcomm USB modem
Jun  5 10:16:18 taroona kernel: [   30.093694] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
Jun  5 10:16:18 taroona kernel: [   30.093801] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
Jun  5 10:16:18 taroona kernel: [   30.093828] usbcore: registered new interface driver qcserial

```

I've extracted the udev daemon entries that process this device
```

Jun  5 10:16:19 taroona udevd[483]: 'gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi' [831] exit with return code 0
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2308 processed with 0
Jun  5 10:16:19 taroona udevd[483]: seq 2417 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748226800 has devpath '/devices/virtual/bdi/0:19'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/+bdi:0:19: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/+bdi:0:19' for '/devices/virtual/bdi/0:19'
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2417 processed with 0
Jun  5 10:16:19 taroona udevd[483]: seq 2418 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748213720 has devpath '/module/vmnet'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/+module:vmnet: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/+module:vmnet' for '/module/vmnet'
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2418 processed with 0
Jun  5 10:16:19 taroona udevd[483]: seq 2419 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748226800 has devpath '/module/vesafb'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/+module:vesafb: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/+module:vesafb' for '/module/vesafb'
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2419 processed with 0
Jun  5 10:16:19 taroona udevd[483]: seq 2421 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748215410 has devpath '/devices/platform/vesafb.0/graphics/fb0'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/c29:0: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa74822b180 has devpath '/devices/platform/vesafb.0'
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748215000 has devpath '/devices/platform'
Jun  5 10:16:19 taroona udevd[483]: GROUP 44 /lib/udev/rules.d/50-udev-default.rules:38
Jun  5 10:16:19 taroona udevd[483]: RUN '/sbin/modprobe -q fbcon' /lib/udev/rules.d/80-drivers.rules:12
Jun  5 10:16:19 taroona udevd[483]: no node name set, will use kernel supplied name 'fb0'
Jun  5 10:16:19 taroona udevd[483]: creating device node '/dev/fb0', devnum=29:0, mode=0660, uid=0, gid=44
Jun  5 10:16:19 taroona udevd[483]: preserve file '/dev/fb0', because it has correct dev_t
Jun  5 10:16:19 taroona udevd[483]: set permissions /dev/fb0, 020660, uid=0, gid=44
Jun  5 10:16:19 taroona udevd[483]: creating symlink '/dev/char/29:0' to '../fb0'
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/c29:0' for '/devices/platform/vesafb.0/graphics/fb0'
Jun  5 10:16:19 taroona udevd[483]: '/sbin/modprobe -q fbcon' [1240] exit with return code 0
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2421 processed with 0
Jun  5 10:16:19 taroona udevd[483]: seq 2424 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748213720 has devpath '/module/dm_crypt'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/+module:dm_crypt: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/+module:dm_crypt' for '/module/dm_crypt'
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2424 processed with 0
Jun  5 10:16:20 taroona udevd[483]: seq 2426 running
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa7482157a0 has devpath '/devices/virtual/net/vmnet1'
Jun  5 10:16:20 taroona udevd[483]: no db file to read /run/udev/data/n4: No such file or directory
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/n4' for '/devices/virtual/net/vmnet1'
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2426 processed with 0
Jun  5 10:16:20 taroona udevd[483]: seq 2427 running
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/virtual/net/vmnet1'
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/+queues:rx-0' for '/devices/virtual/net/vmnet1/queues/rx-0'
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2427 processed with 0
Jun  5 10:16:20 taroona udevd[483]: seq 2429 running
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa7482157a0 has devpath '/devices/virtual/net/vmnet8'
Jun  5 10:16:20 taroona udevd[483]: no db file to read /run/udev/data/n5: No such file or directory
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/n5' for '/devices/virtual/net/vmnet8'
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2429 processed with 0
Jun  5 10:16:20 taroona udevd[483]: seq 2430 running
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/virtual/net/vmnet8'
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/+queues:rx-0' for '/devices/virtual/net/vmnet8/queues/rx-0'
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2430 processed with 0
Jun  5 10:16:20 taroona udevd[483]: seq 2432 running
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748226ca0 has devpath '/bus/acpi/drivers/NVIDIA ACPI Video Driver'
Jun  5 10:16:20 taroona udevd[483]: no db file to read /run/udev/data/+drivers:NVIDIA ACPI Video Driver: No such file or directory
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748226a70 has devpath '/bus/acpi/drivers'
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748227020 has devpath '/bus/acpi'
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/+drivers:NVIDIA ACPI Video Driver' for '/bus/acpi/drivers/NVIDIA ACPI Video Driver'
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2432 processed with 0
Jun  5 10:16:21 taroona udevd[483]: seq 2433 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227020 filled with db file data
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227280 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748214490 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748214bf0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227730 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[483]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:21 taroona udevd[483]: no reference left, remove '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0'
Jun  5 10:16:21 taroona udevd[483]: no reference left, remove '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.1-port0'
Jun  5 10:16:21 taroona udevd[483]: device node '/dev/ttyUSB0' not found
Jun  5 10:16:21 taroona udevd[483]: removing device node '/dev/ttyUSB0'
Jun  5 10:16:21 taroona udevd[483]: '/etc/.mplab_ide/mchplinusbdevice remove ' [1644] exit with return code 0
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2433 processed with 0
Jun  5 10:16:21 taroona udevd[483]: seq 2434 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227730 filled with db file data
Jun  5 10:16:21 taroona udevd[483]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:21 taroona udevd[483]: '/etc/.mplab_ide/mchplinusbdevice remove ' [1645] exit with return code 0
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2434 processed with 0
Jun  5 10:16:21 taroona udevd[483]: seq 2435 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748215770 filled with db file data
Jun  5 10:16:21 taroona udevd[483]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:21 taroona udevd[483]: '/etc/.mplab_ide/mchplinusbdevice remove 5c6/9204/2' [1646] exit with return code 0
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2435 processed with 0
Jun  5 10:16:21 taroona udevd[483]: seq 2436 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748215770 filled with db file data
Jun  5 10:16:21 taroona udevd[483]: IMPORT builtin 'usb_id' /lib/udev/rules.d/50-udev-default.rules:56
Jun  5 10:16:21 taroona udevd[483]: No USB vendor information available
Jun  5 10:16:21 taroona udevd[483]: IMPORT builtin 'usb_id' returned non-zero
Jun  5 10:16:21 taroona udevd[483]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:21 taroona udevd[483]: device node '/dev/bus/usb/002/004' not found
Jun  5 10:16:21 taroona udevd[483]: removing device node '/dev/bus/usb/002/004'
Jun  5 10:16:21 taroona udevd[483]: '/etc/.mplab_ide/mchplinusbdevice remove 5c6/9204/2' [1647] exit with return code 0
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2436 processed with 0
Jun  5 10:16:21 taroona udevd[483]: seq 2437 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-0'
Jun  5 10:16:21 taroona udevd[483]: no db file to read /run/udev/data/+i2c:i2c-0: No such file or directory
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748215380 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227450 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227990 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[483]: created db file '/run/udev/data/+i2c:i2c-0' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-0'
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2437 processed with 0
Jun  5 10:16:21 taroona udevd[483]: seq 2441 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-4'
Jun  5 10:16:21 taroona udevd[483]: no db file to read /run/udev/data/+i2c:i2c-4: No such file or directory
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa7482156a0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa7482151e0 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748214a80 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[483]: created db file '/run/udev/data/+i2c:i2c-4' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-4'
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2441 processed with 0
Jun  5 10:16:21 taroona udevd[483]: seq 2446 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227140 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-9'
Jun  5 10:16:21 taroona udevd[483]: no db file to read /run/udev/data/+i2c:i2c-9: No such file or directory
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa7482151e0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748214c50 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748226800 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[483]: created db file '/run/udev/data/+i2c:i2c-9' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-9'
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2446 processed with 0
Jun  5 10:16:22 taroona udevd[483]: seq 2447 running
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa7482151e0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:22 taroona udevd[483]: no db file to read /run/udev/data/c189:132: No such file or directory
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa748214ea0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa748214a80 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa748227900 has devpath '/devices/pci0000:00'
Jun  5 10:16:22 taroona udevd[483]: IMPORT builtin 'usb_id' /lib/udev/rules.d/40-libgphoto2-2.rules:11
Jun  5 10:16:22 taroona udevd[483]: ID_VENDOR=Qualcomm_Incorporated
Jun  5 10:16:22 taroona udevd[483]: ID_VENDOR_ENC=Qualcomm\x20Incorporated
Jun  5 10:16:22 taroona udevd[483]: ID_VENDOR_ID=05c6
Jun  5 10:16:22 taroona udevd[483]: ID_MODEL=Qualcomm_Gobi_2000
Jun  5 10:16:22 taroona udevd[483]: ID_MODEL_ENC=Qualcomm\x20Gobi\x202000
Jun  5 10:16:22 taroona udevd[483]: ID_MODEL_ID=9205
Jun  5 10:16:22 taroona udevd[483]: ID_REVISION=0002
Jun  5 10:16:22 taroona udevd[483]: ID_SERIAL=Qualcomm_Incorporated_Qualcomm_Gobi_2000
Jun  5 10:16:22 taroona udevd[483]: ID_BUS=usb
Jun  5 10:16:22 taroona udevd[483]: ID_USB_INTERFACES=:ffffff:
Jun  5 10:16:22 taroona udevd[483]: MODE 0664 /lib/udev/rules.d/50-udev-default.rules:55
Jun  5 10:16:22 taroona udevd[483]: IMPORT builtin skip 'usb_id' /lib/udev/rules.d/50-udev-default.rules:56
Jun  5 10:16:22 taroona udevd[483]: PROGRAM 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 2 5' /lib/udev/rules.d/69-libmtp.rules:884
Jun  5 10:16:23 taroona udevd[483]: 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 2 5'(out) '0'
Jun  5 10:16:23 taroona udevd[483]: 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 2 5' [1710] exit with return code 0
Jun  5 10:16:23 taroona udevd[483]: no node name set, will use kernel supplied name 'bus/usb/002/005'
Jun  5 10:16:23 taroona udevd[483]: creating device node '/dev/bus/usb/002/005', devnum=189:132, mode=0664, uid=0, gid=0
Jun  5 10:16:23 taroona udevd[483]: preserve file '/dev/bus/usb/002/005', because it has correct dev_t
Jun  5 10:16:23 taroona udevd[483]: set permissions /dev/bus/usb/002/005, 020664, uid=0, gid=0
Jun  5 10:16:23 taroona udevd[483]: creating symlink '/dev/char/189:132' to '../bus/usb/002/005'
Jun  5 10:16:23 taroona udevd[483]: created db file '/run/udev/data/c189:132' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:23 taroona udevd[483]: seq 2447 processed with 0
Jun  5 10:16:23 taroona udevd[483]: seq 2448 running
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0'
Jun  5 10:16:23 taroona udevd[483]: no db file to read /run/udev/data/+usb:2-1.4:1.0: No such file or directory
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748228930 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748214db0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748214fe0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748226ad0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748213dc0 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[483]: RUN 'usb_modeswitch --driver-bind %p %s{idVendor} %s{idProduct} %E{PRODUCT}' /lib/udev/rules.d/40-usb_modeswitch.rules:16
Jun  5 10:16:23 taroona udevd[483]: RUN '/sbin/modprobe -bv $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5
Jun  5 10:16:23 taroona udevd[483]: created db file '/run/udev/data/+usb:2-1.4:1.0' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0'
Jun  5 10:16:24 taroona udevd[483]: 'usb_modeswitch --driver-bind /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0   5c6/9205/2' [1711] exit with return code 0
Jun  5 10:16:24 taroona udevd[483]: '/sbin/modprobe -bv usb:v05C6p9205d0002dc00dsc00dp00icFFiscFFipFF' [1995] exit with return code 0
Jun  5 10:16:24 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:24 taroona udevd[483]: seq 2448 processed with 0
Jun  5 10:16:24 taroona udevd[483]: seq 2458 running
Jun  5 10:16:24 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/virtual/bdi/0:20'
Jun  5 10:16:24 taroona udevd[483]: no db file to read /run/udev/data/+bdi:0:20: No such file or directory
Jun  5 10:16:24 taroona udevd[483]: created db file '/run/udev/data/+bdi:0:20' for '/devices/virtual/bdi/0:20'
Jun  5 10:16:24 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:24 taroona udevd[483]: seq 2458 processed with 0

```


And here is a more complete section of the log covering the Network Manager initialisation (including the udevd entries)...
```

Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: init!
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: update_system_hostname
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPluginIfupdown: management mode: unmanaged
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: end _init.
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun  5 10:16:19 taroona NetworkManager[1093]:    Ifupdown: get unmanaged devices count: 0
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: (13436720) ... get_connections.
Jun  5 10:16:19 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: (13436720) ... get_connections (managed=false): return empty list.
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Qantas-Lounge ... 
Jun  5 10:16:19 taroona bluetoothd[1050]: input-headset driver probe failed for device 5C:57:C8:02:0E:42
Jun  5 10:16:19 taroona bluetoothd[1050]: Adapter /org/bluez/1050/hci0 has been enabled
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'Qantas-Lounge'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Jimojo Hotspot M4-1 ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     error: invalid or missing connection property 'connection setting not found'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing EAST_Guest ... 
Jun  5 10:16:19 taroona udevd[456]: seq 2400 queued, 'add' 'module'
Jun  5 10:16:19 taroona udevd[456]: passed 144 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: seq 2400 running
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748215f10 has devpath '/module/parport_pc'
Jun  5 10:16:19 taroona udevd[456]: seq 2401 queued, 'add' 'drivers'
Jun  5 10:16:19 taroona udevd[456]: passed 159 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: no db file to read /run/udev/data/+module:parport_pc: No such file or directory
Jun  5 10:16:19 taroona udevd[456]: seq 2402 queued, 'add' 'drivers'
Jun  5 10:16:19 taroona udevd[485]: RUN '/sbin/modprobe -bv ppdev' /lib/udev/rules.d/80-drivers.rules:11
Jun  5 10:16:19 taroona udevd[456]: passed 154 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[456]: seq 2403 queued, 'add' 'platform'
Jun  5 10:16:19 taroona udevd[487]: seq 2402 running
Jun  5 10:16:19 taroona udevd[486]: seq 2401 running
Jun  5 10:16:19 taroona udevd[456]: passed 189 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: created db file '/run/udev/data/+module:parport_pc' for '/module/parport_pc'
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa7482132d0 has devpath '/bus/platform/drivers/parport_pc'
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa748213720 has devpath '/bus/pnp/drivers/parport_pc'
Jun  5 10:16:19 taroona udevd[456]: seq 2404 queued, 'remove' 'platform'
Jun  5 10:16:19 taroona udevd[488]: seq 2403 running
Jun  5 10:16:19 taroona udevd[456]: seq 2405 queued, 'add' 'platform'
Jun  5 10:16:19 taroona udevd[486]: no db file to read /run/udev/data/+drivers:parport_pc: No such file or directory
Jun  5 10:16:19 taroona udevd[487]: no db file to read /run/udev/data/+drivers:parport_pc: No such file or directory
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748226ea0 has devpath '/bus/platform/drivers'
Jun  5 10:16:19 taroona udevd[489]: seq 2405 running
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa7482278f0 has devpath '/bus/platform'
Jun  5 10:16:19 taroona udevd[489]: device 0x7fa74822ac30 has devpath '/devices/platform'
Jun  5 10:16:19 taroona udevd[488]: device 0x7fa748213720 has devpath '/devices/platform'
Jun  5 10:16:19 taroona udevd[1125]: starting '/sbin/modprobe -bv ppdev'
Jun  5 10:16:19 taroona udevd[489]: RUN '/sbin/modprobe -bv $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5
Jun  5 10:16:19 taroona udevd[488]: RUN '/sbin/modprobe -bv $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5
Jun  5 10:16:19 taroona udevd[486]: created db file '/run/udev/data/+drivers:parport_pc' for '/bus/platform/drivers/parport_pc'
Jun  5 10:16:19 taroona udevd[489]: created db file '/run/udev/data/+platform:parport_pc.888' for '/devices/platform/parport_pc.888'
Jun  5 10:16:19 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:19 taroona udevd[486]: seq 2401 processed with 0
Jun  5 10:16:19 taroona udevd[488]: created db file '/run/udev/data/+platform:parport_pc.956' for '/devices/platform/parport_pc.956'
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa7482142d0 has devpath '/bus/pnp/drivers'
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa748213ce0 has devpath '/bus/pnp'
Jun  5 10:16:19 taroona udevd[1126]: starting '/sbin/modprobe -bv platform:parport_pc'
Jun  5 10:16:19 taroona udevd[1128]: starting '/sbin/modprobe -bv platform:parport_pc'
Jun  5 10:16:19 taroona udevd[487]: created db file '/run/udev/data/+drivers:parport_pc' for '/bus/pnp/drivers/parport_pc'
Jun  5 10:16:19 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:19 taroona udevd[487]: seq 2402 processed with 0
Jun  5 10:16:19 taroona udevd[456]: passed 189 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[456]: seq 2401 done with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2402 done with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2406 queued, 'remove' 'platform'
Jun  5 10:16:19 taroona udevd[456]: seq 2407 queued, 'add' 'platform'
Jun  5 10:16:19 taroona udevd[456]: passed 189 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[456]: seq 2408 queued, 'remove' 'platform'
Jun  5 10:16:19 taroona udevd[456]: seq 2409 queued, 'add' 'drivers'
Jun  5 10:16:19 taroona udevd[456]: passed 154 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[486]: seq 2407 running
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748227fb0 has devpath '/devices/platform'
Jun  5 10:16:19 taroona udevd[486]: RUN '/sbin/modprobe -bv $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5
Jun  5 10:16:19 taroona udevd[486]: created db file '/run/udev/data/+platform:parport_pc.632' for '/devices/platform/parport_pc.632'
Jun  5 10:16:19 taroona udevd[487]: seq 2409 running
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa748215790 has devpath '/bus/pci/drivers/parport_pc'
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa748215790 filled with db file data
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa748213720 has devpath '/bus/pci/drivers'
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa748213ad0 has devpath '/bus/pci'
Jun  5 10:16:19 taroona udevd[1129]: starting '/sbin/modprobe -bv platform:parport_pc'
Jun  5 10:16:19 taroona udevd[487]: created db file '/run/udev/data/+drivers:parport_pc' for '/bus/pci/drivers/parport_pc'
Jun  5 10:16:19 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:19 taroona udevd[487]: seq 2409 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2409 done with 0
Jun  5 10:16:19 taroona udevd[485]: '/sbin/modprobe -bv ppdev' [1125] exit with return code 0
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[456]: seq 2400 done with 0
Jun  5 10:16:19 taroona udevd[485]: seq 2400 processed with 0
Jun  5 10:16:19 taroona udevd[489]: '/sbin/modprobe -bv platform:parport_pc'(err) 'FATAL: Module platform:parport_pc not found.'
Jun  5 10:16:19 taroona udevd[489]: '/sbin/modprobe -bv platform:parport_pc' [1126] exit with return code 1
Jun  5 10:16:19 taroona udevd[488]: '/sbin/modprobe -bv platform:parport_pc'(err) 'FATAL: Module platform:parport_pc not found.'
Jun  5 10:16:19 taroona udevd[489]: passed -1 bytes to netlink monitor 0x7fa748260010
Jun  5 10:16:19 taroona udevd[488]: '/sbin/modprobe -bv platform:parport_pc' [1128] exit with return code 1
Jun  5 10:16:19 taroona udevd[489]: seq 2405 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2405 done with 0
Jun  5 10:16:19 taroona udevd[456]: passed 192 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[488]: passed -1 bytes to netlink monitor 0x7fa74825d640
Jun  5 10:16:19 taroona udevd[488]: seq 2403 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2403 done with 0
Jun  5 10:16:19 taroona udevd[485]: seq 2406 running
Jun  5 10:16:19 taroona udevd[456]: passed 192 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[487]: seq 2404 running
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748215f10 filled with db file data
Jun  5 10:16:19 taroona udevd[485]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa748213ad0 filled with db file data
Jun  5 10:16:19 taroona udevd[487]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:19 taroona udevd[1132]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:16:19 taroona udevd[1133]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:16:19 taroona udevd[486]: '/sbin/modprobe -bv platform:parport_pc'(err) 'FATAL: Module platform:parport_pc not found.'
Jun  5 10:16:19 taroona udevd[486]: '/sbin/modprobe -bv platform:parport_pc' [1129] exit with return code 1
Jun  5 10:16:19 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:19 taroona udevd[486]: seq 2407 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2407 done with 0
Jun  5 10:16:19 taroona udevd[456]: passed 192 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[486]: seq 2408 running
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748227fb0 filled with db file data
Jun  5 10:16:19 taroona udevd[486]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:19 taroona udevd[485]: '/etc/.mplab_ide/mchplinusbdevice remove ' [1132] exit with return code 0
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[485]: seq 2406 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2406 done with 0
Jun  5 10:16:19 taroona udevd[487]: '/etc/.mplab_ide/mchplinusbdevice remove ' [1133] exit with return code 0
Jun  5 10:16:19 taroona udevd[1136]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:16:19 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:19 taroona udevd[487]: seq 2404 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2404 done with 0
Jun  5 10:16:19 taroona udevd[486]: '/etc/.mplab_ide/mchplinusbdevice remove ' [1136] exit with return code 0
Jun  5 10:16:19 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:19 taroona udevd[486]: seq 2408 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2408 done with 0
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'EAST_Guest'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Free_Hotspot_2 ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     error: invalid or missing connection property 'connection setting not found'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Hyatt ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'Hyatt'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Mguest ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     error: invalid or missing connection property 'connection setting not found'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing TelstraViaMobilE ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'TelstraViaMobilE'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing 3151420-41326 ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection '3151420-41326'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing JavaPoint ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'JavaPoint'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing wireless ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'wireless'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Ethernet ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'Ethernet'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing guests ... 
Jun  5 10:16:19 taroona dbus[1035]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jun  5 10:16:19 taroona dbus[1035]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'guests'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing CLUBHOUSE_FREE_WiFi ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     error: invalid or missing connection property 'connection setting not found'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing unit314 ... 
Jun  5 10:16:19 taroona udevd[456]: seq 2410 queued, 'add' 'module'
Jun  5 10:16:19 taroona udevd[456]: passed 139 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: seq 2410 running
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748215f10 has devpath '/module/vmmon'
Jun  5 10:16:19 taroona udevd[485]: no db file to read /run/udev/data/+module:vmmon: No such file or directory
Jun  5 10:16:19 taroona udevd[456]: seq 2411 queued, 'add' 'misc'
Jun  5 10:16:19 taroona udevd[485]: created db file '/run/udev/data/+module:vmmon' for '/module/vmmon'
Jun  5 10:16:19 taroona udevd[456]: passed 184 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[486]: seq 2411 running
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[485]: seq 2410 processed with 0
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748226800 has devpath '/devices/virtual/misc/vmmon'
Jun  5 10:16:19 taroona udevd[456]: seq 2410 done with 0
Jun  5 10:16:19 taroona udevd[486]: no db file to read /run/udev/data/c10:165: No such file or directory
Jun  5 10:16:19 taroona udevd[486]: no node name set, will use kernel supplied name 'vmmon'
Jun  5 10:16:19 taroona udevd[486]: creating device node '/dev/vmmon', devnum=10:165, mode=0600, uid=0, gid=0
Jun  5 10:16:19 taroona udevd[486]: preserve file '/dev/vmmon', because it has correct dev_t
Jun  5 10:16:19 taroona udevd[486]: preserve permissions /dev/vmmon, 020600, uid=0, gid=0
Jun  5 10:16:19 taroona udevd[486]: creating symlink '/dev/char/10:165' to '../vmmon'
Jun  5 10:16:19 taroona udevd[486]: created db file '/run/udev/data/c10:165' for '/devices/virtual/misc/vmmon'
Jun  5 10:16:19 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:19 taroona udevd[486]: seq 2411 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2411 done with 0
Jun  5 10:16:19 taroona kernel: [   32.799411] /dev/vmmon[1145]: Module vmmon: registered with major=10 minor=165
Jun  5 10:16:19 taroona kernel: [   32.799419] /dev/vmmon[1145]: Module vmmon: initialized
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'unit314'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Telstra Default ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'Telstra Default'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Crowne Plaza Conference ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'Crowne Plaza Conference'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing Telstra_via_Gobi_2000 ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'Telstra_via_Gobi_2000'
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile: parsing IBM ... 
Jun  5 10:16:19 taroona NetworkManager[1093]:    keyfile:     read connection 'IBM'
Jun  5 10:16:19 taroona NetworkManager[1093]:    Ifupdown: get unmanaged devices count: 0
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> modem-manager is now available
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill1) (driver (unknown))
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> found WWAN radio killswitch rfkill3 (at /sys/devices/platform/thinkpad_acpi/rfkill/rfkill3) (driver thinkpad_acpi)
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> Networking is enabled by state file
Jun  5 10:16:19 taroona NetworkManager[1093]: <warn> failed to allocate link cache: (-10) Operation not supported
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (eth0): carrier is OFF
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (eth0): now managed
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (eth0): bringing up device.
Jun  5 10:16:19 taroona udevd[456]: seq 2412 queued, 'add' 'module'
Jun  5 10:16:19 taroona udevd[456]: passed 138 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: seq 2412 running
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa7482132d0 has devpath '/module/vmci'
Jun  5 10:16:19 taroona udevd[456]: seq 2413 queued, 'add' 'drivers'
Jun  5 10:16:19 taroona udevd[485]: no db file to read /run/udev/data/+module:vmci: No such file or directory
Jun  5 10:16:19 taroona udevd[456]: passed 148 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[486]: seq 2413 running
Jun  5 10:16:19 taroona udevd[456]: seq 2414 queued, 'add' 'misc'
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748227fb0 has devpath '/bus/pci/drivers/vmci'
Jun  5 10:16:19 taroona udevd[485]: created db file '/run/udev/data/+module:vmci' for '/module/vmci'
Jun  5 10:16:19 taroona udevd[486]: no db file to read /run/udev/data/+drivers:vmci: No such file or directory
Jun  5 10:16:19 taroona udevd[456]: passed 181 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748226a90 has devpath '/bus/pci/drivers'
Jun  5 10:16:19 taroona udevd[485]: seq 2412 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2412 done with 0
Jun  5 10:16:19 taroona udevd[487]: seq 2414 running
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748226fb0 has devpath '/bus/pci'
Jun  5 10:16:19 taroona udevd[487]: device 0x7fa748214db0 has devpath '/devices/virtual/misc/vmci'
Jun  5 10:16:19 taroona udevd[487]: no db file to read /run/udev/data/c10:57: No such file or directory
Jun  5 10:16:19 taroona udevd[486]: created db file '/run/udev/data/+drivers:vmci' for '/bus/pci/drivers/vmci'
Jun  5 10:16:19 taroona kernel: [   32.876863] [1156]: VMCI: shared components initialized.
Jun  5 10:16:19 taroona kernel: [   32.876912] [1156]: VMCI: host components initialized.
Jun  5 10:16:19 taroona kernel: [   32.876976] [1156]: VMCI: Module registered (name=vmci,major=10,minor=57).
Jun  5 10:16:19 taroona kernel: [   32.876979] [1156]: VMCI: Using host personality
Jun  5 10:16:19 taroona kernel: [   32.876981] [1156]: VMCI: Module (name=vmci) is initialized
Jun  5 10:16:19 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:19 taroona udevd[486]: seq 2413 processed with 0
Jun  5 10:16:19 taroona udevd[487]: no node name set, will use kernel supplied name 'vmci'
Jun  5 10:16:19 taroona udevd[456]: seq 2413 done with 0
Jun  5 10:16:19 taroona udevd[487]: creating device node '/dev/vmci', devnum=10:57, mode=0600, uid=0, gid=0
Jun  5 10:16:19 taroona udevd[487]: preserve file '/dev/vmci', because it has correct dev_t
Jun  5 10:16:19 taroona udevd[487]: preserve permissions /dev/vmci, 020600, uid=0, gid=0
Jun  5 10:16:19 taroona udevd[487]: creating symlink '/dev/char/10:57' to '../vmci'
Jun  5 10:16:19 taroona udevd[487]: created db file '/run/udev/data/c10:57' for '/devices/virtual/misc/vmci'
Jun  5 10:16:19 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:19 taroona udevd[487]: seq 2414 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2414 done with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2415 queued, 'add' 'module'
Jun  5 10:16:19 taroona udevd[456]: passed 139 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: seq 2415 running
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748215f10 has devpath '/module/vsock'
Jun  5 10:16:19 taroona udevd[485]: no db file to read /run/udev/data/+module:vsock: No such file or directory
Jun  5 10:16:19 taroona udevd[485]: created db file '/run/udev/data/+module:vsock' for '/module/vsock'
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[485]: seq 2415 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2415 done with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2416 queued, 'add' 'misc'
Jun  5 10:16:19 taroona udevd[456]: passed 183 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: seq 2416 running
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748216760 has devpath '/devices/virtual/misc/vsock'
Jun  5 10:16:19 taroona udevd[485]: no db file to read /run/udev/data/c10:56: No such file or directory
Jun  5 10:16:19 taroona udevd[485]: no node name set, will use kernel supplied name 'vsock'
Jun  5 10:16:19 taroona udevd[485]: creating device node '/dev/vsock', devnum=10:56, mode=0600, uid=0, gid=0
Jun  5 10:16:19 taroona udevd[485]: preserve file '/dev/vsock', because it has correct dev_t
Jun  5 10:16:19 taroona udevd[485]: preserve permissions /dev/vsock, 020600, uid=0, gid=0
Jun  5 10:16:19 taroona udevd[485]: creating symlink '/dev/char/10:56' to '../vsock'
Jun  5 10:16:19 taroona udevd[485]: created db file '/run/udev/data/c10:56' for '/devices/virtual/misc/vsock'
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[485]: seq 2416 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2416 done with 0
Jun  5 10:16:19 taroona kernel: [   32.961697] e1000e 0000:00:19.0: irq 54 for MSI/MSI-X
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (eth0): preparing device.
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (wlan0): using nl80211 for WiFi device control
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (wlan0): now managed
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (wlan0): bringing up device.
Jun  5 10:16:19 taroona kernel: [   33.021561] e1000e 0000:00:19.0: irq 54 for MSI/MSI-X
Jun  5 10:16:19 taroona kernel: [   33.022761] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  5 10:16:19 taroona kernel: [   33.023041] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  5 10:16:19 taroona kernel: [   33.024504] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
Jun  5 10:16:19 taroona kernel: [   33.030959] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1

Jun  5 10:16:19 taroona udevd[483]: 'gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi' [831] exit with return code 0
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2308 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2308 done with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2417 queued, 'add' 'bdi'
Jun  5 10:16:19 taroona udevd[456]: passed 148 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[483]: seq 2417 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748226800 has devpath '/devices/virtual/bdi/0:19'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/+bdi:0:19: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/+bdi:0:19' for '/devices/virtual/bdi/0:19'
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2417 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2417 done with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2418 queued, 'add' 'module'
Jun  5 10:16:19 taroona udevd[456]: passed 139 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[483]: seq 2418 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748213720 has devpath '/module/vmnet'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/+module:vmnet: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/+module:vmnet' for '/module/vmnet'
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2418 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2418 done with 0
Jun  5 10:16:19 taroona vmnetBridge: Bridge process created.
Jun  5 10:16:19 taroona udevd[456]: seq 2419 queued, 'add' 'module'
Jun  5 10:16:19 taroona udevd[456]: passed 140 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[483]: seq 2419 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748226800 has devpath '/module/vesafb'
Jun  5 10:16:19 taroona kernel: [   33.221747] vesafb: mode is 640x480x32, linelength=2560, pages=0
Jun  5 10:16:19 taroona kernel: [   33.221752] vesafb: scrolling: redraw
Jun  5 10:16:19 taroona kernel: [   33.221756] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/+module:vesafb: No such file or directory
Jun  5 10:16:19 taroona udevd[456]: seq 2420 queued, 'add' 'platform'
Jun  5 10:16:19 taroona udevd[456]: passed 179 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/+module:vesafb' for '/module/vesafb'
Jun  5 10:16:19 taroona udevd[485]: seq 2420 running
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748213720 has devpath '/devices/platform/vesafb.0'
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2419 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2419 done with 0
Jun  5 10:16:19 taroona udevd[485]: no db file to read /run/udev/data/+platform:vesafb.0: No such file or directory
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748216500 has devpath '/devices/platform'
Jun  5 10:16:19 taroona udevd[485]: created db file '/run/udev/data/+platform:vesafb.0' for '/devices/platform/vesafb.0'
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[485]: seq 2420 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2420 done with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2421 queued, 'add' 'graphics'
Jun  5 10:16:19 taroona udevd[456]: passed 196 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[456]: seq 2422 queued, 'add' 'vtconsole'
Jun  5 10:16:19 taroona udevd[483]: seq 2421 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748215410 has devpath '/devices/platform/vesafb.0/graphics/fb0'
Jun  5 10:16:19 taroona udevd[456]: passed 162 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: seq 2422 running
Jun  5 10:16:19 taroona udevd[456]: seq 2423 queued, 'add' 'drivers'
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748216bf0 has devpath '/devices/virtual/vtconsole/vtcon1'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/c29:0: No such file or directory
Jun  5 10:16:19 taroona udevd[456]: passed 155 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa74822b180 has devpath '/devices/platform/vesafb.0'
Jun  5 10:16:19 taroona udevd[485]: no db file to read /run/udev/data/+vtconsole:vtcon1: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748215000 has devpath '/devices/platform'
Jun  5 10:16:19 taroona udevd[486]: seq 2423 running
Jun  5 10:16:19 taroona udevd[483]: GROUP 44 /lib/udev/rules.d/50-udev-default.rules:38
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748226800 has devpath '/bus/platform/drivers/vesafb'
Jun  5 10:16:19 taroona udevd[485]: created db file '/run/udev/data/+vtconsole:vtcon1' for '/devices/virtual/vtconsole/vtcon1'
Jun  5 10:16:19 taroona udevd[486]: no db file to read /run/udev/data/+drivers:vesafb: No such file or directory
Jun  5 10:16:19 taroona udevd[483]: RUN '/sbin/modprobe -q fbcon' /lib/udev/rules.d/80-drivers.rules:12
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa7482132d0 has devpath '/bus/platform/drivers'
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[483]: no node name set, will use kernel supplied name 'fb0'
Jun  5 10:16:19 taroona udevd[485]: seq 2422 processed with 0
Jun  5 10:16:19 taroona udevd[483]: creating device node '/dev/fb0', devnum=29:0, mode=0660, uid=0, gid=44
Jun  5 10:16:19 taroona udevd[486]: device 0x7fa748227180 has devpath '/bus/platform'
Jun  5 10:16:19 taroona udevd[483]: preserve file '/dev/fb0', because it has correct dev_t
Jun  5 10:16:19 taroona udevd[483]: set permissions /dev/fb0, 020660, uid=0, gid=44
Jun  5 10:16:19 taroona udevd[456]: seq 2422 done with 0
Jun  5 10:16:19 taroona udevd[483]: creating symlink '/dev/char/29:0' to '../fb0'
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/c29:0' for '/devices/platform/vesafb.0/graphics/fb0'
Jun  5 10:16:19 taroona udevd[486]: created db file '/run/udev/data/+drivers:vesafb' for '/bus/platform/drivers/vesafb'
Jun  5 10:16:19 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:19 taroona udevd[486]: seq 2423 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2423 done with 0
Jun  5 10:16:19 taroona udevd[1240]: starting '/sbin/modprobe -q fbcon'
Jun  5 10:16:19 taroona kernel: [   33.227065] vesafb: framebuffer at 0xcf000000, mapped to 0xffffc90013180000, using 1216k, total 1216k
Jun  5 10:16:19 taroona kernel: [   33.227225] Console: switching to colour frame buffer device 80x30
Jun  5 10:16:19 taroona kernel: [   33.227248] fb0: VESA VGA frame buffer device
Jun  5 10:16:19 taroona udevd[483]: '/sbin/modprobe -q fbcon' [1240] exit with return code 0
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2421 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2421 done with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2424 queued, 'add' 'module'
Jun  5 10:16:19 taroona udevd[456]: passed 142 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[483]: seq 2424 running
Jun  5 10:16:19 taroona udevd[483]: device 0x7fa748213720 has devpath '/module/dm_crypt'
Jun  5 10:16:19 taroona udevd[483]: no db file to read /run/udev/data/+module:dm_crypt: No such file or directory
Jun  5 10:16:19 taroona udevd[456]: seq 2425 queued, 'add' 'slab'
Jun  5 10:16:19 taroona udevd[456]: passed 147 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:19 taroona udevd[485]: seq 2425 running
Jun  5 10:16:19 taroona udevd[483]: created db file '/run/udev/data/+module:dm_crypt' for '/module/dm_crypt'
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748213720 has devpath '/kernel/slab/:t-0000152'
Jun  5 10:16:19 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:19 taroona udevd[483]: seq 2424 processed with 0
Jun  5 10:16:19 taroona udevd[485]: device 0x7fa748215670 has devpath '/kernel/slab'
Jun  5 10:16:19 taroona udevd[456]: seq 2424 done with 0
Jun  5 10:16:19 taroona udevd[485]: created db file '/run/udev/data/+slab::t-0000152' for '/kernel/slab/:t-0000152'
Jun  5 10:16:19 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:19 taroona udevd[485]: seq 2425 processed with 0
Jun  5 10:16:19 taroona udevd[456]: seq 2425 done with 0
Jun  5 10:16:19 taroona kernel: [   33.264656] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
Jun  5 10:16:19 taroona kernel: [   33.271072] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
Jun  5 10:16:19 taroona kernel: [   33.395519] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  5 10:16:19 taroona vmnetBridge: RTM_NEWLINK: name:wlan0 index:3 flags:0x00001043
Jun  5 10:16:19 taroona vmnetBridge: Adding interface wlan0 index:3
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (wlan0): preparing device.
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun  5 10:16:19 taroona vmnetBridge: Started bridge wlan0 to virtual network 0.
Jun  5 10:16:19 taroona vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001003
Jun  5 10:16:19 taroona vmnetBridge: RTM_NEWLINK: name:wlan0 index:3 flags:0x00001043
Jun  5 10:16:19 taroona vmnetBridge: RTM_NEWLINK: name:wlan0 index:3 flags:0x00001003
Jun  5 10:16:19 taroona vmnetBridge: Removing interface wlan0 index:3
Jun  5 10:16:19 taroona dbus[1035]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jun  5 10:16:19 taroona kernel: [   33.396983] /dev/vmnet: open called by PID 1223 (vmnet-bridge)
Jun  5 10:16:19 taroona kernel: [   33.396994] /dev/vmnet: hub 0 does not exist, allocating memory.
Jun  5 10:16:19 taroona kernel: [   33.397024] /dev/vmnet: port on hub 0 successfully opened
Jun  5 10:16:19 taroona kernel: [   33.397043] bridge-wlan0: device is wireless, enabling SMAC
Jun  5 10:16:19 taroona kernel: [   33.397047] bridge-wlan0: up
Jun  5 10:16:19 taroona kernel: [   33.397051] bridge-wlan0: attached
Jun  5 10:16:19 taroona kernel: [   33.397108] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  5 10:16:19 taroona kernel: [   33.397112] bridge-wlan0: disabling the bridge
Jun  5 10:16:19 taroona NetworkManager[1093]: <warn> (5C:57:C8:02:0E:42): failed to look up interface index
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> BT device NomadAU (5C:57:C8:02:0E:42) added (DUN)
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (5C:57:C8:02:0E:42): new Bluetooth device (driver: 'bluez' ifindex: 0)
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (5C:57:C8:02:0E:42): exported as /org/freedesktop/NetworkManager/Devices/2
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (5C:57:C8:02:0E:42): now managed
Jun  5 10:16:19 taroona dbus[1035]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (5C:57:C8:02:0E:42): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (5C:57:C8:02:0E:42): deactivating device (reason 'managed') [2]
Jun  5 10:16:19 taroona NetworkManager[1093]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Jun  5 10:16:19 taroona NetworkManager[1093]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> wpa_supplicant started
Jun  5 10:16:19 taroona NetworkManager[1093]: <info> (5C:57:C8:02:0E:42): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jun  5 10:16:19 taroona vmnetBridge: Stopped bridge wlan0 to virtual network 0.
Jun  5 10:16:19 taroona kernel: [   33.421038] bridge-wlan0: down
Jun  5 10:16:19 taroona kernel: [   33.421044] bridge-wlan0: detached
Jun  5 10:16:20 taroona NetworkManager[1093]: <info> (wlan0): supplicant interface state: starting -> ready
Jun  5 10:16:20 taroona NetworkManager[1093]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun  5 10:16:20 taroona NetworkManager[1093]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  5 10:16:20 taroona NetworkManager[1093]: <warn> Trying to remove a non-existant call id.
Jun  5 10:16:20 taroona acpid: client connected from 1282[0:0]
Jun  5 10:16:20 taroona acpid: 1 client rule loaded
Jun  5 10:16:20 taroona udevd[456]: seq 2426 queued, 'add' 'net'
Jun  5 10:16:20 taroona udevd[456]: passed 177 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:20 taroona udevd[456]: seq 2427 queued, 'add' 'queues'
Jun  5 10:16:20 taroona udevd[456]: seq 2428 queued, 'add' 'queues'
Jun  5 10:16:20 taroona udevd[483]: seq 2426 running
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa7482157a0 has devpath '/devices/virtual/net/vmnet1'
Jun  5 10:16:20 taroona udevd[483]: no db file to read /run/udev/data/n4: No such file or directory
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/n4' for '/devices/virtual/net/vmnet1'
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2426 processed with 0
Jun  5 10:16:20 taroona udevd[456]: seq 2426 done with 0
Jun  5 10:16:20 taroona udevd[456]: passed 165 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:20 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vmnet1, iface: vmnet1)
Jun  5 10:16:20 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vmnet1, iface: vmnet1): no ifupdown configuration found.
Jun  5 10:16:20 taroona udevd[456]: passed 165 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:20 taroona udevd[483]: seq 2427 running
Jun  5 10:16:20 taroona udevd[485]: seq 2428 running
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/virtual/net/vmnet1'
Jun  5 10:16:20 taroona udevd[485]: device 0x7fa748213720 has devpath '/devices/virtual/net/vmnet1'
Jun  5 10:16:20 taroona NetworkManager[1093]: <warn> /sys/devices/virtual/net/vmnet1: couldn't determine device driver; ignoring...
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/+queues:rx-0' for '/devices/virtual/net/vmnet1/queues/rx-0'
Jun  5 10:16:20 taroona udevd[485]: created db file '/run/udev/data/+queues:tx-0' for '/devices/virtual/net/vmnet1/queues/tx-0'
Jun  5 10:16:20 taroona avahi-daemon[1100]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 192.168.103.1.
Jun  5 10:16:20 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:20 taroona udevd[485]: seq 2428 processed with 0
Jun  5 10:16:20 taroona udevd[456]: seq 2428 done with 0
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2427 processed with 0
Jun  5 10:16:20 taroona kernel: [   33.654881] /dev/vmnet: open called by PID 1284 (vmnet-netifup)
Jun  5 10:16:20 taroona kernel: [   33.654888] /dev/vmnet: hub 1 does not exist, allocating memory.
Jun  5 10:16:20 taroona kernel: [   33.654903] /dev/vmnet: port on hub 1 successfully opened
Jun  5 10:16:20 taroona udevd[456]: seq 2427 done with 0
Jun  5 10:16:20 taroona avahi-daemon[1100]: New relevant interface vmnet1.IPv4 for mDNS.
Jun  5 10:16:20 taroona avahi-daemon[1100]: Registering new address record for 192.168.103.1 on vmnet1.IPv4.
Jun  5 10:16:20 taroona vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jun  5 10:16:20 taroona vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jun  5 10:16:20 taroona vmnet-dhcpd: All rights reserved.
Jun  5 10:16:20 taroona vmnet-dhcpd: 
Jun  5 10:16:20 taroona vmnet-dhcpd: Please contribute if you find this software useful.
Jun  5 10:16:20 taroona vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jun  5 10:16:20 taroona vmnet-dhcpd: 
Jun  5 10:16:20 taroona vmnet-dhcpd: Configured subnet: 192.168.103.0
Jun  5 10:16:20 taroona vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.103.254
Jun  5 10:16:20 taroona vmnet-dhcpd: Recving on     VNet/vmnet1/192.168.103.0
Jun  5 10:16:20 taroona vmnet-dhcpd: Sending on     VNet/vmnet1/192.168.103.0
Jun  5 10:16:20 taroona kernel: [   33.854986] /dev/vmnet: open called by PID 1288 (vmnet-dhcpd)
Jun  5 10:16:20 taroona kernel: [   33.855004] /dev/vmnet: port on hub 1 successfully opened
Jun  5 10:16:20 taroona vmnet-natd: RTM_NEWLINK: name:eth0 index:2 flags:0x00001003
Jun  5 10:16:20 taroona vmnet-natd: RTM_NEWLINK: name:wlan0 index:3 flags:0x00001003
Jun  5 10:16:20 taroona kernel: [   33.858771] /dev/vmnet: open called by PID 1293 (vmnet-natd)
Jun  5 10:16:20 taroona kernel: [   33.858777] /dev/vmnet: hub 8 does not exist, allocating memory.
Jun  5 10:16:20 taroona kernel: [   33.858794] /dev/vmnet: port on hub 8 successfully opened
Jun  5 10:16:20 taroona udevd[456]: seq 2429 queued, 'add' 'net'
Jun  5 10:16:20 taroona udevd[456]: passed 177 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:20 taroona udevd[456]: seq 2430 queued, 'add' 'queues'
Jun  5 10:16:20 taroona udevd[483]: seq 2429 running
Jun  5 10:16:20 taroona udevd[456]: seq 2431 queued, 'add' 'queues'
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa7482157a0 has devpath '/devices/virtual/net/vmnet8'
Jun  5 10:16:20 taroona udevd[483]: no db file to read /run/udev/data/n5: No such file or directory
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/n5' for '/devices/virtual/net/vmnet8'
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2429 processed with 0
Jun  5 10:16:20 taroona udevd[456]: seq 2429 done with 0
Jun  5 10:16:20 taroona udevd[456]: passed 165 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:20 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vmnet8, iface: vmnet8)
Jun  5 10:16:20 taroona udevd[483]: seq 2430 running
Jun  5 10:16:20 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vmnet8, iface: vmnet8): no ifupdown configuration found.
Jun  5 10:16:20 taroona udevd[456]: passed 165 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/virtual/net/vmnet8'
Jun  5 10:16:20 taroona udevd[485]: seq 2431 running
Jun  5 10:16:20 taroona udevd[485]: device 0x7fa7482132d0 has devpath '/devices/virtual/net/vmnet8'
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/+queues:rx-0' for '/devices/virtual/net/vmnet8/queues/rx-0'
Jun  5 10:16:20 taroona NetworkManager[1093]: <warn> /sys/devices/virtual/net/vmnet8: couldn't determine device driver; ignoring...
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2430 processed with 0
Jun  5 10:16:20 taroona udevd[456]: seq 2430 done with 0
Jun  5 10:16:20 taroona udevd[485]: created db file '/run/udev/data/+queues:tx-0' for '/devices/virtual/net/vmnet8/queues/tx-0'
Jun  5 10:16:20 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:20 taroona udevd[485]: seq 2431 processed with 0
Jun  5 10:16:20 taroona udevd[456]: seq 2431 done with 0
Jun  5 10:16:20 taroona kernel: [   33.860857] /dev/vmnet: open called by PID 1294 (vmnet-netifup)
Jun  5 10:16:20 taroona kernel: [   33.860865] /dev/vmnet: port on hub 8 successfully opened
Jun  5 10:16:20 taroona avahi-daemon[1100]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.216.1.
Jun  5 10:16:20 taroona avahi-daemon[1100]: New relevant interface vmnet8.IPv4 for mDNS.
Jun  5 10:16:20 taroona avahi-daemon[1100]: Registering new address record for 172.16.216.1 on vmnet8.IPv4.
Jun  5 10:16:20 taroona vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jun  5 10:16:20 taroona vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jun  5 10:16:20 taroona vmnet-dhcpd: All rights reserved.
Jun  5 10:16:20 taroona vmnet-dhcpd: 
Jun  5 10:16:20 taroona vmnet-dhcpd: Please contribute if you find this software useful.
Jun  5 10:16:20 taroona vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jun  5 10:16:20 taroona vmnet-dhcpd: 
Jun  5 10:16:20 taroona vmnet-dhcpd: Configured subnet: 172.16.216.0
Jun  5 10:16:20 taroona vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.216.254
Jun  5 10:16:20 taroona vmnet-dhcpd: Recving on     VNet/vmnet8/172.16.216.0
Jun  5 10:16:20 taroona vmnet-dhcpd: Sending on     VNet/vmnet8/172.16.216.0
Jun  5 10:16:20 taroona kernel: [   34.195921] /dev/vmnet: open called by PID 1299 (vmnet-dhcpd)
Jun  5 10:16:20 taroona kernel: [   34.195964] /dev/vmnet: port on hub 8 successfully opened
Jun  5 10:16:20 taroona udevd[456]: seq 2432 queued, 'add' 'drivers'
Jun  5 10:16:20 taroona udevd[456]: passed 169 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:20 taroona udevd[483]: seq 2432 running
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748226ca0 has devpath '/bus/acpi/drivers/NVIDIA ACPI Video Driver'
Jun  5 10:16:20 taroona udevd[483]: no db file to read /run/udev/data/+drivers:NVIDIA ACPI Video Driver: No such file or directory
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748226a70 has devpath '/bus/acpi/drivers'
Jun  5 10:16:20 taroona udevd[483]: device 0x7fa748227020 has devpath '/bus/acpi'
Jun  5 10:16:20 taroona udevd[483]: created db file '/run/udev/data/+drivers:NVIDIA ACPI Video Driver' for '/bus/acpi/drivers/NVIDIA ACPI Video Driver'
Jun  5 10:16:20 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:20 taroona udevd[483]: seq 2432 processed with 0
Jun  5 10:16:20 taroona udevd[456]: seq 2432 done with 0
Jun  5 10:16:21 taroona kernel: [   35.070693] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
Jun  5 10:16:21 taroona udevd[456]: seq 2433 queued, 'remove' 'tty'
Jun  5 10:16:21 taroona udevd[456]: passed 237 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[456]: seq 2434 queued, 'remove' 'usb-serial'
Jun  5 10:16:21 taroona udevd[483]: seq 2433 running
Jun  5 10:16:21 taroona udevd[456]: seq 2435 queued, 'remove' 'usb'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227020 filled with db file data
Jun  5 10:16:21 taroona udevd[456]: seq 2436 queued, 'remove' 'usb'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227280 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748214490 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748214bf0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227730 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[483]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:21 taroona udevd[483]: no reference left, remove '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0'
Jun  5 10:16:21 taroona udevd[483]: no reference left, remove '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.1-port0'
Jun  5 10:16:21 taroona udevd[483]: device node '/dev/ttyUSB0' not found
Jun  5 10:16:21 taroona udevd[483]: removing device node '/dev/ttyUSB0'
Jun  5 10:16:21 taroona udevd[1644]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:16:21 taroona kernel: [   35.089574] usb 2-1.4: USB disconnect, device number 4
Jun  5 10:16:21 taroona kernel: [   35.089730] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
Jun  5 10:16:21 taroona kernel: [   35.089756] qcserial 2-1.4:1.1: device disconnected
Jun  5 10:16:21 taroona udevd[483]: '/etc/.mplab_ide/mchplinusbdevice remove ' [1644] exit with return code 0
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2433 processed with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2433 done with 0
Jun  5 10:16:21 taroona udevd[456]: passed 198 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[483]: seq 2434 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227730 filled with db file data
Jun  5 10:16:21 taroona udevd[483]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:21 taroona udevd[1645]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:16:21 taroona udevd[483]: '/etc/.mplab_ide/mchplinusbdevice remove ' [1645] exit with return code 0
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2434 processed with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2434 done with 0
Jun  5 10:16:21 taroona udevd[456]: passed 312 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[483]: seq 2435 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748215770 filled with db file data
Jun  5 10:16:21 taroona udevd[483]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:21 taroona udevd[1646]: starting '/etc/.mplab_ide/mchplinusbdevice remove 5c6/9204/2'
Jun  5 10:16:21 taroona udevd[483]: '/etc/.mplab_ide/mchplinusbdevice remove 5c6/9204/2' [1646] exit with return code 0
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2435 processed with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2435 done with 0
Jun  5 10:16:21 taroona udevd[456]: passed 288 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[483]: seq 2436 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748215770 filled with db file data
Jun  5 10:16:21 taroona udevd[483]: IMPORT builtin 'usb_id' /lib/udev/rules.d/50-udev-default.rules:56
Jun  5 10:16:21 taroona udevd[483]: No USB vendor information available
Jun  5 10:16:21 taroona udevd[483]: IMPORT builtin 'usb_id' returned non-zero
Jun  5 10:16:21 taroona udevd[483]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:21 taroona udevd[483]: device node '/dev/bus/usb/002/004' not found
Jun  5 10:16:21 taroona udevd[483]: removing device node '/dev/bus/usb/002/004'
Jun  5 10:16:21 taroona udevd[1647]: starting '/etc/.mplab_ide/mchplinusbdevice remove 5c6/9204/2'
Jun  5 10:16:21 taroona udevd[483]: '/etc/.mplab_ide/mchplinusbdevice remove 5c6/9204/2' [1647] exit with return code 0
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2436 processed with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2436 done with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2437 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[456]: seq 2438 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[483]: seq 2437 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-0'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[485]: seq 2438 running
Jun  5 10:16:21 taroona udevd[456]: seq 2439 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[483]: no db file to read /run/udev/data/+i2c:i2c-0: No such file or directory
Jun  5 10:16:21 taroona udevd[485]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-1'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748215380 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[456]: seq 2440 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[486]: seq 2439 running
Jun  5 10:16:21 taroona udevd[485]: no db file to read /run/udev/data/+i2c:i2c-1: No such file or directory
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227450 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[485]: device 0x7fa7482153a0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[486]: device 0x7fa748226800 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-2'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227990 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[487]: seq 2440 running
Jun  5 10:16:21 taroona udevd[485]: device 0x7fa748216470 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[487]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-3'
Jun  5 10:16:21 taroona udevd[485]: device 0x7fa748213ad0 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[486]: no db file to read /run/udev/data/+i2c:i2c-2: No such file or directory
Jun  5 10:16:21 taroona udevd[486]: device 0x7fa748227f70 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[487]: no db file to read /run/udev/data/+i2c:i2c-3: No such file or directory
Jun  5 10:16:21 taroona udevd[487]: device 0x7fa748214fc0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[486]: device 0x7fa748226fb0 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[483]: created db file '/run/udev/data/+i2c:i2c-0' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-0'
Jun  5 10:16:21 taroona udevd[486]: device 0x7fa748227730 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[487]: device 0x7fa7482146f0 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[487]: device 0x7fa748213ad0 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[485]: created db file '/run/udev/data/+i2c:i2c-1' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-1'
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2437 processed with 0
Jun  5 10:16:21 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:21 taroona udevd[485]: seq 2438 processed with 0
Jun  5 10:16:21 taroona udevd[486]: created db file '/run/udev/data/+i2c:i2c-2' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-2'
Jun  5 10:16:21 taroona udevd[487]: created db file '/run/udev/data/+i2c:i2c-3' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-3'
Jun  5 10:16:21 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:21 taroona udevd[486]: seq 2439 processed with 0
Jun  5 10:16:21 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:21 taroona udevd[487]: seq 2440 processed with 0
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[456]: seq 2437 done with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2438 done with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2439 done with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2440 done with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2441 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[483]: seq 2441 running
Jun  5 10:16:21 taroona udevd[456]: seq 2442 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-4'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[483]: no db file to read /run/udev/data/+i2c:i2c-4: No such file or directory
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa7482156a0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[485]: seq 2442 running
Jun  5 10:16:21 taroona udevd[456]: seq 2443 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa7482151e0 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[485]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-5'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748214a80 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[456]: seq 2444 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[485]: no db file to read /run/udev/data/+i2c:i2c-5: No such file or directory
Jun  5 10:16:21 taroona udevd[486]: seq 2443 running
Jun  5 10:16:21 taroona udevd[485]: device 0x7fa7482132d0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[486]: device 0x7fa748213ad0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-6'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[483]: created db file '/run/udev/data/+i2c:i2c-4' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-4'
Jun  5 10:16:21 taroona udevd[485]: device 0x7fa748213ca0 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[487]: seq 2444 running
Jun  5 10:16:21 taroona udevd[456]: seq 2445 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[485]: device 0x7fa748214260 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[488]: seq 2445 running
Jun  5 10:16:21 taroona udevd[483]: seq 2441 processed with 0
Jun  5 10:16:21 taroona udevd[488]: device 0x7fa74825c940 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-8'
Jun  5 10:16:21 taroona udevd[485]: created db file '/run/udev/data/+i2c:i2c-5' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-5'
Jun  5 10:16:21 taroona udevd[487]: device 0x7fa748215760 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-7'
Jun  5 10:16:21 taroona udevd[488]: no db file to read /run/udev/data/+i2c:i2c-8: No such file or directory
Jun  5 10:16:21 taroona udevd[488]: device 0x7fa74825ce60 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:21 taroona udevd[485]: seq 2442 processed with 0
Jun  5 10:16:21 taroona udevd[487]: no db file to read /run/udev/data/+i2c:i2c-7: No such file or directory
Jun  5 10:16:21 taroona udevd[488]: device 0x7fa74825d3c0 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[488]: device 0x7fa748213dd0 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[487]: device 0x7fa748215290 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[487]: device 0x7fa748214280 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[487]: device 0x7fa7482144d0 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[488]: created db file '/run/udev/data/+i2c:i2c-8' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-8'
Jun  5 10:16:21 taroona udevd[487]: created db file '/run/udev/data/+i2c:i2c-7' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-7'
Jun  5 10:16:21 taroona udevd[488]: passed -1 bytes to netlink monitor 0x7fa74825d640
Jun  5 10:16:21 taroona udevd[488]: seq 2445 processed with 0
Jun  5 10:16:21 taroona udevd[486]: no db file to read /run/udev/data/+i2c:i2c-6: No such file or directory
Jun  5 10:16:21 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:21 taroona udevd[487]: seq 2444 processed with 0
Jun  5 10:16:21 taroona udevd[486]: device 0x7fa7482132d0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[486]: device 0x7fa748228510 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[456]: seq 2441 done with 0
Jun  5 10:16:21 taroona udevd[486]: device 0x7fa748226a90 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[456]: seq 2442 done with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2445 done with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2444 done with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2446 queued, 'add' 'i2c'
Jun  5 10:16:21 taroona udevd[456]: passed 174 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:21 taroona udevd[486]: created db file '/run/udev/data/+i2c:i2c-6' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-6'
Jun  5 10:16:21 taroona udevd[483]: seq 2446 running
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748227140 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-9'
Jun  5 10:16:21 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:21 taroona udevd[486]: seq 2443 processed with 0
Jun  5 10:16:21 taroona udevd[483]: no db file to read /run/udev/data/+i2c:i2c-9: No such file or directory
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa7482151e0 has devpath '/devices/pci0000:00/0000:00:03.0/0000:01:00.0'
Jun  5 10:16:21 taroona udevd[456]: seq 2443 done with 0
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748214c50 has devpath '/devices/pci0000:00/0000:00:03.0'
Jun  5 10:16:21 taroona udevd[483]: device 0x7fa748226800 has devpath '/devices/pci0000:00'
Jun  5 10:16:21 taroona udevd[483]: created db file '/run/udev/data/+i2c:i2c-9' for '/devices/pci0000:00/0000:00:03.0/0000:01:00.0/i2c-9'
Jun  5 10:16:21 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:21 taroona udevd[483]: seq 2446 processed with 0
Jun  5 10:16:21 taroona udevd[456]: seq 2446 done with 0
Jun  5 10:16:21 taroona kernel: [   35.311190] NVRM: Your system is not currently configured to drive a VGA console
Jun  5 10:16:21 taroona kernel: [   35.311196] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
Jun  5 10:16:21 taroona kernel: [   35.311201] NVRM: requires the use of a text-mode VGA console. Use of other console
Jun  5 10:16:21 taroona kernel: [   35.311204] NVRM: drivers including, but not limited to, vesafb, may result in
Jun  5 10:16:21 taroona kernel: [   35.311208] NVRM: corruption and stability problems, and is not supported.
Jun  5 10:16:21 taroona avahi-daemon[1100]: Joining mDNS multicast group on interface vmnet1.IPv6 with address fe80::250:56ff:fec0:1.
Jun  5 10:16:21 taroona avahi-daemon[1100]: New relevant interface vmnet1.IPv6 for mDNS.
Jun  5 10:16:21 taroona avahi-daemon[1100]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Jun  5 10:16:21 taroona kernel: [   35.415551] cfg80211: Found new beacon on frequency: 5240 MHz (Ch 48) on phy0
Jun  5 10:16:22 taroona anacron[1706]: Anacron 2.3 started on 2013-06-05
Jun  5 10:16:22 taroona avahi-daemon[1100]: Joining mDNS multicast group on interface vmnet8.IPv6 with address fe80::250:56ff:fec0:8.
Jun  5 10:16:22 taroona avahi-daemon[1100]: New relevant interface vmnet8.IPv6 for mDNS.
Jun  5 10:16:22 taroona avahi-daemon[1100]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Jun  5 10:16:22 taroona kernel: [   36.318325] usb 2-1.4: new high-speed USB device number 5 using ehci_hcd
Jun  5 10:16:22 taroona udevd[456]: seq 2447 queued, 'add' 'usb'
Jun  5 10:16:22 taroona udevd[456]: passed 285 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:22 taroona udevd[483]: seq 2447 running
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa7482151e0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:22 taroona udevd[483]: no db file to read /run/udev/data/c189:132: No such file or directory
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa748214ea0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa748214a80 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:22 taroona udevd[483]: device 0x7fa748227900 has devpath '/devices/pci0000:00'
Jun  5 10:16:22 taroona udevd[483]: IMPORT builtin 'usb_id' /lib/udev/rules.d/40-libgphoto2-2.rules:11
Jun  5 10:16:22 taroona udevd[483]: ID_VENDOR=Qualcomm_Incorporated
Jun  5 10:16:22 taroona udevd[483]: ID_VENDOR_ENC=Qualcomm\x20Incorporated
Jun  5 10:16:22 taroona udevd[483]: ID_VENDOR_ID=05c6
Jun  5 10:16:22 taroona udevd[483]: ID_MODEL=Qualcomm_Gobi_2000
Jun  5 10:16:22 taroona udevd[483]: ID_MODEL_ENC=Qualcomm\x20Gobi\x202000
Jun  5 10:16:22 taroona udevd[483]: ID_MODEL_ID=9205
Jun  5 10:16:22 taroona udevd[483]: ID_REVISION=0002
Jun  5 10:16:22 taroona udevd[483]: ID_SERIAL=Qualcomm_Incorporated_Qualcomm_Gobi_2000
Jun  5 10:16:22 taroona udevd[483]: ID_BUS=usb
Jun  5 10:16:22 taroona udevd[483]: ID_USB_INTERFACES=:ffffff:
Jun  5 10:16:22 taroona udevd[483]: MODE 0664 /lib/udev/rules.d/50-udev-default.rules:55
Jun  5 10:16:22 taroona udevd[483]: IMPORT builtin skip 'usb_id' /lib/udev/rules.d/50-udev-default.rules:56
Jun  5 10:16:22 taroona udevd[483]: PROGRAM 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 2 5' /lib/udev/rules.d/69-libmtp.rules:884
Jun  5 10:16:22 taroona udevd[1710]: starting 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 2 5'
Jun  5 10:16:22 taroona udevd[456]: seq 2448 queued, 'add' 'usb'
Jun  5 10:16:22 taroona udevd[456]: seq 2449 queued, 'add' 'usb'
Jun  5 10:16:23 taroona mtp-probe: checking bus 2, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Jun  5 10:16:23 taroona udevd[456]: seq 2450 queued, 'add' 'usb-serial'
Jun  5 10:16:23 taroona udevd[456]: seq 2451 queued, 'add' 'tty'
Jun  5 10:16:23 taroona udevd[456]: seq 2452 queued, 'add' 'usb'
Jun  5 10:16:23 taroona udevd[456]: seq 2453 queued, 'add' 'usb-serial'
Jun  5 10:16:23 taroona udevd[456]: seq 2454 queued, 'add' 'tty'
Jun  5 10:16:23 taroona udevd[456]: seq 2455 queued, 'add' 'usb'
Jun  5 10:16:23 taroona kernel: [   36.424525] qcserial 2-1.4:1.1: Qualcomm USB modem converter detected
Jun  5 10:16:23 taroona kernel: [   36.424673] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB0
Jun  5 10:16:23 taroona kernel: [   36.425777] qcserial 2-1.4:1.2: Qualcomm USB modem converter detected
Jun  5 10:16:23 taroona kernel: [   36.425904] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB1
Jun  5 10:16:23 taroona udevd[456]: seq 2456 queued, 'add' 'usb-serial'
Jun  5 10:16:23 taroona udevd[456]: seq 2457 queued, 'add' 'tty'
Jun  5 10:16:23 taroona mtp-probe: bus: 2, device: 5 was not an MTP device
Jun  5 10:16:23 taroona udevd[483]: 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 2 5'(out) '0'
Jun  5 10:16:23 taroona udevd[483]: 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 2 5' [1710] exit with return code 0
Jun  5 10:16:23 taroona udevd[483]: no node name set, will use kernel supplied name 'bus/usb/002/005'
Jun  5 10:16:23 taroona udevd[483]: creating device node '/dev/bus/usb/002/005', devnum=189:132, mode=0664, uid=0, gid=0
Jun  5 10:16:23 taroona udevd[483]: preserve file '/dev/bus/usb/002/005', because it has correct dev_t
Jun  5 10:16:23 taroona udevd[483]: set permissions /dev/bus/usb/002/005, 020664, uid=0, gid=0
Jun  5 10:16:23 taroona udevd[483]: creating symlink '/dev/char/189:132' to '../bus/usb/002/005'
Jun  5 10:16:23 taroona udevd[483]: created db file '/run/udev/data/c189:132' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:23 taroona udevd[483]: seq 2447 processed with 0
Jun  5 10:16:23 taroona udevd[456]: seq 2447 done with 0
Jun  5 10:16:23 taroona udevd[456]: passed 309 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:23 taroona udevd[483]: seq 2448 running
Jun  5 10:16:23 taroona udevd[485]: seq 2449 running
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1'
Jun  5 10:16:23 taroona kernel: [   36.426597] qcserial 2-1.4:1.3: Qualcomm USB modem converter detected
Jun  5 10:16:23 taroona kernel: [   36.426864] usb 2-1.4: Qualcomm USB modem converter now attached to ttyUSB2
Jun  5 10:16:23 taroona udevd[483]: no db file to read /run/udev/data/+usb:2-1.4:1.0: No such file or directory
Jun  5 10:16:23 taroona udevd[485]: no db file to read /run/udev/data/+usb:2-1.4:1.1: No such file or directory
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748228930 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa7482153a0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748214db0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748214b40 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748214fe0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748213ad0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748214020 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748226ad0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748216540 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[483]: device 0x7fa748213dc0 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[483]: RUN 'usb_modeswitch --driver-bind %p %s{idVendor} %s{idProduct} %E{PRODUCT}' /lib/udev/rules.d/40-usb_modeswitch.rules:16
Jun  5 10:16:23 taroona udevd[485]: created db file '/run/udev/data/+usb:2-1.4:1.1' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1'
Jun  5 10:16:23 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:23 taroona udevd[485]: seq 2449 processed with 0
Jun  5 10:16:23 taroona udevd[456]: passed 309 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:23  udevd[456]: last message repeated 2 times
Jun  5 10:16:23 taroona udevd[456]: seq 2449 done with 0
Jun  5 10:16:23 taroona udevd[483]: RUN '/sbin/modprobe -bv $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5
Jun  5 10:16:23 taroona udevd[486]: seq 2452 running
Jun  5 10:16:23 taroona udevd[487]: seq 2455 running
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748213de0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748215290 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3'
Jun  5 10:16:23 taroona udevd[483]: created db file '/run/udev/data/+usb:2-1.4:1.0' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0'
Jun  5 10:16:23 taroona udevd[485]: seq 2450 running
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0'
Jun  5 10:16:23 taroona udevd[487]: no db file to read /run/udev/data/+usb:2-1.4:1.3: No such file or directory
Jun  5 10:16:23 taroona udevd[486]: no db file to read /run/udev/data/+usb:2-1.4:1.2: No such file or directory
Jun  5 10:16:23 taroona udevd[485]: no db file to read /run/udev/data/+usb-serial:ttyUSB0: No such file or directory
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748215f10 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748228510 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748216710 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748214e20 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748227a50 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748215070 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748216240 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748227520 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748213b10 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748213de0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748226fb0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa7482167c0 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748214340 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[1711]: starting 'usb_modeswitch --driver-bind /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0   5c6/9205/2'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748214540 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748214590 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748227070 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[487]: created db file '/run/udev/data/+usb:2-1.4:1.3' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3'
Jun  5 10:16:23 taroona udevd[485]: created db file '/run/udev/data/+usb-serial:ttyUSB0' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0'
Jun  5 10:16:23 taroona udevd[486]: created db file '/run/udev/data/+usb:2-1.4:1.2' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2'
Jun  5 10:16:23 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:23 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:23 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:23 taroona udevd[485]: seq 2450 processed with 0
Jun  5 10:16:23 taroona udevd[487]: seq 2455 processed with 0
Jun  5 10:16:23 taroona udevd[486]: seq 2452 processed with 0
Jun  5 10:16:23 taroona udevd[456]: passed 195 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:23 taroona udevd[456]: seq 2450 done with 0
Jun  5 10:16:23 taroona udevd[456]: seq 2455 done with 0
Jun  5 10:16:23 taroona udevd[456]: seq 2452 done with 0
Jun  5 10:16:23 taroona udevd[485]: seq 2451 running
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748216b80 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: no db file to read /run/udev/data/c188:0: No such file or directory
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748227510 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748226e30 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748227c10 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748216220 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa748214c80 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[485]: device 0x7fa7482151c0 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[485]: PROGRAM 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0 05c6 9205 ' /lib/udev/rules.d/40-usb_modeswitch.rules:9
Jun  5 10:16:23 taroona udevd[456]: passed 234 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:23 taroona udevd[1713]: starting 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0 05c6 9205 '
Jun  5 10:16:23 taroona udevd[456]: passed 195 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:23 taroona udevd[486]: seq 2453 running
Jun  5 10:16:23 taroona udevd[456]: passed 195 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748213310 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1'
Jun  5 10:16:23 taroona udevd[487]: seq 2456 running
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748215760 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2'
Jun  5 10:16:23 taroona udevd[486]: no db file to read /run/udev/data/+usb-serial:ttyUSB1: No such file or directory
Jun  5 10:16:23 taroona udevd[487]: no db file to read /run/udev/data/+usb-serial:ttyUSB2: No such file or directory
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748213be0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa7482154a0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748227b80 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa7482141e0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748213ad0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa7482282a0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748214590 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748214ae0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748214130 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748216200 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748214f20 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748215460 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[487]: created db file '/run/udev/data/+usb-serial:ttyUSB2' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:23 taroona udevd[487]: seq 2456 processed with 0
Jun  5 10:16:23 taroona udevd[456]: seq 2456 done with 0
Jun  5 10:16:23 taroona udevd[486]: created db file '/run/udev/data/+usb-serial:ttyUSB1' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1'
Jun  5 10:16:23 taroona udevd[487]: seq 2457 running
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748216e00 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2'
Jun  5 10:16:23 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:23 taroona udevd[486]: seq 2453 processed with 0
Jun  5 10:16:23 taroona udevd[487]: no db file to read /run/udev/data/c188:2: No such file or directory
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748213720 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748214220 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748216af0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748213ad0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748214590 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748214ac0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[487]: device 0x7fa748215110 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[487]: PROGRAM 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2 05c6 9205 ' /lib/udev/rules.d/40-usb_modeswitch.rules:9
Jun  5 10:16:23 taroona udevd[456]: passed 234 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:23 taroona udevd[456]: seq 2453 done with 0
Jun  5 10:16:23 taroona udevd[456]: passed 234 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:23 taroona udevd[1719]: starting 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2 05c6 9205 '
Jun  5 10:16:23 taroona udevd[486]: seq 2454 running
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748213be0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: no db file to read /run/udev/data/c188:1: No such file or directory
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748227b80 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748227e90 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748214870 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa7482285d0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun  5 10:16:23 taroona udevd[485]: 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0 05c6 9205 ' [1713] exit with return code 0
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748214110 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun  5 10:16:23 taroona udevd[485]: GROUP 20 /lib/udev/rules.d/50-udev-default.rules:11
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748214f20 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun  5 10:16:23 taroona udevd[486]: device 0x7fa748226b10 has devpath '/devices/pci0000:00'
Jun  5 10:16:23 taroona udevd[485]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-persistent-serial.rules:9
Jun  5 10:16:23 taroona udevd[486]: PROGRAM 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1 05c6 9205 ' /lib/udev/rules.d/40-usb_modeswitch.rules:9
Jun  5 10:16:23 taroona udevd[485]: ID_PATH=pci-0000:00:1d.0-usb-0:1.4:1.1
Jun  5 10:16:23 taroona udevd[485]: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_1_4_1_1
Jun  5 10:16:23 taroona udevd[485]: LINK 'serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.1-port0' /lib/udev/rules.d/60-persistent-serial.rules:11
Jun  5 10:16:23 taroona udevd[485]: IMPORT builtin 'usb_id' /lib/udev/rules.d/60-persistent-serial.rules:13
Jun  5 10:16:23 taroona udevd[485]: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1: if_class 255 protocol 0
Jun  5 10:16:23 taroona udevd[1720]: starting 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1 05c6 9205 '
Jun  5 10:16:23 taroona udevd[485]: ID_VENDOR=Qualcomm_Incorporated
Jun  5 10:16:23 taroona udevd[485]: ID_VENDOR_ENC=Qualcomm\x20Incorporated
Jun  5 10:16:23 taroona udevd[485]: ID_VENDOR_ID=05c6
Jun  5 10:16:23 taroona udevd[485]: ID_MODEL=Qualcomm_Gobi_2000
Jun  5 10:16:23 taroona udevd[485]: ID_MODEL_ENC=Qualcomm\x20Gobi\x202000
Jun  5 10:16:23 taroona udevd[485]: ID_MODEL_ID=9205
Jun  5 10:16:23 taroona udevd[485]: ID_REVISION=0002
Jun  5 10:16:23 taroona udevd[485]: ID_SERIAL=Qualcomm_Incorporated_Qualcomm_Gobi_2000
Jun  5 10:16:23 taroona udevd[485]: ID_TYPE=generic
Jun  5 10:16:23 taroona udevd[485]: ID_BUS=usb
Jun  5 10:16:23 taroona udevd[485]: ID_USB_INTERFACES=:ffffff:
Jun  5 10:16:23 taroona udevd[485]: ID_USB_INTERFACE_NUM=01
Jun  5 10:16:23 taroona udevd[485]: ID_USB_DRIVER=qcserial
Jun  5 10:16:23 taroona udevd[485]: LINK 'serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0' /lib/udev/rules.d/60-persistent-serial.rules:18
Jun  5 10:16:23 taroona udevd[485]: IMPORT 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0' /lib/udev/rules.d/75-tty-description.rules:7
Jun  5 10:16:23 taroona udevd[1723]: starting 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'
Jun  5 10:16:23 taroona udevd[487]: 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2 05c6 9205 ' [1719] exit with return code 0
Jun  5 10:16:23 taroona udevd[487]: GROUP 20 /lib/udev/rules.d/50-udev-default.rules:11
Jun  5 10:16:23 taroona udevd[487]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-persistent-serial.rules:9
Jun  5 10:16:23 taroona udevd[485]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'(err) 'libudev: udev_device_new_from_syspath: device 0x7fa8b448a580 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0''
Jun  5 10:16:23 taroona udevd[485]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'(err) 'libudev: udev_device_new_from_syspath: device 0x7fa8b448aa40 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0''
Jun  5 10:16:23 taroona udevd[487]: ID_PATH=pci-0000:00:1d.0-usb-0:1.4:1.3
Jun  5 10:16:23 taroona udevd[487]: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_1_4_1_3
Jun  5 10:16:23 taroona udevd[485]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'(err) 'libudev: udev_device_new_from_syspath: device 0x7fa8b448b060 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1''
Jun  5 10:16:23 taroona udevd[487]: LINK 'serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.3-port0' /lib/udev/rules.d/60-persistent-serial.rules:11
Jun  5 10:16:23 taroona udevd[487]: IMPORT builtin 'usb_id' /lib/udev/rules.d/60-persistent-serial.rules:13
Jun  5 10:16:23 taroona udevd[485]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'(err) 'libudev: udev_device_new_from_syspath: device 0x7fa8b448b680 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4''
Jun  5 10:16:23 taroona udevd[487]: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3: if_class 255 protocol 0
Jun  5 10:16:23 taroona udevd[486]: 'usb_modeswitch --symlink-name /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1 05c6 9205 ' [1720] exit with return code 0
Jun  5 10:16:23 taroona udevd[486]: GROUP 20 /lib/udev/rules.d/50-udev-default.rules:11
Jun  5 10:16:23 taroona udevd[487]: ID_VENDOR=Qualcomm_Incorporated
Jun  5 10:16:23 taroona udevd[487]: ID_VENDOR_ENC=Qualcomm\x20Incorporated
Jun  5 10:16:23 taroona udevd[487]: ID_VENDOR_ID=05c6
Jun  5 10:16:23 taroona udevd[487]: ID_MODEL=Qualcomm_Gobi_2000
Jun  5 10:16:23 taroona udevd[487]: ID_MODEL_ENC=Qualcomm\x20Gobi\x202000
Jun  5 10:16:23 taroona udevd[487]: ID_MODEL_ID=9205
Jun  5 10:16:23 taroona udevd[487]: ID_REVISION=0002
Jun  5 10:16:23 taroona udevd[487]: ID_SERIAL=Qualcomm_Incorporated_Qualcomm_Gobi_2000
Jun  5 10:16:23 taroona udevd[487]: ID_TYPE=generic
Jun  5 10:16:23 taroona udevd[487]: ID_BUS=usb
Jun  5 10:16:23 taroona udevd[487]: ID_USB_INTERFACES=:ffffff:
Jun  5 10:16:23 taroona udevd[487]: ID_USB_INTERFACE_NUM=03
Jun  5 10:16:23 taroona udevd[487]: ID_USB_DRIVER=qcserial
Jun  5 10:16:23 taroona udevd[487]: LINK 'serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if03-port0' /lib/udev/rules.d/60-persistent-serial.rules:18
Jun  5 10:16:23 taroona udevd[487]: IMPORT 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2' /lib/udev/rules.d/75-tty-description.rules:7
Jun  5 10:16:23 taroona udevd[486]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-persistent-serial.rules:9
Jun  5 10:16:23 taroona udevd[486]: ID_PATH=pci-0000:00:1d.0-usb-0:1.4:1.2
Jun  5 10:16:23 taroona udevd[486]: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_1_4_1_2
Jun  5 10:16:23 taroona udevd[486]: LINK 'serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.2-port0' /lib/udev/rules.d/60-persistent-serial.rules:11
Jun  5 10:16:23 taroona udevd[486]: IMPORT builtin 'usb_id' /lib/udev/rules.d/60-persistent-serial.rules:13
Jun  5 10:16:23 taroona udevd[1725]: starting 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2'
Jun  5 10:16:23 taroona udevd[486]: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2: if_class 255 protocol 0
Jun  5 10:16:23 taroona udevd[486]: ID_VENDOR=Qualcomm_Incorporated
Jun  5 10:16:23 taroona udevd[486]: ID_VENDOR_ENC=Qualcomm\x20Incorporated
Jun  5 10:16:23 taroona udevd[486]: ID_VENDOR_ID=05c6
Jun  5 10:16:23 taroona udevd[486]: ID_MODEL=Qualcomm_Gobi_2000
Jun  5 10:16:23 taroona udevd[486]: ID_MODEL_ENC=Qualcomm\x20Gobi\x202000
Jun  5 10:16:23 taroona udevd[486]: ID_MODEL_ID=9205
Jun  5 10:16:23 taroona udevd[486]: ID_REVISION=0002
Jun  5 10:16:23 taroona udevd[486]: ID_SERIAL=Qualcomm_Incorporated_Qualcomm_Gobi_2000
Jun  5 10:16:23 taroona udevd[486]: ID_TYPE=generic
Jun  5 10:16:23 taroona udevd[486]: ID_BUS=usb
Jun  5 10:16:23 taroona udevd[486]: ID_USB_INTERFACES=:ffffff:
Jun  5 10:16:23 taroona udevd[486]: ID_USB_INTERFACE_NUM=02
Jun  5 10:16:23 taroona udevd[486]: ID_USB_DRIVER=qcserial
Jun  5 10:16:23 taroona udevd[486]: LINK 'serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if02-port0' /lib/udev/rules.d/60-persistent-serial.rules:18
Jun  5 10:16:23 taroona udevd[486]: IMPORT 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1' /lib/udev/rules.d/75-tty-description.rules:7
Jun  5 10:16:23 taroona udevd[1726]: starting 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1'
Jun  5 10:16:23 taroona udevd[487]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2'(err) 'libudev: udev_device_new_from_syspath: device 0x7fa7d1564580 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2''
Jun  5 10:16:23 taroona udevd[487]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2'(err) 'libudev: udev_device_new_from_syspath: device 0x7fa7d1564a40 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2''
Jun  5 10:16:23 taroona udevd[487]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2'(err) 'libudev: udev_device_new_from_syspath: device 0x7fa7d1565060 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3''
Jun  5 10:16:23 taroona udevd[487]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2'(err) 'libudev: udev_device_new_from_syspath: device 0x7fa7d1565680 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4''
Jun  5 10:16:23 taroona udevd[486]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1'(err) 'libudev: udev_device_new_from_syspath: device 0x7f43bf27d580 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1''
Jun  5 10:16:23 taroona udevd[486]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1'(err) 'libudev: udev_device_new_from_syspath: device 0x7f43bf27da40 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1''
Jun  5 10:16:23 taroona udevd[486]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1'(err) 'libudev: udev_device_new_from_syspath: device 0x7f43bf27e060 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2''
Jun  5 10:16:23 taroona udevd[486]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1'(err) 'libudev: udev_device_new_from_syspath: device 0x7f43bf27e680 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4''
Jun  5 10:16:23 taroona udevd[485]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'(out) 'ID_VENDOR_FROM_DATABASE=Qualcomm, Inc.'
Jun  5 10:16:23 taroona udevd[485]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0' [1723] exit with return code 0
Jun  5 10:16:23 taroona udevd[485]: no node name set, will use kernel supplied name 'ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: creating device node '/dev/ttyUSB0', devnum=188:0, mode=0660, uid=0, gid=20
Jun  5 10:16:23 taroona udevd[485]: preserve file '/dev/ttyUSB0', because it has correct dev_t
Jun  5 10:16:23 taroona udevd[485]: set permissions /dev/ttyUSB0, 020660, uid=0, gid=20
Jun  5 10:16:23 taroona udevd[485]: creating symlink '/dev/char/188:0' to '../ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: creating link '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0' to '/dev/ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: creating symlink '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0' to '../../ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: creating link '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.1-port0' to '/dev/ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: creating symlink '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.1-port0' to '../../ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: created db file '/run/udev/data/c188:0' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1/ttyUSB0/tty/ttyUSB0'
Jun  5 10:16:23 taroona udevd[485]: passed -1 bytes to netlink monitor 0x7fa74825b460
Jun  5 10:16:23 taroona udevd[485]: seq 2451 processed with 0
Jun  5 10:16:23 taroona udevd[487]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2'(out) 'ID_VENDOR_FROM_DATABASE=Qualcomm, Inc.'
Jun  5 10:16:23 taroona udevd[487]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2' [1725] exit with return code 0
Jun  5 10:16:23 taroona udevd[487]: no node name set, will use kernel supplied name 'ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: creating device node '/dev/ttyUSB2', devnum=188:2, mode=0660, uid=0, gid=20
Jun  5 10:16:23 taroona udevd[487]: preserve file '/dev/ttyUSB2', because it has correct dev_t
Jun  5 10:16:23 taroona udevd[487]: set permissions /dev/ttyUSB2, 020660, uid=0, gid=20
Jun  5 10:16:23 taroona udevd[487]: creating symlink '/dev/char/188:2' to '../ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: creating link '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if03-port0' to '/dev/ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: creating symlink '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if03-port0' to '../../ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: creating link '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.3-port0' to '/dev/ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: creating symlink '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.3-port0' to '../../ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: created db file '/run/udev/data/c188:2' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3/ttyUSB2/tty/ttyUSB2'
Jun  5 10:16:23 taroona udevd[487]: passed -1 bytes to netlink monitor 0x7fa74825c9a0
Jun  5 10:16:23 taroona udevd[487]: seq 2457 processed with 0
Jun  5 10:16:23 taroona udevd[456]: seq 2451 done with 0
Jun  5 10:16:23 taroona udevd[456]: seq 2457 done with 0
Jun  5 10:16:23 taroona udevd[486]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1'(out) 'ID_VENDOR_FROM_DATABASE=Qualcomm, Inc.'
Jun  5 10:16:23 taroona udevd[486]: 'usb-db /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1' [1726] exit with return code 0
Jun  5 10:16:23 taroona udevd[486]: no node name set, will use kernel supplied name 'ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: creating device node '/dev/ttyUSB1', devnum=188:1, mode=0660, uid=0, gid=20
Jun  5 10:16:23 taroona udevd[486]: preserve file '/dev/ttyUSB1', because it has correct dev_t
Jun  5 10:16:23 taroona udevd[486]: set permissions /dev/ttyUSB1, 020660, uid=0, gid=20
Jun  5 10:16:23 taroona udevd[486]: creating symlink '/dev/char/188:1' to '../ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: creating link '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if02-port0' to '/dev/ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: creating symlink '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if02-port0' to '../../ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: creating link '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.2-port0' to '/dev/ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: creating symlink '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.2-port0' to '../../ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: created db file '/run/udev/data/c188:1' for '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2/ttyUSB1/tty/ttyUSB1'
Jun  5 10:16:23 taroona udevd[486]: passed -1 bytes to netlink monitor 0x7fa74825bda0
Jun  5 10:16:23 taroona udevd[486]: seq 2454 processed with 0
Jun  5 10:16:23 taroona udevd[456]: seq 2454 done with 0
Jun  5 10:16:23 taroona modem-manager[1048]: <info>  (ttyUSB0) opening serial port...
Jun  5 10:16:23 taroona modem-manager[1048]: <info>  (ttyUSB2) opening serial port...
Jun  5 10:16:23 taroona modem-manager[1048]: <info>  (ttyUSB1) opening serial port...
Jun  5 10:16:23 taroona anacron[1706]: Normal exit (0 jobs run)
Jun  5 10:16:23 taroona acpid: client connected from 1282[0:0]
Jun  5 10:16:23 taroona acpid: 1 client rule loaded
Jun  5 10:16:23 taroona dbus[1035]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jun  5 10:16:23 taroona dbus[1035]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jun  5 10:16:23 taroona accounts-daemon[1905]: started daemon version 0.6.15
Jun  5 10:16:23 taroona dbus[1035]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jun  5 10:16:23 taroona dbus[1035]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jun  5 10:16:24 taroona udevd[483]: 'usb_modeswitch --driver-bind /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0   5c6/9205/2' [1711] exit with return code 0
Jun  5 10:16:24 taroona udevd[1995]: starting '/sbin/modprobe -bv usb:v05C6p9205d0002dc00dsc00dp00icFFiscFFipFF'
Jun  5 10:16:24 taroona udevd[483]: '/sbin/modprobe -bv usb:v05C6p9205d0002dc00dsc00dp00icFFiscFFipFF' [1995] exit with return code 0
Jun  5 10:16:24 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:24 taroona udevd[483]: seq 2448 processed with 0
Jun  5 10:16:24 taroona udevd[456]: seq 2448 done with 0
Jun  5 10:16:24 taroona kernel: [   37.590710] cfg80211: Found new beacon on frequency: 5805 MHz (Ch 161) on phy0
Jun  5 10:16:24 taroona udevd[456]: seq 2458 queued, 'add' 'bdi'
Jun  5 10:16:24 taroona udevd[483]: seq 2458 running
Jun  5 10:16:24 taroona udevd[483]: device 0x7fa748213720 has devpath '/devices/virtual/bdi/0:20'
Jun  5 10:16:24 taroona udevd[483]: no db file to read /run/udev/data/+bdi:0:20: No such file or directory
Jun  5 10:16:24 taroona udevd[483]: created db file '/run/udev/data/+bdi:0:20' for '/devices/virtual/bdi/0:20'
Jun  5 10:16:24 taroona udevd[483]: passed -1 bytes to netlink monitor 0x7fa7482133f0
Jun  5 10:16:24 taroona udevd[483]: seq 2458 processed with 0
Jun  5 10:16:24 taroona udevd[456]: passed 148 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:24 taroona udevd[456]: seq 2458 done with 0
Jun  5 10:16:24 taroona dbus[1035]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jun  5 10:16:24 taroona dbus[1035]: [system] Successfully activated service 'org.freedesktop.UPower'
Jun  5 10:16:24 taroona udevadm[2085]: custom logging function 0x7f0fd5d8a250 registered
Jun  5 10:16:24 taroona udevadm[2085]: selinux=0
Jun  5 10:16:24 taroona udevadm[2085]: runtime dir '/run/udev'
Jun  5 10:16:24 taroona udevadm[2085]: calling: info
Jun  5 10:16:24 taroona udevadm[2085]: device 0x7f0fd5d8a2d0 has devpath '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda'
Jun  5 10:16:24 taroona udevadm[2085]: device 0x7f0fd5d8a2d0 filled with db file data
Jun  5 10:16:24 taroona udevadm[2093]: custom logging function 0x7f93129cf250 registered
Jun  5 10:16:24 taroona udevadm[2093]: selinux=0
Jun  5 10:16:24 taroona udevadm[2093]: runtime dir '/run/udev'
Jun  5 10:16:24 taroona udevadm[2093]: calling: info
Jun  5 10:16:24 taroona udevadm[2093]: device 0x7f93129cf2d0 has devpath '/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0/block/sda'
Jun  5 10:16:24 taroona udevadm[2093]: device 0x7f93129cf2d0 filled with db file data
Jun  5 10:16:24 taroona udevadm[2100]: custom logging function 0x7f6ea9730250 registered
Jun  5 10:16:24 taroona udevadm[2100]: selinux=0
Jun  5 10:16:24 taroona udevadm[2100]: runtime dir '/run/udev'
Jun  5 10:16:24 taroona udevadm[2100]: calling: info
Jun  5 10:16:24 taroona udevadm[2100]: device 0x7f6ea97302d0 has devpath '/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sdb'
Jun  5 10:16:24 taroona udevadm[2100]: device 0x7f6ea97302d0 filled with db file data
Jun  5 10:16:24 taroona udevadm[2108]: custom logging function 0x7fd683120250 registered
Jun  5 10:16:24 taroona udevadm[2108]: selinux=0
Jun  5 10:16:24 taroona udevadm[2108]: runtime dir '/run/udev'
Jun  5 10:16:24 taroona udevadm[2108]: calling: info
Jun  5 10:16:24 taroona udevadm[2108]: device 0x7fd6831202d0 has devpath '/devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sdb'
Jun  5 10:16:24 taroona udevadm[2108]: device 0x7fd6831202d0 filled with db file data
Jun  5 10:16:24 taroona anacron[2117]: Anacron 2.3 started on 2013-06-05
Jun  5 10:16:24 taroona anacron[2117]: Normal exit (0 jobs run)
Jun  5 10:16:24 taroona dbus[1035]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jun  5 10:16:24 taroona dbus[1035]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jun  5 10:16:24 taroona rtkit-daemon[2303]: Successfully called chroot.
Jun  5 10:16:24 taroona rtkit-daemon[2303]: Successfully dropped privileges.
Jun  5 10:16:24 taroona rtkit-daemon[2303]: Successfully limited resources.
Jun  5 10:16:24 taroona rtkit-daemon[2303]: Running.
Jun  5 10:16:24 taroona rtkit-daemon[2303]: Canary thread running.
Jun  5 10:16:24 taroona rtkit-daemon[2303]: Watchdog thread running.
Jun  5 10:16:24 taroona rtkit-daemon[2303]: Successfully made thread 2301 of process 2301 (n/a) owned by '104' high priority at nice level -11.
Jun  5 10:16:24 taroona rtkit-daemon[2303]: Supervising 1 threads of 1 processes of 1 users.
Jun  5 10:16:25 taroona rtkit-daemon[2303]: Successfully made thread 2311 of process 2301 (n/a) owned by '104' RT at priority 5.
Jun  5 10:16:25 taroona rtkit-daemon[2303]: Supervising 2 threads of 1 processes of 1 users.
Jun  5 10:16:25 taroona rtkit-daemon[2303]: Successfully made thread 2312 of process 2301 (n/a) owned by '104' RT at priority 5.
Jun  5 10:16:25 taroona rtkit-daemon[2303]: Supervising 3 threads of 1 processes of 1 users.
Jun  5 10:16:25 taroona rtkit-daemon[2303]: Successfully made thread 2313 of process 2301 (n/a) owned by '104' RT at priority 5.
Jun  5 10:16:25 taroona rtkit-daemon[2303]: Supervising 4 threads of 1 processes of 1 users.
Jun  5 10:16:25 taroona bluetoothd[1050]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/HFPAG
Jun  5 10:16:25 taroona bluetoothd[1050]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/A2DPSource
Jun  5 10:16:25 taroona bluetoothd[1050]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/A2DPSink
Jun  5 10:16:25 taroona pulseaudio[2301]: [pulseaudio] bluetooth-util.c: Property name not a string.
Jun  5 10:16:25 taroona pulseaudio[2301]: [pulseaudio] bluetooth-util.c: Property name not a string.
Jun  5 10:16:25 taroona rtkit-daemon[2303]: Successfully made thread 2316 of process 2316 (n/a) owned by '104' high priority at nice level -11.
Jun  5 10:16:25 taroona rtkit-daemon[2303]: Supervising 5 threads of 2 processes of 1 users.
Jun  5 10:16:25 taroona pulseaudio[2316]: [pulseaudio] pid.c: Daemon already running.
Jun  5 10:16:27 taroona udevd[456]: worker [483] exit

...... removed many udevd thread clean up entries

Jun  5 10:16:28 taroona modem-manager[1048]: <info>  (ttyUSB1) closing serial port...
Jun  5 10:16:28 taroona modem-manager[1048]: <info>  (ttyUSB1) serial port closed
Jun  5 10:16:28 taroona modem-manager[1048]: <info>  (ttyUSB1) opening serial port...
Jun  5 10:16:28 taroona modem-manager[1048]: <info>  (Gobi): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4 claimed port ttyUSB1
Jun  5 10:16:30 taroona modem-manager[1048]: <info>  (ttyS4) closing serial port...
Jun  5 10:16:30 taroona modem-manager[1048]: <info>  (ttyS4) serial port closed
Jun  5 10:16:30 taroona modem-manager[1048]: <info>  (ttyS4) opening serial port...
Jun  5 10:16:30 taroona kernel: [   44.374527] vmnet1: no IPv6 routers present
Jun  5 10:16:31 taroona kernel: [   44.854155] vmnet8: no IPv6 routers present
Jun  5 10:16:32 taroona udevd[456]: seq 2459 queued, 'remove' 'bdi'
Jun  5 10:16:32 taroona udevd[456]: passed 151 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:32 taroona udevd[623]: seq 2459 running
Jun  5 10:16:32 taroona udevd[623]: device 0x7fa74824f3f0 filled with db file data
Jun  5 10:16:32 taroona udevd[623]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:16:32 taroona udevd[2335]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:16:32 taroona udevd[623]: '/etc/.mplab_ide/mchplinusbdevice remove ' [2335] exit with return code 0
Jun  5 10:16:32 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:16:32 taroona udevd[623]: seq 2459 processed with 0
Jun  5 10:16:32 taroona udevd[456]: seq 2459 done with 0
Jun  5 10:16:32 taroona modem-manager[1048]: <info>  (ttyUSB1) closing serial port...
Jun  5 10:16:32 taroona modem-manager[1048]: <info>  (ttyUSB1) serial port closed
Jun  5 10:16:33 taroona udevd[456]: seq 2460 queued, 'add' 'bdi'
Jun  5 10:16:33 taroona udevd[456]: passed 148 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:16:33 taroona udevd[623]: seq 2460 running
Jun  5 10:16:33 taroona udevd[623]: device 0x7fa748213da0 has devpath '/devices/virtual/bdi/0:20'
Jun  5 10:16:33 taroona udevd[623]: no db file to read /run/udev/data/+bdi:0:20: No such file or directory
Jun  5 10:16:33 taroona udevd[623]: created db file '/run/udev/data/+bdi:0:20' for '/devices/virtual/bdi/0:20'
Jun  5 10:16:33 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:16:33 taroona udevd[623]: seq 2460 processed with 0
Jun  5 10:16:33 taroona udevd[456]: seq 2460 done with 0
Jun  5 10:16:33 taroona rtkit-daemon[2303]: Successfully made thread 2453 of process 2453 (n/a) owned by '1000' high priority at nice level -11.
Jun  5 10:16:33 taroona rtkit-daemon[2303]: Supervising 5 threads of 2 processes of 2 users.
Jun  5 10:16:33 taroona dbus[1035]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Jun  5 10:16:33 taroona dbus[1035]: [system] Successfully activated service 'org.freedesktop.UDisks'
Jun  5 10:16:35 taroona rtkit-daemon[2303]: Successfully made thread 2508 of process 2453 (n/a) owned by '1000' RT at priority 5.
Jun  5 10:16:35 taroona rtkit-daemon[2303]: Supervising 6 threads of 2 processes of 2 users.
Jun  5 10:16:35 taroona rtkit-daemon[2303]: Successfully made thread 2509 of process 2453 (n/a) owned by '1000' RT at priority 5.
Jun  5 10:16:35 taroona rtkit-daemon[2303]: Supervising 7 threads of 2 processes of 2 users.
Jun  5 10:16:35 taroona rtkit-daemon[2303]: Successfully made thread 2510 of process 2453 (n/a) owned by '1000' RT at priority 5.
Jun  5 10:16:35 taroona rtkit-daemon[2303]: Supervising 8 threads of 2 processes of 2 users.
Jun  5 10:16:35 taroona bluetoothd[1050]: Endpoint registered: sender=:1.52 path=/MediaEndpoint/HFPAG
Jun  5 10:16:35 taroona bluetoothd[1050]: Endpoint registered: sender=:1.52 path=/MediaEndpoint/A2DPSource
Jun  5 10:16:35 taroona bluetoothd[1050]: Endpoint registered: sender=:1.52 path=/MediaEndpoint/A2DPSink
Jun  5 10:16:35 taroona pulseaudio[2453]: [pulseaudio] bluetooth-util.c: Property name not a string.
Jun  5 10:16:35 taroona pulseaudio[2453]: [pulseaudio] bluetooth-util.c: Property name not a string.
Jun  5 10:16:35 taroona modem-manager[1048]: <info>  (ttyUSB0) closing serial port...
Jun  5 10:16:35 taroona modem-manager[1048]: <info>  (ttyUSB0) serial port closed
Jun  5 10:16:35 taroona modem-manager[1048]: <info>  (ttyUSB0) opening serial port...
Jun  5 10:16:35 taroona modem-manager[1048]: <info>  (ttyUSB2) closing serial port...
Jun  5 10:16:35 taroona modem-manager[1048]: <info>  (ttyUSB2) serial port closed
Jun  5 10:16:35 taroona modem-manager[1048]: <info>  (ttyUSB2) opening serial port...
Jun  5 10:16:36 taroona modem-manager[1048]: <info>  (ttyS4) closing serial port...
Jun  5 10:16:36 taroona modem-manager[1048]: <info>  (ttyS4) serial port closed
Jun  5 10:16:38 taroona modem-manager[1048]: <info>  (ttyUSB0) closing serial port...
Jun  5 10:16:38 taroona modem-manager[1048]: <info>  (ttyUSB0) serial port closed
Jun  5 10:16:41 taroona modem-manager[1048]: <info>  (ttyUSB2) closing serial port...
Jun  5 10:16:41 taroona modem-manager[1048]: <info>  (ttyUSB2) serial port closed
Jun  5 10:16:41 taroona NetworkManager[1093]: <warn> (ttyUSB1): failed to look up interface index
Jun  5 10:16:41 taroona NetworkManager[1093]: <info> (ttyUSB1): new GSM/UMTS device (driver: 'qcserial' ifindex: 0)
Jun  5 10:16:41 taroona NetworkManager[1093]: <info> (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/3
Jun  5 10:16:41 taroona NetworkManager[1093]: <info> (ttyUSB1): now managed
Jun  5 10:16:41 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun  5 10:16:41 taroona NetworkManager[1093]: <info> (ttyUSB1): deactivating device (reason 'managed') [2]
Jun  5 10:16:41 taroona NetworkManager[1093]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Jun  5 10:16:41 taroona NetworkManager[1093]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Jun  5 10:16:41 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Jun  5 10:16:48 taroona goa[2624]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun  5 10:16:48 taroona kernel: [   62.075259] audit_printk_skb: 36 callbacks suppressed
Jun  5 10:16:48 taroona kernel: [   62.075261] type=1400 audit(1370391408.673:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=2619 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun  5 10:16:52 taroona bluetoothd[1050]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/HFPAG
Jun  5 10:16:52 taroona bluetoothd[1050]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/A2DPSource
Jun  5 10:16:52 taroona bluetoothd[1050]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/A2DPSink
Jun  5 10:16:59 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) starting connection 'Telstra_via_Gobi_2000'
Jun  5 10:16:59 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  5 10:16:59 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  5 10:16:59 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Jun  5 10:16:59 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Jun  5 10:16:59 taroona modem-manager[1048]: <info>  (ttyUSB1) opening serial port...
Jun  5 10:17:00 taroona modem-manager[1048]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Jun  5 10:17:00 taroona modem-manager[1048]: <info>  (ttyUSB1): using text mode for SMS
Jun  5 10:17:00 taroona modem-manager[1048]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> WWAN now enabled by management service
Jun  5 10:17:00 taroona modem-manager[1048]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Jun  5 10:17:00 taroona modem-manager[1048]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Jun  5 10:17:00 taroona modem-manager[1048]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> connected)
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> starting PPP connection
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> pppd started with pid 2712
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  5 10:17:00 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  5 10:17:00 taroona pppd[2712]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Jun  5 10:17:00 taroona pppd[2712]: pppd 2.4.5 started by root, uid 0
Jun  5 10:17:00 taroona udevd[456]: seq 2461 queued, 'add' 'module'
Jun  5 10:17:00 taroona udevd[456]: passed 143 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:00 taroona udevd[623]: seq 2461 running
Jun  5 10:17:00 taroona udevd[623]: device 0x7fa748213cf0 has devpath '/module/crc_ccitt'
Jun  5 10:17:00 taroona udevd[623]: no db file to read /run/udev/data/+module:crc_ccitt: No such file or directory
Jun  5 10:17:00 taroona udevd[623]: created db file '/run/udev/data/+module:crc_ccitt' for '/module/crc_ccitt'
Jun  5 10:17:00 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:00 taroona udevd[623]: seq 2461 processed with 0
Jun  5 10:17:00 taroona udevd[456]: seq 2461 done with 0
Jun  5 10:17:00 taroona udevd[456]: seq 2462 queued, 'add' 'module'
Jun  5 10:17:00 taroona udevd[456]: passed 143 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:00 taroona udevd[623]: seq 2462 running
Jun  5 10:17:00 taroona udevd[623]: device 0x7fa748214390 has devpath '/module/ppp_async'
Jun  5 10:17:00 taroona udevd[623]: no db file to read /run/udev/data/+module:ppp_async: No such file or directory
Jun  5 10:17:00 taroona udevd[623]: created db file '/run/udev/data/+module:ppp_async' for '/module/ppp_async'
Jun  5 10:17:00 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:00 taroona udevd[623]: seq 2462 processed with 0
Jun  5 10:17:00 taroona udevd[456]: seq 2462 done with 0
Jun  5 10:17:00 taroona udevd[456]: seq 2463 queued, 'add' 'net'
Jun  5 10:17:00 taroona udevd[456]: passed 173 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:00 taroona udevd[456]: seq 2464 queued, 'add' 'queues'
Jun  5 10:17:00 taroona udevd[623]: seq 2463 running
Jun  5 10:17:00 taroona udevd[456]: seq 2465 queued, 'add' 'queues'
Jun  5 10:17:00 taroona udevd[623]: device 0x7fa7482132d0 has devpath '/devices/virtual/net/ppp0'
Jun  5 10:17:00 taroona udevd[623]: no db file to read /run/udev/data/n6: No such file or directory
Jun  5 10:17:00 taroona udevd[623]: created db file '/run/udev/data/n6' for '/devices/virtual/net/ppp0'
Jun  5 10:17:00 taroona pppd[2712]: Using interface ppp0
Jun  5 10:17:00 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:00 taroona udevd[623]: seq 2463 processed with 0
Jun  5 10:17:00 taroona udevd[456]: seq 2463 done with 0
Jun  5 10:17:00 taroona pppd[2712]: Connect: ppp0 <--> /dev/ttyUSB1
Jun  5 10:17:00 taroona udevd[456]: passed 163 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:00 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun  5 10:17:00 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun  5 10:17:00 taroona udevd[654]: seq 2465 running
Jun  5 10:17:00 taroona udevd[654]: device 0x7fa7482152d0 has devpath '/devices/virtual/net/ppp0'
Jun  5 10:17:00 taroona udevd[623]: seq 2464 running
Jun  5 10:17:00 taroona udevd[623]: device 0x7fa7482132d0 has devpath '/devices/virtual/net/ppp0'
Jun  5 10:17:00 taroona udevd[654]: created db file '/run/udev/data/+queues:tx-0' for '/devices/virtual/net/ppp0/queues/tx-0'
Jun  5 10:17:00 taroona udevd[654]: passed -1 bytes to netlink monitor 0x7fa748258a40
Jun  5 10:17:00 taroona udevd[654]: seq 2465 processed with 0
Jun  5 10:17:00 taroona udevd[623]: created db file '/run/udev/data/+queues:rx-0' for '/devices/virtual/net/ppp0/queues/rx-0'
Jun  5 10:17:00 taroona udevd[456]: passed 163 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:00 taroona udevd[456]: seq 2465 done with 0
Jun  5 10:17:00 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:00 taroona udevd[623]: seq 2464 processed with 0
Jun  5 10:17:00 taroona udevd[456]: seq 2464 done with 0
Jun  5 10:17:00 taroona pppd[2712]: CHAP authentication succeeded
Jun  5 10:17:00 taroona pppd[2712]: CHAP authentication succeeded
Jun  5 10:17:00 taroona udevd[456]: seq 2466 queued, 'add' 'module'
Jun  5 10:17:00 taroona udevd[456]: passed 142 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:00 taroona udevd[623]: seq 2466 running
Jun  5 10:17:00 taroona udevd[623]: device 0x7fa748213720 has devpath '/module/bsd_comp'
Jun  5 10:17:00 taroona udevd[623]: no db file to read /run/udev/data/+module:bsd_comp: No such file or directory
Jun  5 10:17:00 taroona udevd[623]: created db file '/run/udev/data/+module:bsd_comp' for '/module/bsd_comp'
Jun  5 10:17:00 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:00 taroona udevd[623]: seq 2466 processed with 0
Jun  5 10:17:00 taroona udevd[456]: seq 2466 done with 0
Jun  5 10:17:00 taroona kernel: [   74.378966] PPP BSD Compression module registered
Jun  5 10:17:01 taroona udevd[456]: seq 2467 queued, 'add' 'module'
Jun  5 10:17:01 taroona udevd[456]: passed 146 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:01 taroona udevd[623]: seq 2467 running
Jun  5 10:17:01 taroona udevd[623]: device 0x7fa7482132d0 has devpath '/module/zlib_deflate'
Jun  5 10:17:01 taroona udevd[623]: no db file to read /run/udev/data/+module:zlib_deflate: No such file or directory
Jun  5 10:17:01 taroona udevd[623]: created db file '/run/udev/data/+module:zlib_deflate' for '/module/zlib_deflate'
Jun  5 10:17:01 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:01 taroona udevd[623]: seq 2467 processed with 0
Jun  5 10:17:01 taroona udevd[456]: seq 2467 done with 0
Jun  5 10:17:01 taroona udevd[456]: seq 2468 queued, 'add' 'module'
Jun  5 10:17:01 taroona udevd[456]: passed 145 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:01 taroona udevd[623]: seq 2468 running
Jun  5 10:17:01 taroona udevd[623]: device 0x7fa748213720 has devpath '/module/ppp_deflate'
Jun  5 10:17:01 taroona udevd[623]: no db file to read /run/udev/data/+module:ppp_deflate: No such file or directory
Jun  5 10:17:01 taroona udevd[623]: created db file '/run/udev/data/+module:ppp_deflate' for '/module/ppp_deflate'
Jun  5 10:17:01 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:01 taroona udevd[623]: seq 2468 processed with 0
Jun  5 10:17:01 taroona udevd[456]: seq 2468 done with 0
Jun  5 10:17:01 taroona kernel: [   74.391994] PPP Deflate Compression module registered
Jun  5 10:17:01 taroona CRON[2724]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  5 10:17:20 taroona NetworkManager[1093]: <warn> pppd timed out or didn't initialize our dbus module
Jun  5 10:17:20 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jun  5 10:17:20 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jun  5 10:17:20 taroona pppd[2712]: Terminating on signal 15
Jun  5 10:17:20 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jun  5 10:17:20 taroona NetworkManager[1093]: <warn> Activation (ttyUSB1) failed.
Jun  5 10:17:20 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jun  5 10:17:20 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun  5 10:17:20 taroona NetworkManager[1093]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Jun  5 10:17:20 taroona NetworkManager[1093]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Jun  5 10:17:20 taroona NetworkManager[1093]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Jun  5 10:17:20 taroona modem-manager[1048]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disconnecting)
Jun  5 10:17:22 taroona avahi-daemon[1100]: Withdrawing workstation service for ppp0.
Jun  5 10:17:22 taroona udevd[456]: seq 2469 queued, 'remove' 'queues'
Jun  5 10:17:22 taroona udevd[623]: seq 2469 running
Jun  5 10:17:22 taroona udevd[623]: device 0x7fa748213720 filled with db file data
Jun  5 10:17:22 taroona udevd[623]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:17:22 taroona udevd[456]: passed 166 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:22 taroona udevd[456]: seq 2470 queued, 'remove' 'queues'
Jun  5 10:17:22 taroona udevd[456]: passed 166 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:22 taroona udevd[456]: seq 2471 queued, 'remove' 'net'
Jun  5 10:17:22 taroona udevd[654]: seq 2470 running
Jun  5 10:17:22 taroona udevd[2855]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:17:22 taroona udevd[654]: device 0x7fa7482132d0 filled with db file data
Jun  5 10:17:22 taroona udevd[654]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:17:22 taroona udevd[2856]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:17:22 taroona udevd[623]: '/etc/.mplab_ide/mchplinusbdevice remove ' [2855] exit with return code 0
Jun  5 10:17:22 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:22 taroona udevd[623]: seq 2469 processed with 0
Jun  5 10:17:22 taroona udevd[456]: seq 2469 done with 0
Jun  5 10:17:22 taroona udevd[654]: '/etc/.mplab_ide/mchplinusbdevice remove ' [2856] exit with return code 0
Jun  5 10:17:22 taroona udevd[654]: passed -1 bytes to netlink monitor 0x7fa748258a40
Jun  5 10:17:22 taroona udevd[654]: seq 2470 processed with 0
Jun  5 10:17:22 taroona udevd[456]: seq 2470 done with 0
Jun  5 10:17:22 taroona udevd[456]: passed 176 bytes to netlink monitor 0x7fa7482132d0
Jun  5 10:17:22 taroona udevd[623]: seq 2471 running
Jun  5 10:17:22 taroona udevd[623]: device 0x7fa748213720 filled with db file data
Jun  5 10:17:22 taroona udevd[623]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun  5 10:17:22 taroona udevd[2857]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun  5 10:17:22 taroona udevd[623]: '/etc/.mplab_ide/mchplinusbdevice remove ' [2857] exit with return code 0
Jun  5 10:17:22 taroona udevd[623]: passed -1 bytes to netlink monitor 0x7fa74822a640
Jun  5 10:17:22 taroona udevd[623]: seq 2471 processed with 0
Jun  5 10:17:22 taroona udevd[456]: seq 2471 done with 0
Jun  5 10:17:22 taroona NetworkManager[1093]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun  5 10:17:25 taroona modem-manager[1048]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (disconnecting -> registered)
Jun  5 10:17:36 taroona dbus[1035]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jun  5 10:17:36 taroona AptDaemon: INFO: Initializing daemon
Jun  5 10:17:36 taroona dbus[1035]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Jun  5 10:17:36 taroona dbus[1035]: [system] Successfully activated service 'com.ubuntu.SystemService'
Jun  5 10:17:37 taroona AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun  5 10:17:37 taroona dbus[1035]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun  5 10:17:37 taroona AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun  5 10:17:37 taroona AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/b9112cf788b04a92b264e482400e0369
Jun  5 10:17:37 taroona AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/b9112cf788b04a92b264e482400e0369
Jun  5 10:17:40 taroona AptDaemon.PackageKit: INFO: Get updates()
Jun  5 10:17:42 taroona AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/b9112cf788b04a92b264e482400e0369
Jun  5 10:18:04 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) starting connection 'Telstra_via_Gobi_2000'
Jun  5 10:18:04 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  5 10:18:04 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Jun  5 10:18:04 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Jun  5 10:18:04 taroona NetworkManager[1093]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Jun  5 10:18:14 taroona NetworkManager[1093]: <warn> GSM connection failed: (32) Sending command failed: 'Resource temporarily unavailable'
Jun  5 10:18:14 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Jun  5 10:18:14 taroona NetworkManager[1093]: <warn> Activation (ttyUSB1) failed.
Jun  5 10:18:14 taroona NetworkManager[1093]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun  5 10:18:14 taroona NetworkManager[1093]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
Jun  5 10:18:14 taroona NetworkManager[1093]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Jun  5 10:18:14 taroona NetworkManager[1093]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed

```

---

