---
title: "Can' read DVD-R with external usb player"
date: 2009-12-03
forum: Multimedia Software
---

### Post by access-denied on 2009-12-03
I recently bought an external USB player LG GE20LU10. When i put some DVD-R that i have already recorder with my camera it seems that it auto mounts the disc but in a second the mount icon for this disc is vanished. When i go to the mount point "/dev/UDF Volume" it is empty.
The same disks are working in the same device under Windows XP without problems. The device seems to be able to read CD's under Ubuntu (9.10 upgrade from 9.04)  but with DVDs ... no luck!
I tried misc things but no progress.
Any ideas? 
The output from "sudo lshw -c disk"
 *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GE20LU10
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/UDF Volume
       version: FE06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/UDF Volume
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted

---

