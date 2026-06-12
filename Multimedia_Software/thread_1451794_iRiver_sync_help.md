---
title: "iRiver sync help"
date: 2010-04-11
forum: Multimedia Software
---

### Post by Requiem of Eternity on 2010-04-11
Hello all!

I'm having issues getting my iRiver Clix 2 [U20] to talk with my newly installed Ubuntu.  I'll warn you, while I am logical and learn fast, I literally just installed it 2 days ago which popped my Linux-cherry.  I.e. I'm very new to Linux, so bear with me.

Anyway, down to business.  I searched in the endless online database with leagues of information and was only able to glean that I needed to have its connection type as UMS[MSC]--done.  I connect it via USB and my player will charge, but they don't talk to each other.  Not so much as a whisper. :[

Player: iRiver U20 [Clix 2]

Hardware: HP Pavilion zv6000 laptop

Software: Ubuntu 9.10

My boyfriend has tinkered with Linux programs for a few years, but he's horrible at explaining and I want to figure it out myself so I can better experience the OS for itself.

any and all help is greatly appreciated--thanks!

---

### Post by Chronon on 2010-04-11
Does it get listed if you run lsusb?  (To run it open the Terminal program, type "lsusb" at the prompt and then press Enter.)

---

### Post by Requiem of Eternity on 2010-04-11
I tried that, and it just lists root hubs 1,2, and 3.

---

### Post by Chronon on 2010-04-11
Try running "dmesg" after plugging it in.  If the device is visible it should generate a message.  If not, then you should try to eliminate hardware factors like faulty cable, bad USB port, etc.

---

### Post by Requiem of Eternity on 2010-04-12
Well I hate to sound like so much of a n00b, but am I looking for the device name?  I found this:

```
)
[   55.730151]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   66.592009] wlan0: no IPv6 routers present
[   73.528634] Marking TSC unstable due to cpufreq changes
[   73.744036] Clocksource tsc unstable (delta = -109737232 ns)
[  772.216053] usb 1-3: new high speed USB device using ehci_hcd and address 2


```But that's it..

---

### Post by Chronon on 2010-04-13
Try waiting a bit longer and running dmesg again.  You should get a bit more activity than that.  Here's what I get if I wait for a bit and run dmesg after plugging in my UMS device (a Sansa Clip).
```
[540756.381184] usb 1-5: new high speed USB device using ehci_hcd and address 25
[540756.539105] usb 1-5: configuration #1 chosen from 1 choice
[540756.545745] scsi7 : SCSI emulation for USB Mass Storage devices
[540756.545876] usb-storage: device found at 25
[540756.545878] usb-storage: waiting for device to settle before scanning
[540761.548353] usb-storage: device scan complete
[540761.550434] scsi 7:0:0:0: Direct-Access     SanDisk  Sansa Clip 1GB   v01. PQ: 0 ANSI: 0
[540761.550939] sd 7:0:0:0: Attached scsi generic sg3 type 0
[540761.554663] sd 7:0:0:0: [sdc] 1986048 512-byte logical blocks: (1.01 GB/969 MiB)
[540761.556035] sd 7:0:0:0: [sdc] Write Protect is off
[540761.556039] sd 7:0:0:0: [sdc] Mode Sense: 04 00 00 00
[540761.556042] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[540761.560573] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[540761.560578]  sdc:
[540761.574150] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[540761.574157] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```

The [sdc] bit tells me that it has been linked to the device node /dev/sdc.

---

### Post by Requiem of Eternity on 2010-04-13
Ok, well, it seems s though I have a few faulty cables. :oops:  Ijust asked to borrow a friend's and connected my device through it and all works.  I feel idiotic now.  I'm going to follow through with the command anyway to learn some more about command line though.

Got it!
```
[ 1724.092060] usb 2-2: new full speed USB device using ohci_hcd and address 2
[ 1724.290185] usb 2-2: not running at top speed; connect to a high speed hub
[ 1724.302330] usb 2-2: configuration #1 chosen from 1 choice
[ 1724.565384] Initializing USB Mass Storage driver...
[ 1724.567015] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1724.567307] usbcore: registered new interface driver usb-storage
[ 1724.567313] USB Mass Storage support registered.
[ 1724.569029] usb-storage: device found at 2
[ 1724.569033] usb-storage: waiting for device to settle before scanning
[ 1729.569083] usb-storage: device scan complete
[ 1729.576759] scsi 2:0:0:0: Direct-Access     iriver   clix                  PQ: 0 ANSI: 0
[ 1729.577662] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1729.593381] sd 2:0:0:0: [sdb] 7815168 512-byte logical blocks: (4.00 GB/3.72 GiB)
[ 1729.599088] sd 2:0:0:0: [sdb] Write Protect is off
[ 1729.599098] sd 2:0:0:0: [sdb] Mode Sense: 37 00 00 08
[ 1729.599103] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1729.629043] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1729.629053]  sdb:
[ 1729.760323] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1729.760334] sd 2:0:0:0: [sdb] Attached SCSI removable disk

```

Thank you again Chronon, you've been most helpful. :]


[SIZE=1][COLOR=Gray](Note to self: do more thorough testing before asking)[/COLOR][/SIZE]

---

### Post by Chronon on 2010-04-13
I kind of had a suspicion it might be a hardware issue.  I have had quite a few run-ins with flaky cables in my time.  :)

---

