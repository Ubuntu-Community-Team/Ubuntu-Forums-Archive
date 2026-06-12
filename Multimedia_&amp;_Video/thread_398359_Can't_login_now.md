---
title: "Can't login now"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by captgadget on 2007-03-31
After a day of messing around I finally got my resolution changed but now I can't login. What would be the connection there? I type my user name and then the password. The screen goes blank and then comes back wanting me to enter user name and password again and on and on and on.

---

### Post by taurus on 2007-04-01
At the GUI login screen, press <Ctrl><Alt>F2 and login from that console with your username and password.  Then, post the output of this command here.

```
df -h
```

Otherwise, boot into recovery mode from GRUB menu and post the output of that command here then.

---

### Post by captgadget on 2007-04-01
Sorry I didn't get back sooner. Had to get some sleep.

Fiilesystem        size      used    Avail.   Use%     Mounted on
/dev/hda1         52G    3.6        46G     8%          /
varrun               157M   88K      157M   1%          /var/run
varlock              157M     0        157M  0%           /var/lock
procbususb         10M     120K     9.9M   2%         /proc/bus/usb
udev                  10M     120K     9.9M   2%         /dev
devshm             157M        0      157M   0%         /dev/shm
lrm                    157M     20M    138M   13%         /lib/modules/2.6.17-generic/volat
ile

---

