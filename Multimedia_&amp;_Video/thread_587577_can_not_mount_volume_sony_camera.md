---
title: "can not mount volume sony camera"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by vbdanl on 2007-10-22
Hi. I used to be able to download pictures from my sony camera via ubuntu, but since recently installing the upgrade to 7.10, it now does not work.  I get the error message: Can not mount volume, unable to mount the volume.  here is what is in syslog:
[ 3163.261615] Initializing USB Mass Storage driver...
[ 3163.261779] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3163.261929] usbcore: registered new interface driver usb-storage
[ 3163.261935] USB Mass Storage support registered.
[ 3163.262213] usb-storage: device found at 2
[ 3163.262218] usb-storage: waiting for device to settle before scanning
[ 3168.250493] usb-storage: device scan complete
[ 3168.253116] scsi 2:0:0:0: Direct-Access     Sony     Sony DSC         4.50 PQ: 0 ANSI: 0 CCS
[ 3168.293948] SCSI device sda: 466944 512-byte hdwr sectors (239 MB)
[ 3168.293958] sda: assuming Write Enabled
[ 3168.293960] sda: assuming drive cache: write through
[ 3168.302924] SCSI device sda: 466944 512-byte hdwr sectors (239 MB)
[ 3168.302933] sda: assuming Write Enabled
[ 3168.302936] sda: assuming drive cache: write through
[ 3168.303633]  sda: sda1
[ 3168.312254] sd 2:0:0:0: Attached scsi removable disk sda
[ 3168.328379] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 3169.399847] FAT: Unrecognized mount option "usefree" or missing value
:~$ 

I can get the pictures off with fedora or pclinuxos, so I know its not the camera.
thanks for your help.

New info.. after researching pmount command, i found i could connect the camera, press cancel on the pop-up error message mentioned above, then from a terminal, type pmount /dev/sda1 camera   After that, it gives me the pop-up that i used to get when it worked right, and it allows me to copy pictures from the camera.  when i am through, i have to enter: pumount camera to unmount the camera.  I also created /media/sda1 and /media/usb directories, but not sure if i really needed to.

good news is i can copy pictures from the camera via ubuntu.
bad news is i have to manually mount and unmount it.  not really sure how to automate this..
anyone else have this problem, or know how i can fix it?

---

