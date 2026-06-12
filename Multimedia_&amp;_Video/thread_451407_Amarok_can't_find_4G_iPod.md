---
title: "Amarok can't find 4G iPod"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by cri on 2007-05-22
Greetings, 

I'm running Feisty Kubuntu. Recently I ran into problems with my iPod and had to restore it via iTunes. Prior to the restore it worked great with Amarok. I'd plug the iPod in and Amarok would read it no problem. However, since the restore Amarok cannot find the iPod. When I plug the iPod in I see the following in /var/log/messages:
```

May 22 10:15:37 localhost kernel: [ 2227.956000] usb 1-6: new high speed USB device using ehci_hcd and address 5
May 22 10:15:37 localhost kernel: [ 2228.088000] usb 1-6: configuration #1 chosen from 1 choice
May 22 10:15:38 localhost kernel: [ 2229.012000] usbcore: registered new interface driver libusual
May 22 10:15:39 localhost kernel: [ 2229.172000] Initializing USB Mass Storage driver...
May 22 10:15:39 localhost kernel: [ 2229.176000] scsi2 : SCSI emulation for USB Mass Storage devices
May 22 10:15:39 localhost kernel: [ 2229.176000] usbcore: registered new interface driver usb-storage
May 22 10:15:39 localhost kernel: [ 2229.176000] USB Mass Storage support registered.
May 22 10:15:44 localhost kernel: [ 2234.176000] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
May 22 10:15:44 localhost kernel: [ 2234.176000] SCSI device sdb: 78126047 512-byte hdwr sectors (40001 MB)
May 22 10:15:44 localhost kernel: [ 2234.180000] sdb: Write Protect is off
May 22 10:15:44 localhost kernel: [ 2234.180000] SCSI device sdb: 78126047 512-byte hdwr sectors (40001 MB)
May 22 10:15:44 localhost kernel: [ 2234.180000] sdb: Write Protect is off
May 22 10:15:44 localhost kernel: [ 2234.180000]  sdb: sdb1 sdb2
May 22 10:15:44 localhost kernel: [ 2234.252000] sd 2:0:0:0: Attached scsi removable disk sdb
May 22 10:15:44 localhost kernel: [ 2234.252000] sd 2:0:0:0: Attached scsi generic sg2 type 0

```
Which looks good. Here is my corresponding /etc/fstab entry:
```

/dev/sdb2 /media/ipod vfat defaults,umask=0002,uid=0,gid=29,noauto,rw,user 0 0

```
And that seems to work because when i `ls /media/ipod` I can see the contents of the ipod. 
In my Amarok media devices settings autodetected is device /dev/sdb2 with mount point /media/ipod. However, when I try to connect to the ipod I get "Media Device: No mounted iPod found." That's the kicker. I have no idea why it can't find the ipod when it is clearly mounted at /media/ipod. Here is what `fdisk -l` shows me:
```

Disk /dev/sdb: 40.0 GB, 40000536064 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131    0  Empty
/dev/sdb2               6        4863    39021885    b  W95 FAT32

```
Which is clearly my iPod on /dev/sdb2. What gives? Any hints? Many thanks in advance.

---

### Post by cri on 2007-05-25
Interestingly, If I go to settings --> configure amarok --> media devices and switch the plugin from "Apple iPod Media Device" to "Generic Audio Player" Amarok can connect to the iPod just fine. Problem is it just shows the iPods contents as if it were another drive. I can browse it's contents but I can't really browse my collection iPods style. Apparently the problem isn't so much with mounting as it is with Amarok being able to read/recognize the iPod as an iPod and read its contents.

---

### Post by ske1fr on 2007-05-25
Forgive me if I display some ignorance here, but are you sure you need an fstab entry?  I have a couple of flash mp3 players that I just plug in after boot and click on the resulting desktop icon to "open" and  mount.  Try commenting out that fstab entry, restart and see if the iPod "just works" when you plug it in.

I'm assuming you don't start up your computer with the iPod already attached?  So you're hotplugging it into the USB port?

---

