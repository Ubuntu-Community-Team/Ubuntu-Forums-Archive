---
title: "ipod suddenly stopped mounting"
date: 2010-09-13
forum: Multimedia Software
---

### Post by BarryDocks on 2010-09-13
I have a 30GB ipod classic and have been happily using banshee to manage it.  Today I plugged it in and it won't mount, just seems to sit there reseting itself.  Unplug it an the ipod works fine.  

Help - I have no idea what is going on.  A reboot has made no difference.

Here's the entry from syslog: 
```
Sep 13 17:05:37 adrian-laptop kernel: [  410.131186] usb 2-3: new high speed USB device using ehci_hcd and address 3
Sep 13 17:05:37 adrian-laptop kernel: [  410.249140] usb 2-3: configuration #1 chosen from 2 choices
Sep 13 17:05:37 adrian-laptop kernel: [  410.249777] scsi6 : SCSI emulation for USB Mass Storage devices
Sep 13 17:05:37 adrian-laptop kernel: [  410.250694] usb-storage: device found at 3
Sep 13 17:05:37 adrian-laptop kernel: [  410.250700] usb-storage: waiting for device to settle before scanning
Sep 13 17:05:42 adrian-laptop kernel: [  415.250686] usb-storage: device scan complete
Sep 13 17:05:42 adrian-laptop kernel: [  415.251768] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Sep 13 17:05:42 adrian-laptop kernel: [  415.253986] sd 6:0:0:0: Attached scsi generic sg2 type 0
Sep 13 17:05:42 adrian-laptop kernel: [  415.258249] sd 6:0:0:0: [sdb] 58605120 512-byte logical blocks: (30.0 GB/27.9 GiB)
Sep 13 17:05:42 adrian-laptop kernel: [  415.259817] sd 6:0:0:0: [sdb] Write Protect is off
Sep 13 17:05:42 adrian-laptop kernel: [  415.259828] sd 6:0:0:0: [sdb] Mode Sense: 68 00 00 08
Sep 13 17:05:42 adrian-laptop kernel: [  415.259835] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 13 17:05:42 adrian-laptop kernel: [  415.264332] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 13 17:05:42 adrian-laptop kernel: [  415.264343]  sdb: sdb1 sdb2
Sep 13 17:05:42 adrian-laptop kernel: [  415.284798] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Sep 13 17:05:42 adrian-laptop kernel: [  415.284803] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Sep 13 17:06:12 adrian-laptop kernel: [  445.803215] usb 2-3: reset high speed USB device using ehci_hcd and address 3
Sep 13 17:06:43 adrian-laptop kernel: [  476.806231] usb 2-3: reset high speed USB device using ehci_hcd and address 3
Sep 13 17:07:15 adrian-laptop kernel: [  508.806092] usb 2-3: reset high speed USB device using ehci_hcd and address 3
Sep 13 17:07:47 adrian-laptop kernel: [  540.806173] usb 2-3: reset high speed USB device using ehci_hcd and address 3
Sep 13 17:08:19 adrian-laptop kernel: [  572.806216] usb 2-3: reset high speed USB device using ehci_hcd and address 3
Sep 13 17:08:51 adrian-laptop kernel: [  604.806202] usb 2-3: reset high speed USB device using ehci_hcd and address 3
```

Results from lsusb:
```
:~# lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:1209 Apple, Inc. iPod Video
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

results from relevant section of lshw:
```
*-scsi
          physical id: 0
          bus info: usb@2:3
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: iPod
             vendor: Apple
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.62
             serial: 2Z6020YQSZ92
             size: 27GiB (30GB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 27GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=20202020
              *-volume:0
                   description: Empty partition
                   physical id: 1
                   logical name: /dev/sdb1
                   capacity: 78MiB
                   capabilities: primary nofs
              *-volume:1
                   description: Windows FAT volume
                   vendor: *UOKJIHC
                   physical id: 2
                   logical name: /dev/sdb2
                   version: FAT32
                   serial: c57c-7d5e
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat label=IPOD

```

---

