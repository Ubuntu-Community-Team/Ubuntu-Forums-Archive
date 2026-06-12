---
title: "Prof 1100 DVB-S USB adapter"
date: 2009-09-30
forum: Multimedia Software
---

### Post by duckmonkey on 2009-09-30
So I bought this "Prof 1100 USB DVB-S" adapter on the basis that it came with linux drivers and their website seems to give the impression that they at least semi-support Linux:

[http://www.prof-tuners.com/eng/prof1100.html](http://www.prof-tuners.com/eng/prof1100.html)

Plugging it in yields the result:

```
[  892.232180] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  892.368087] usb 2-2: configuration #1 chosen from 1 choice
```and no /dev/dvb/adapter0

which i kind of expected, since they supply their own driver source:

_[[U]http://www.prof-tuners.com/download/linux/Prof_linux_driver.zip_]("http://www.prof-tuners.com/download/linux/Prof_linux_driver.zip")[/U]

However I can't get it to compile with 9.04:

```
gjm@m1330:~/Desktop/Prof_linux_driver$ make
make -C /home/gjm/Desktop/Prof_linux_driver/v4l 
make[1]: Entering directory `/home/gjm/Desktop/Prof_linux_driver/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.24-19-generic/build
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/gjm/Desktop/Prof_linux_driver/v4l  modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.24-19-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gjm/Desktop/Prof_linux_driver/v4l'
make: *** [all] Error 2

```Changing the .version file so it matches the running kernel improves things and I can see some modules being built but then:

```

.....
  CC [M]  /home/gjm/Desktop/Prof_linux_driver/v4l/af9005-fe.o
  CC [M]  /home/gjm/Desktop/Prof_linux_driver/v4l/au6610.o
  CC [M]  /home/gjm/Desktop/Prof_linux_driver/v4l/cxusb.o
/home/gjm/Desktop/Prof_linux_driver/v4l/cxusb.c: In function 'bluebird_patch_dvico_firmware_download':
/home/gjm/Desktop/Prof_linux_driver/v4l/cxusb.c:702: error: assignment of read-only location '*(fw->data + ((unsigned int)idoff + 2u))'
/home/gjm/Desktop/Prof_linux_driver/v4l/cxusb.c:704: error: assignment of read-only location '*(fw->data + ((unsigned int)idoff + 3u))'
make[2]: *** [/home/gjm/Desktop/Prof_linux_driver/v4l/cxusb.o] Error 1
make[1]: *** [_module_/home/gjm/Desktop/Prof_linux_driver/v4l] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
```lsusb:

```
Bus 002 Device 004: ID 3011:b012  
Bus 002 Device 003: ID 05a9:7670 OmniVision Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```where the 1st line is the 'Prof'.

Any ideas?  I thought I was being clever by making the effort to buy from someone who said it worked with Linux!

---

