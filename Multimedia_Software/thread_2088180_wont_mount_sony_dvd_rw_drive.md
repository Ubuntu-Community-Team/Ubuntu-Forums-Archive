---
title: "wont mount sony dvd rw drive"
date: 2012-11-25
forum: Multimedia Software
---

### Post by greatsirkain on 2012-11-25
lshw shows it's there:

*-cdrom
                description: DVD writer
                product: DVD RW DW-D22A
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom3
                logical name: /dev/cdrw3
                logical name: /dev/dvd3
                logical name: /dev/dvdrw3
                logical name: /dev/sr0
                version: BYS3
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc

but it doesn't mount, even wen there is a disk in it. I tried to mount it manually and got this:

mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab

tested it with cds and dvds & it doesn't work. Works fine when booting from it so I know it's not bust

any thoughts?

---

### Post by greatsirkain on 2012-12-07
*ahem* still no further forward with this....I know DVD and CD is a redundant technology but I'd really rather be able to retrieve all my data before it dies completely

---

### Post by dannyboy79 on 2012-12-07
so when you put it in your drive and shut it, nothing pops up on your desktop? Have you tried adding an fstab entry like in the old days?
```
/dev/cdrom /media/cdrom auto ro,noauto,user,exec 0 0
```

make sure to change /dev/cdrom to whatever your device is and also make sure there's a folder within /media/ and it has proper permissions.

That's all I can suggest, I thought having cdrom/dvd-rom entries in fstab were a thing of the past with the automounting capabilities but if it's not working that my next best guess for a solution

---

