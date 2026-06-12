---
title: "mp3 player not working"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by yourearthlymaster on 2006-12-11
ok, my Samsung YP-U2J mp3 player is not mounting and I didn't find the other thread on this prob of any help.  
this is what I get when I enter:  dmesg | grep usb
[17179575.576000] usbcore: registered new driver usbfs
[17179575.576000] usbcore: registered new driver hub
[17179575.980000] usb usb1: configuration #1 chosen from 1 choice
[17179576.084000] usb usb2: configuration #1 chosen from 1 choice
[17179576.628000] usb usb3: configuration #1 chosen from 1 choice
[17179647.948000] usb 3-2: new full speed USB device using ohci_hcd and address 2
[17179648.144000] usb 3-2: not running at top speed; connect to a high speed hub
[17179648.156000] usb 3-2: configuration #1 chosen from 1 choice
[17179648.376000] usbcore: registered new driver libusual
[17179648.464000] usb-storage: device found at 2
[17179648.464000] usb-storage: waiting for device to settle before scanning
[17179648.464000] usbcore: registered new driver usb-storage
[17179653.464000] usb-storage: device scan complete
[17179653.692000] usb 3-2: USB disconnect, address 2
[17179830.940000] usb 3-2: new full speed USB device using ohci_hcd and address 3
[17179831.136000] usb 3-2: not running at top speed; connect to a high speed hub
[17179831.148000] usb 3-2: configuration #1 chosen from 1 choice
[17179831.152000] usb-storage: device found at 3
[17179831.152000] usb-storage: waiting for device to settle before scanning
[17179836.152000] usb-storage: device scan complete
[17179836.380000] usb 3-2: USB disconnect, address 3


thanx in advance.

---

### Post by yourearthlymaster on 2006-12-11
any help you could give, even a pointer towards the right direction, would be nice.

---

### Post by praxis22 on 2006-12-12
Is there an option on the player to make it look like a drive? I know many cameras have this.

---

### Post by tauko on 2006-12-12
Mp3 players and usbdrivers usually are in /dev/sdx. 

Try with```
dmesg | grep sd
```

My example:```
~$ dmesg | grep sd
[17179598.592000] SCSI device sda: 585938944 512-byte hdwr sectors (300001 MB)
[17179598.796000] sda: Write Protect is off
[17179598.796000] sda: Mode Sense: 1c 00 00 00
[17179598.796000] sda: assuming drive cache: write through
[17179598.800000] SCSI device sda: 585938944 512-byte hdwr sectors (300001 MB)
[17179599.008000] sda: Write Protect is off
[17179599.008000] sda: Mode Sense: 1c 00 00 00
[17179599.008000] sda: assuming drive cache: write through
[17179599.008000]  sda: sda1
[17179599.040000] sd 0:0:0:0: Attached scsi disk sda
[17179599.072000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179609.756000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179647.888000] EXT3 FS on sda1, internal journal

```
As you can see, I've a usb conected hard drive. It's partition it's ext3 and its location is on /dev/sda.

What I can't tell you right now is how to mount it...

If you can, please post more info!

---

### Post by yourearthlymaster on 2006-12-13
Sorry about taking so long to get back to you, something came up...

anyway.  here is what I found when I typed:  dmesg|grep sd

thats right, nothing.  
I tried a Lexar JumpDrive to see if it worked and it did, automount and all.  
but still dont see whats wrong with my mp3 player.  
and lsusb returns this:  
:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

also my dmesg has changed since i disconnected all other connections:  

:~$ dmesg|grep usb
[17179573.340000] usbcore: registered new driver usbfs
[17179573.340000] usbcore: registered new driver hub
[17179573.728000] usb usb1: configuration #1 chosen from 1 choice
[17179574.216000] usb usb2: configuration #1 chosen from 1 choice
[17179574.320000] usb usb3: configuration #1 chosen from 1 choice
[17179700.160000] usb 3-3: new high speed USB device using ehci_hcd and address 2
[17179700.292000] usb 3-3: configuration #1 chosen from 1 choice
[17179700.524000] usbcore: registered new driver libusual
[17179700.612000] usb-storage: device found at 2
[17179700.612000] usb-storage: waiting for device to settle before scanning
[17179700.612000] usbcore: registered new driver usb-storage
[17179705.612000] usb-storage: device scan complete
[17179705.836000] usb 3-3: USB disconnect, address 2

---

