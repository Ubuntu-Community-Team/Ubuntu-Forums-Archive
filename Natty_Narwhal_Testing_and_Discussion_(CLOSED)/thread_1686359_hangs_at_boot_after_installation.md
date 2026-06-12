---
title: "hangs at boot after installation"
date: 2011-02-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by biggerben on 2011-02-12
I tried out natty today. After the installation, I installed nvidia-xconfig and nvidia-settings and rebooted.

Booting without option "splash quiet" looked like this (copying from photo I took, so not quite verbatim):

```

 * Stopping anac(h)ronistic cron
[16.6] usb 1-5 device descriptor read/64, error -110
[31.8] usb 1-5 device descriptor read/64, error -110
[47.7] usb 1-5 device descriptor read/64, error -110
[62.4] usb 1-5 device descriptor read/64, error -110
[73.0] usb 1-5 device not accepting address 4, error -110
[83.6] usb 1-5 device not accepting address 5, error -110
[83.6] hub1-0:1.0: unable to enumerate USB device on port 5
[85.2] sd 6:0:0:0: [sdc] Asking for cache data dfailed
[85.2] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[85.2] sd 6:0:0:0: [sdc] Asking for cache data dfailed
[85.2] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[85.2] sd 6:0:0:0: [sdc] Asking for cache data dfailed
[85.2] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[99.6] usb 5-1: device descriptor read/64, error -110
[114.] usb 5-1: device descriptor read/64, error -110
[130.] usb 5-1: device descriptor read/64, error -110
[145.] usb 5-1: device descriptor read/64, error -110
[156.] usb 5-1: device not accepting address 4, error -110
[166.] usb 5-1: device not accepting address 5, error -110
[166.] hub 5-0:1.0: unable to enumerate USB devices on port 1

```

and after that nothing, even after waiting a couple of minutes.

A few thoughts: I have a built in cardreader which worked fine in 10.04 caused problems (with similar error messages in 10.10). Also, both in 10.10 and (the one time I could start 11.04) it took ages for the mouse to start working with similar messages appearing in dmesg (see second 166):

