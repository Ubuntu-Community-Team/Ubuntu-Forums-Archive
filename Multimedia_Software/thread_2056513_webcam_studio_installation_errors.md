---
title: "webcam studio installation errors"
date: 2012-09-11
forum: Multimedia Software
---

### Post by cybercity@localhost on 2012-09-11
I tried to start webcamstudio, but it's splash screen pop's up then  nothing. here is output of lsusb
```

Bus 007 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 007 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```also tried to re-install the software but installation fails with this error..
```

(Reading database ... 189076 files and directories currently installed.)
Preparing to replace webcamstudio 0.56 (using webcamstudio_0.56_all.deb) ...
Unpacking replacement webcamstudio ...
Setting up webcamstudio (0.56) ...
Removing the webcamstudio module from memory
ERROR: Module webcamstudio does not exist in /proc/modules
Removing webcamstudio.ko from the modules
rm: cannot remove `/lib/modules/2.6.38-15-generic/kernel/drivers/misc/webcamstudio.ko': No such file or directory
Restating the webcamstudio service to update the module
 * Stopping WebcamStudio kernel module webcamstudio                                                                                                   [ OK ] 
 * Starting WebcamStudio kernel module webcamstudio                                                                                                          make -C /lib/modules/2.6.38-15-generic/build SUBDIRS=/tmp/webcamstudio-src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-15-generic'
  CC [M]  /tmp/webcamstudio-src/webcamstudio.o
/tmp/webcamstudio-src/webcamstudio.c:191:2: error: #error "need CONFIG_VIDEO_V4L1_COMPAT"
/tmp/webcamstudio-src/webcamstudio.c:215:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/webcamstudio-src/webcamstudio.o] Error 1
make[1]: *** [_module_/tmp/webcamstudio-src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-15-generic'
make: *** [all] Error 2
install -d /lib/modules/2.6.38-15-generic/kernel/drivers/misc
install -m 644 -c webcamstudio.ko /lib/modules/2.6.38-15-generic/kernel/drivers/misc
install: cannot stat `webcamstudio.ko': No such file or directory
make: *** [install] Error 1

 * Modprobe webcamstudio failed. Please use 'dmesg' to find out why.

```i don't know how but software icon is shown in Sound and Video but when i click on it nothing happens.
here is output of /var/log/messages
```

Sep 11 23:05:28 cybercity kernel: [ 1855.568472] usb 1-4: USB disconnect, address 3
Sep 11 23:07:21 cybercity kernel: [ 1969.164030] usb 1-4: new high speed USB device using ehci_hcd and address 4
Sep 11 23:07:22 cybercity kernel: [ 1969.309518] uvcvideo: Found UVC 1.00 device Vimicro USB 2.0 PC Camera (Venus) (0ac8:3420)
**[COLOR=Red]Sep 11 23:07:22 cybercity kernel: [ 1969.309527] uvcvideo: No streaming interface found for terminal 3[/COLOR]**.
Sep 11 23:07:22 cybercity kernel: [ 1969.309624] input: Vimicro USB 2.0 PC Camera (Venu as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input8

```is the coloured portion an issue?

---

