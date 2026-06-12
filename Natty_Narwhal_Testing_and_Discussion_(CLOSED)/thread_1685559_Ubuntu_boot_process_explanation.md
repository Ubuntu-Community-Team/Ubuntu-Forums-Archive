---
title: "Ubuntu boot process explanation"
date: 2011-02-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by bonixavier on 2011-02-10
I was curious about Natty Narwhal and Unity so I cleared up a couple of gigabytes and installed 10.10 to it to try to upgrade to the alpha release. I had a problem when I tried to boot Ubuntu.

As we all know, Ubuntu uses grub 2 as its bootlader, but I am not interested in grub 2. Its script-messiness gets to my nerves so I chose to boot Ubuntu directly from LILO (I'm a Slacker). Ubuntu's configuration in lilo.conf was this:
```
image = /mnt/hd/boot/vmlinuz-2.6.35-22-generic 
initrd = /mnt/hd/boot/initrd.img-2.6.35-22-generic
root = /dev/sda3
label = Ubuntu
read-only
```Other arguments passed to LILO were compact, lba32 and large-memory.

However, as I tried to boot, I was dropped to busybox because, from what I could make of the warnings in the screen, my disk had been mounted as /dev/sde instead of /dev/sda, making it impossible to boot (conflicted with fstab, for example). The messages printed on the screen were these ( I had to copy it all by hand so I only copied what seemed relevant - I may have missed something fundamental, in which case I apologize):
> [COLOR=#000000][FONT=Sans Serif][COLOR=#181818][FONT=monospace][       1.899637] sd 2:0:0:0: [sda] Attached SCSI removable disk
[/FONT][/COLOR][/FONT][/COLOR]
(snip)

[       1.917721] ata 3.00: ATA-7: WDC WD1600AAJS-22PSA0, 05.06H05, max UDMA/133
[       1.919200] ata 3:00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[       1.936549] ata 3:00: configured for UDMA/133
[       1.938152] scsi 3:0:0:0: Direct Access ATA WDC WD1600AAJS-2 05.0 PQ:0 ANSI: 5
[       1.939850] sd 3:0:0:0: Attached scsi generic sg4 type0
[       1.939863] sd 3:0:0:0: [sde] 312581808 512-byte logical blocks: (160GB/149GiB)
[       1.939948] sd 3:0:0:0: [sde] Write cache: enabled, read cahe: enabled, doesn't support DPO or FUA
[       1.940164] sde: sde1 sde2 sde3 sde4

(snip)

Begin: Running /scripts/local-premount... done
mount: mounting /dev/root on /root failed: No medium found
Begin: Running /scripts/local-bottom... done
done
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootargPassing the symlinks in / of the kernel and initrd to LILO caused the same behavior. 

Is there anything that has to be loaded besides the kernel and the initrd in order to boot Ubuntu? What can have caused such an error? I have been able to boot Debian Squeeze, Gentoo, Arch and, of course, Slackware from LILO so I don't get what's going on here.

Please do not suggest chain-loading. It works. I did that to test the install and, as it booted normally, I concluded it was not defective. I'm not interested in booting anything outside of LILO. LILO **can** and **does** boot ext4. If there was a time it didn't, that time has been over at least since last May. All my partitions, except for swap, are ext4 and LILO boots them just fine.

I don't have Ubuntu installed anymore because I wasn't able to boot it properly from LILO. I am still interested in checking Unity out, though, so, if there's a solution, I'll be trying that again.

---

### Post by philinux on 2011-02-11
Moved to natty testing.

---

### Post by jerrylamos on 2011-02-11
Natty Grub2 has been really screwed up on my pc's, all of which are multiboot and a couple share a USB hard drive.

So "if" I can get Natty to install or update, next I boot up Maverick with an /etc/grub.d/06_custom like so:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above
menuentry "Lucid LTS sda6" {
set root=(hd0,6)
linux /vmlinuz root=/dev/sda6 ro quiet
initrd /initrd.img
}
menuentry "Narwhal on sda5" {
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro quiet
initrd /initrd.img
}
menuentry "Meerkat Rel on sda12" {
set root=(hd0,12)
linux /vmlinuz root=/dev/sda12 ro quiet
initrd /initrd.img
}
menuentry "TinyCore on sda14" {
set root=(hd0,14)
linux /boot/bzImage root=/dev/sda14 tce=hda14/tce quiet
initrd /boot/tinycore.gz
}
menuentry "Debian Live on /dev/sda8" {
set root='(hd0,8)'
linux /live/vmlinuz boot=live root=/dev/ram ramdisk_size=524388 rw quiet
initrd /live/initrd.img
}

```
Then
sudo chmod 755 /etc/grub.d/06_custom
sudo update-grub
sudo grub-install /dev/sda

Why Natty Grub 2 wants to take a fairly simple process and make a holy mess out of it I don't know.  More importantly my pc's don't understand Natty Grub 2 either.

Jerry

---

### Post by drs305 on 2011-02-11
> **bonixavier said:**
>  Ubuntu's configuration in lilo.conf was this:
```
image = /mnt/hd/boot/vmlinuz-2.6.35-22-generic 
initrd = /mnt/hd/boot/initrd.img-2.6.35-22-generic
root = /dev/sda3
label = Ubuntu
read-only
```Other arguments passed to LILO were compact, lba32 and large-memory.


Is there anything that has to be loaded besides the kernel and the initrd in order to boot Ubuntu? What can have caused such an error? I have been able to boot Debian Squeeze, Gentoo, Arch and, of course, Slackware from LILO so I don't get what's going on here.

I'm away from my Desktop on which I've played with lilo, but the boot failure may be caused by the path you have listed. Since lilo is running before the OS, I would suspect it can't use "/mnt/hd". I'd guess the path should probably not include the "/mnt" and most likely not even "/mnt/hd" unless "hd" is the top folder on the device. Try a more direct path from the device.

---

### Post by bonixavier on 2011-02-11
> **drs305 said:**
> I'm away from my Desktop on which I've played with lilo, but the boot failure may be caused by the path you have listed. Since lilo is running before the OS, I would suspect it can't use "/mnt/hd". I'd guess the path should probably not include the "/mnt" and most likely not even "/mnt/hd" unless "hd" is the top folder on the device. Try a more direct path from the device.
Thank you for your suggestion. However, the boot-loader is installed in Slackware (sda1) and Ubuntu lied in sda3. If I assigned a /boot/vmlinuz path, LILO would use Slackware's kernel. You have to add the mount point to lilo.conf. After you run lilo, it stores the block address in the mbr, not a path. Here, it's different from grub and that's why you have to run lilo all the time you have a kernel update. Unfortunately, that doesn't fix it.

I suspect it has something to do with the initrd. Once I had a similar problem when I was toying with Arch in an old computer and I added IDE support instead of PATA. That made the partitions be named /dev/hda like in the old days. OTOH, if I chain-load, it works so I think something else is being called to help boot the OS and I can't figure out what it is.

---

