---
title: "Support for 'AVEO_Technology_Corp._USB2.0_Camera' ?"
date: 2011-12-18
forum: Multimedia Software
---

### Post by LianerGoist on 2011-12-18
I got a usb-microscope, and when I connect it to my computer (Ubuntu 11.10), the following is written in syslog - I have inserted the commands that are called. 

As you can see, Ubuntu can't find the module to load, and try to run the command '/sbin/modprobe -bv usb:v1871p0516d0307dcEFdsc02dp01ic0Eisc02ip00'. There is a chance it will work with the module 'uvcvideo.ko', but how can I tell Ubuntu to use that module? Thanks...

```
kernel: [ 1486.944217] usb 2-5: new high speed USB device number 4 using ehci_hcd
udevd[307]: seq 1977 queued, 'add' 'usb'
udevd[307]: passed 257 bytes to netlink monitor 0x215c21f8
udevd[503]: seq 1977 running
udevd[503]: device 0x215c5078 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-5'
udevd[503]: no db file to read /run/udev/data/c189:131: No such file or directory
udevd[503]: PROGRAM 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5 2 4' /lib/udev/rules.d/39-libmtp.rules:735

* Line 735: ENV{ID_MTP_DEVICE}!="1", ATTR{bDeviceClass}=="00|02|06|ef|ff", PROGRAM="mtp-probe /sys$env{DEVPATH} $attr{busnum} $attr{devnum}", RESULT=="1", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1" *

udevd[307]: seq 1978 queued, 'add' 'usb'
udevd[307]: seq 1979 queued, 'add' 'usb'
udevd[3755]: starting 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5 2 4'
mtp-probe: checking bus 2, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5"
mtp-probe: bus: 2, device: 4 was not an MTP device
udevd[503]: 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5 2 4'(out) '0'
udevd[503]: 'mtp-probe /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-5 2 4' [3755] exit with return code 0

* Okay, /lib/udev/rules.d/39-libmtp.rules:735 done. *

udevd[503]: device 0x215c5200 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2'
udevd[503]: device 0x215c3200 has devpath '/devices/pci0000:00/0000:00:1d.7'
udevd[503]: device 0x215c4bf0 has devpath '/devices/pci0000:00'
udevd[503]: IMPORT 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5' /lib/udev/rules.d/40-libgphoto2-2.rules:11

*  Line 11: ENV{ID_USB_INTERFACES}=="", IMPORT{program}="usb_id --export %p" *

udevd[3756]: starting 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'
usb_id[3756]: custom logging function 0x22cb0008 registered
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_VENDOR=AVEO_Technology_Corp.'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_VENDOR_ENC=AVEO\x20Technology\x20Corp.'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_VENDOR_ID=1871'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_MODEL=USB2.0_Camera'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_MODEL_ENC=USB2.0\x20Camera'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_MODEL_ID=0516'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_REVISION=0307'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_SERIAL=AVEO_Technology_Corp._USB2.0_Camera'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_BUS=usb'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5'(out) 'ID_USB_INTERFACES=:ff0100:0e0200:'
udevd[503]: 'usb_id --export /devices/pci0000:00/0000:00:1d.7/usb2/2-5' [3756] exit with return code 0
udevd[503]: MODE 0664 /lib/udev/rules.d/50-udev-default.rules:55

* Line 55: SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664" *

udevd[503]: no node name set, will use kernel supplied name 'bus/usb/002/004'
udevd[503]: creating device node '/dev/bus/usb/002/004', devnum=189:131, mode=0664, uid=0, gid=0
udevd[503]: preserve file '/dev/bus/usb/002/004', because it has correct dev_t
udevd[503]: set permissions /dev/bus/usb/002/004, 020664, uid=0, gid=0
udevd[503]: creating symlink '/dev/char/189:131' to '../bus/usb/002/004'
udevd[503]: created db file '/run/udev/data/c189:131' for '/devices/pci0000:00/0000:00:1d.7/usb2/2-5'
udevd[503]: passed -1 bytes to netlink monitor 0x215c9708
udevd[503]: seq 1977 processed with 0
udevd[307]: seq 1977 done with 0
udevd[307]: passed 275 bytes to netlink monitor 0x215c21f8
udevd[504]: seq 1979 running
udevd[503]: seq 1978 running
udevd[503]: device 0x215c3c00 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0'
udevd[504]: device 0x215c21f8 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.1'
udevd[503]: no db file to read /run/udev/data/+usb:2-5:1.0: No such file or directory
udevd[504]: no db file to read /run/udev/data/+usb:2-5:1.1: No such file or directory
udevd[503]: device 0x215c4f58 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-5'
udevd[504]: device 0x215c26b0 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2/2-5'
udevd[503]: device 0x215c3d38 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2'
udevd[503]: device 0x215c3eb0 has devpath '/devices/pci0000:00/0000:00:1d.7'
udevd[504]: device 0x215c2990 has devpath '/devices/pci0000:00/0000:00:1d.7/usb2'
udevd[503]: device 0x215c35a0 has devpath '/devices/pci0000:00'
udevd[504]: device 0x215c2b28 has devpath '/devices/pci0000:00/0000:00:1d.7'
udevd[504]: device 0x215c2cf8 has devpath '/devices/pci0000:00'
udevd[307]: passed 274 bytes to netlink monitor 0x215c21f8
udevd[503]: RUN 'usb_modeswitch --driver-bind %p %s{idVendor} %s{idProduct} %E{PRODUCT}' /lib/udev/rules.d/40-usb_modeswitch.rules:17

* Line 17: ATTR{bInterfaceClass}=="ff", ATTR{bInterfaceNumber}=="00", ATTRS{bNumConfigurations}=="*", RUN+="usb_modeswitch --driver-bind %p %s{idVendor} %s{idProduct} %E{PRODUCT}" *

udevd[503]: RUN '/sbin/modprobe -bv $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5
udevd[504]: RUN '/sbin/modprobe -bv $env{MODALIAS}' /lib/udev/rules.d/80-drivers.rules:5

* Line 5: DRIVER!="?*", ENV{MODALIAS}=="?*", RUN+="/sbin/modprobe -bv $env{MODALIAS}" *

udevd[3757]: starting 'usb_modeswitch --driver-bind /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0   1871/516/307'
udevd[3758]: starting '/sbin/modprobe -bv usb:v1871p0516d0307dcEFdsc02dp01ic0Eisc02ip00'
udevd[504]: '/sbin/modprobe -bv usb:v1871p0516d0307dcEFdsc02dp01ic0Eisc02ip00'(err) 'FATAL: Module usb:v1871p0516d0307dcEFdsc02dp01ic0Eisc02ip00 not found.'
udevd[504]: '/sbin/modprobe -bv usb:v1871p0516d0307dcEFdsc02dp01ic0Eisc02ip00' [3758] exit with return code 1
udevd[504]: passed -1 bytes to netlink monitor 0x215c9140
udevd[504]: seq 1979 processed with 0
udevd[307]: seq 1979 done with 0
udevd[503]: 'usb_modeswitch --driver-bind /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0   1871/516/307' [3757] exit with return code 0
udevd[3764]: starting '/sbin/modprobe -bv usb:v1871p0516d0307dcEFdsc02dp01icFFisc01ip00'
udevd[503]: '/sbin/modprobe -bv usb:v1871p0516d0307dcEFdsc02dp01icFFisc01ip00'(err) 'FATAL: Module usb:v1871p0516d0307dcEFdsc02dp01icFFisc01ip00 not found.'
udevd[503]: '/sbin/modprobe -bv usb:v1871p0516d0307dcEFdsc02dp01icFFisc01ip00' [3764] exit with return code 1
udevd[503]: passed -1 bytes to netlink monitor 0x215c9708
udevd[503]: seq 1978 processed with 0
udevd[307]: seq 1978 done with 0
```

---

