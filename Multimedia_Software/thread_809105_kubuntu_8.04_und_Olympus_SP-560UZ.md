---
title: "kubuntu 8.04 und Olympus SP-560UZ"
date: 2008-05-27
forum: Multimedia Software
---

### Post by hutzelfix on 2008-05-27
hi all,

being unable to get inmages from my brandnew camera I decided to ask you :)

Camera works on debian sarge and etch, can be mounted from /dev/sda1 or /dev/sdb1.
But not on kubuntu 8.04 :(
USB Stick Kingston is working, old camera (Olympus 720UZ) is working too.

camera is seen by lsusb, but slightly wrong: Model is not correct:
Bus 008 Device 002: ID 07b4:0109 Olympus Optical Co., Ltd C-370Z/D-535Z/X-450
in syslog there is no hint which device could be the camera:

> May 27 10:45:35 majestix kernel: [ 2568.554001] usb 8-1: new high speed USB device using ehci_hcd and address 2
May 27 10:45:35 majestix kernel: [ 2568.878843] usb 8-1: configuration #1 chosen from 1 choice
May 27 10:45:35 majestix NetworkManager: <debug> [1211877935.976147] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7b4_109_000L77549957').
May 27 10:45:36 majestix kernel: [ 2569.251533] usbcore: registered new interface driver libusual
May 27 10:45:36 majestix kernel: [ 2569.277785] Initializing USB Mass Storage driver...
May 27 10:45:36 majestix kernel: [ 2569.279066] scsi7 : SCSI emulation for USB Mass Storage devices
May 27 10:45:36 majestix kernel: [ 2569.280356] usbcore: registered new interface driver usb-storage
May 27 10:45:36 majestix kernel: [ 2569.280361] USB Mass Storage support registered.
May 27 10:45:36 majestix kernel: [ 2569.281201] usb-storage: device found at 2
May 27 10:45:36 majestix kernel: [ 2569.281204] usb-storage: waiting for device to settle before scanning
May 27 10:45:36 majestix NetworkManager: <debug> [1211877936.375346] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7b4_109_000L77549957_if0').

the old camera _is_ mounted, as shown in syslog:
> May 27 10:55:50 majestix kernel: [ 3183.098346] usb 4-2: new full speed USB device using uhci_hcd and address 2
May 27 10:55:50 majestix kernel: [ 3183.339345] usb 4-2: configuration #1 chosen from 1 choice
May 27 10:55:50 majestix NetworkManager: <debug> [1211878550.780182] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7b4_102_108433109').
May 27 10:55:50 majestix kernel: [ 3183.344319] scsi8 : SCSI emulation for USB Mass Storage devices
May 27 10:55:50 majestix kernel: [ 3183.344942] usb-storage: device found at 2
May 27 10:55:50 majestix kernel: [ 3183.344945] usb-storage: waiting for device to settle before scanning
May 27 10:55:50 majestix NetworkManager: <debug> [1211878550.856172] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7b4_102_108433109_if0').
May 27 10:55:55 majestix kernel: [ 3188.341600] usb-storage: device scan complete
May 27 10:55:55 majestix kernel: [ 3188.351601] scsi 8:0:0:0: Direct-Access     OLYMPUS  C720UZ           1034 PQ: 0 ANSI: 2
May 27 10:55:55 majestix kernel: [ 3188.397556] sd 8:0:0:0: [sdb] 256000 512-byte hardware sectors (131 MB)
May 27 10:55:55 majestix kernel: [ 3188.414827] sd 8:0:0:0: [sdb] Write Protect is off
May 27 10:55:55 majestix kernel: [ 3188.414832] sd 8:0:0:0: [sdb] Mode Sense: 17 00 00 08
May 27 10:55:55 majestix kernel: [ 3188.414834] sd 8:0:0:0: [sdb] Assuming drive cache: write through
May 27 10:55:55 majestix NetworkManager: <debug> [1211878555.855507] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7b4_102_108433109_if0_scsi_host').
May 27 10:55:55 majestix NetworkManager: <debug> [1211878555.857575] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_7b4_102_108433109_if0_scsi_host_scsi_device_lun0').
May 27 10:55:55 majestix kernel: [ 3188.465524] sd 8:0:0:0: [sdb] 256000 512-byte hardware sectors (131 MB)
May 27 10:55:55 majestix kernel: [ 3188.482504] sd 8:0:0:0: [sdb] Write Protect is off
May 27 10:55:55 majestix kernel: [ 3188.482508] sd 8:0:0:0: [sdb] Mode Sense: 17 00 00 08
May 27 10:55:55 majestix kernel: [ 3188.482510] sd 8:0:0:0: [sdb] Assuming drive cache: write through
May 27 10:55:55 majestix kernel: [ 3188.482514]  sdb: sdb1

so, something is missing . but what?

tia

---

### Post by hutzelfix on 2008-05-28
I set the debug-level in /etc/udev/udev.conf to 'debug'

here is the result:
[http://www.hutzelfix.de/test/udev_log_verbose.txt](http://www.hutzelfix.de/test/udev_log_verbose.txt)

first at 18:00:yy the failure of the SP-560UZ

then at 18:05:yy the successful C-720UZ

may be this helps?:confused:


<edit>
just got a hint to stop hal before testing - and it works!

have to 'mount /dev/sdb1/ /mnt/usbcam' but it works.

---

### Post by maxcelpc on 2008-05-28
Thank you hutzelfix.

I had a similar problem with Hardy not recognising a SmartDisk FlashTrax XT, so I tried:

mount -t vfat /dev/sdb1/ /media/smartdisk and it works!

---

### Post by hutzelfix on 2008-05-28
the problem is that no /dev/sdXX device is there that could be mounted.

only if I stop hal by issuing '/etc/init.d/hal stop' before connecting the camera there is a /dev/sdb1 device which I than can mount to /mnt/usb or whatever.

So the problem still is there](*,) . it is just a workaround](*,)

thx anyway :popcorn:

---

