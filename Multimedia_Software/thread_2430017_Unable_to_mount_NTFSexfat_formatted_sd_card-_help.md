---
title: "Unable to mount NTFS/exfat formatted sd card- help"
date: 2019-10-26
forum: Multimedia Software
---

### Post by adi50 on 2019-10-26
So I purchased a new SD card for my camera and used it without first formatiing it to fat32

Trying to mount it gives the following error:

Error mounting system-managed device /dev/mmcblk0p1: Command-line `mount "/mnt/camera"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'
 (udisks-error-quark, 0)

When I look in Disks I get this information about the formatting:

Partition Type: HPFS/NTFS

Contents: exFAT (version 1.0) 


How can I mount this so that I can access my pictures?

---

### Post by Yellow Pasque on 2019-10-26
> mount: unknown filesystem type 'exfat'
If you are getting ^this error, you probably need to install the appropriate packages to use exfat. Run the following command and try to mount it again:
```
sudo apt-get install exfat-fuse exfat-utils
```

---

