---
title: "New 1gb Ipod Shuffle working on Edgy"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by rcatman on 2006-11-07
I bought a new 1GB Ipod Shuffle today and was very eager to test out Ubuntu's capability to communicate with an Ipod. This was a true test of Ubuntu fulfilling my demands. I plugged in the dock, then plugged in the ipod to the dock and voila! Rhythmbox popped right up with the name of my ipod and a listing of the musics I had loaded previously after setting it up on my Mac G5.

Reading around I found that the best(if not only) way to set up the ipod is on a windows or mac. Gagging over the thought of using windows, I gladly ran to my Mac and, after installing iTunes 7.0.2, setting up the shuffle took a minute. At the [iPod shuffle Database Builder]("http://shuffle-db.sourceforge.net/") it mentioned to Enable Disk Use. I enabled disk use with the bar all the way to the right for maximum song storage. 

I searched synaptic for the term 'ipod' and examined the results. I had libgpod0 installed. Rhythmbox claimed to support ipod connectivity. So why not, I plugged in my ipod. Rhythmbox popped up and here is what my dmesg says...
```
[17191766.588000] usb 2-3: new full speed USB device using ohci_hcd and address 4
[17191766.808000] usb 2-3: configuration #1 chosen from 2 choices
[17191767.712000] usbcore: registered new driver libusual
[17191768.020000] SCSI subsystem initialized
[17191768.028000] Initializing USB Mass Storage driver...
[17191768.032000] scsi0 : SCSI emulation for USB Mass Storage devices
[17191768.032000] usb-storage: device found at 4
[17191768.032000] usb-storage: waiting for device to settle before scanning
[17191768.032000] usbcore: registered new driver usb-storage
[17191768.032000] USB Mass Storage support registered.
[17191773.032000] usb-storage: device scan complete
[17191773.040000]   Vendor: Apple     Model: iPod              Rev: 2.70
[17191773.040000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17191773.228000] SCSI device sda: 495616 2048-byte hdwr sectors (1015 MB)
[17191773.236000] sda: Write Protect is off
[17191773.236000] sda: Mode Sense: 64 00 00 08
[17191773.236000] sda: assuming drive cache: write through
[17191773.256000] SCSI device sda: 495616 2048-byte hdwr sectors (1015 MB)
[17191773.264000] sda: Write Protect is off
[17191773.264000] sda: Mode Sense: 64 00 00 08
[17191773.264000] sda: assuming drive cache: write through
[17191773.264000]  sda: unknown partition table
[17191773.304000] sd 0:0:0:0: Attached scsi removable disk sda
[17191773.344000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17191774.776000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```


I dragged a song from my library onto my iPod playlist and everything went well! Ubuntu is by far the best choice I could've ever made! It just worked! What can I say 8)

---