(kubuntu 10.10)
```

# dmesg
(...)
[   31.530012] usb 1-5: device descriptor read/64, error -110
[   31.761249] usb 1-5: new high speed USB device using ehci_hcd and address 3
[   32.193081] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   32.410275] EXT4-fs (sda4): re-mounted. Opts: commit=0
[   39.760006] eth1: no IPv6 routers present
[   43.710733] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   43.987337] EXT4-fs (sda4): re-mounted. Opts: commit=0
[   46.881276] usb 1-5: device descriptor read/64, error -110
[   62.121255] usb 1-5: device descriptor read/64, error -110
[   62.361274] usb 1-5: new high speed USB device using ehci_hcd and address 4
[   71.145106] lo: Disabled Privacy Extensions
[   72.777900] usb 1-5: device not accepting address 4, error -110
[   72.890018] usb 1-5: new high speed USB device using ehci_hcd and address 5
[   83.321262] usb 1-5: device not accepting address 5, error -110
[   83.321279] hub 1-0:1.0: unable to enumerate USB device on port 5
[   83.661271] usb 2-4: new high speed USB device using ehci_hcd and address 4
[   83.895621] Initializing USB Mass Storage driver...
[   83.895842] scsi6 : usb-storage 2-4:1.0
[   83.895983] usbcore: registered new interface driver usb-storage
[   83.895985] USB Mass Storage support registered.
[   84.230023] usb 5-1: new full speed USB device using uhci_hcd and address 2
[   84.935226] scsi 6:0:0:0: Direct-Access     ST364032 3AS                   PQ: 0 ANSI: 2 CCS
[   84.935799] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   84.936321] sd 6:0:0:0: [sdc] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[   84.937065] sd 6:0:0:0: [sdc] Write Protect is off
[   84.937067] sd 6:0:0:0: [sdc] Mode Sense: 00 38 00 00
[   84.937070] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   84.939944] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   84.939951]  sdc: sdc1 sdc2
[   84.942684] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   84.942689] sd 6:0:0:0: [sdc] Attached SCSI disk
[   99.360015] usb 5-1: device descriptor read/64, error -110
[  114.591267] usb 5-1: device descriptor read/64, error -110
[  114.821266] usb 5-1: new full speed USB device using uhci_hcd and address 3
[  129.940024] usb 5-1: device descriptor read/64, error -110
[  145.180014] usb 5-1: device descriptor read/64, error -110
[  145.420009] usb 5-1: new full speed USB device using uhci_hcd and address 4
[  155.850011] usb 5-1: device not accepting address 4, error -110
[  155.970016] usb 5-1: new full speed USB device using uhci_hcd and address 5
[  166.404300] usb 5-1: device not accepting address 5, error -110
[  166.404317] hub 5-0:1.0: unable to enumerate USB device on port 1
[  166.681262] usb 6-1: new low speed USB device using uhci_hcd and address 2
[  166.905554] usbcore: registered new interface driver hiddev
[  166.919175] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input3
[  166.919293] generic-usb 0003:046D:C043.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1/input0
[  166.919315] usbcore: registered new interface driver usbhid
[  166.919317] usbhid: USB HID core driver
[  167.150013] usb 7-1: new full speed USB device using uhci_hcd and address 2
[  167.312026] hub 7-1:1.0: USB hub found
[  167.313987] hub 7-1:1.0: 4 ports detected
[  167.600016] usb 8-1: new full speed USB device using uhci_hcd and address 2
[  167.825970] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1204
[  167.825994] usbcore: registered new interface driver usblp
[  169.011389] usb 8-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  350.990024] usb 5-1: new full speed USB device using uhci_hcd and address 6
[  366.111267] usb 5-1: device descriptor read/64, error -110
[  381.340017] usb 5-1: device descriptor read/64, error -110
[  381.571272] usb 5-1: new full speed USB device using uhci_hcd and address 7
[  396.750019] usb 5-1: device descriptor read/64, error -110
[  411.980016] usb 5-1: device descriptor read/64, error -110
[  412.210017] usb 5-1: new full speed USB device using uhci_hcd and address 8
[  422.630011] usb 5-1: device not accepting address 8, error -110
[  422.751269] usb 5-1: new full speed USB device using uhci_hcd and address 9
[  433.171262] usb 5-1: device not accepting address 9, error -110
[  433.171277] hub 5-0:1.0: unable to enumerate USB device on port 1
[ 2049.491284] usb 5-1: new full speed USB device using uhci_hcd and address 10
[ 2064.611264] usb 5-1: device descriptor read/64, error -110
[ 2079.841268] usb 5-1: device descriptor read/64, error -110
[ 2080.070011] usb 5-1: new full speed USB device using uhci_hcd and address 11
[ 2095.260893] usb 5-1: device descriptor read/64, error -110
[ 2110.491264] usb 5-1: device descriptor read/64, error -110
[ 2110.721265] usb 5-1: new full speed USB device using uhci_hcd and address 12
[ 2121.141267] usb 5-1: device not accepting address 12, error -110
[ 2121.260015] usb 5-1: new full speed USB device using uhci_hcd and address 13
[ 2131.680018] usb 5-1: device not accepting address 13, error -110
[ 2131.680035] hub 5-0:1.0: unable to enumerate USB device on port 1

```

Looks like this could have something to do with it.

Should I file a bug (if so, how?), else any help on how to get this working would be greatly appreciated!

-Ben

---

### Post by biggerben on 2011-02-12
also, can anyone tell me how to file this in launchpad?

---

### Post by dino99 on 2011-02-12
you should make a clean install from scratch. Are you booting with an usb stick plugged ? Check usb bios settings.

---

### Post by biggerben on 2011-02-13
Maybe I'll try with a clean install with the next beta. But for now: how do I file this bug in launchpad?

---

