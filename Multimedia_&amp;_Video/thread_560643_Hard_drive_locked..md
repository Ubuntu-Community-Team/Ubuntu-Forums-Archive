---
title: "Hard drive locked."
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by l337a on 2007-09-26
My secondary hard drive is locked even after partitioning it to the ext3 file system format.

tyler@tyler-desktop:~$ df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             27617036  23610708   2603456  91% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                  517644       100    517544   1% /var/run
varlock                 517644         0    517644   0% /var/lock
procbususb              517644       108    517536   1% /proc/bus/usb
udev                    517644       108    517536   1% /dev
devshm                  517644         0    517644   0% /dev/shm
devpts                       0         0         0   -  /dev/pts
lrm                     517644     33788    483856   7% /lib/modules/2.6.20-15-generic/volatile
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc
/dev/sdb1             59084932    184272  55899320   1% /media/disk


How on earth can i unlock this so i can dump all my music back on it? :B

---

### Post by yabbadabbadont on 2007-09-27
```
sudo chown tyler:users /media/disk
```

:)

---

