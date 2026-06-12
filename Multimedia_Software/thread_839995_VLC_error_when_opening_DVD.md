---
title: "VLC error when opening DVD"
date: 2008-06-24
forum: Multimedia Software
---

### Post by presStr on 2008-06-24
On Hardy Heron using VLC and get the following error:

Unable to open 'dvd:///dev/hdd'

(Actually have Hardy installed a while, just never got round to playing DVDs - vlc worked just fine pre-Hardy)

/etc/fstab has

/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

I've seen forums with comments on libdvdcss2 and other packages but I've got these installed.

Any suggestions?

---

### Post by mc4man on 2008-06-25
May be good to take a look at. run 
```
sudo lshw -C disk
```

---

### Post by presStr on 2008-06-25
Got the following...

  *-cdrom:0
       description: DVD reader
       product: DVD-ROM GDR8163B
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Wiener Staatsoper DVD1
       version: 0D20
       capabilities: removable audio dvd

I presume that first logical name should be changed?

---

### Post by mc4man on 2008-06-25
> I presume that first logical name should be changed?
_No_
If you want to get vlc to work then when you go file ->  open disk make the device name /dev/scd0
To fix things up post from /etc/udev/rules.d - the contents of 70-persistent-cd rules
(going to need that file to figure out your symlinks even if you don't want to fix things up)
Your issues are similar to this
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

Atm don't worry about fstab, you can edit it later as needed

---

### Post by presStr on 2008-07-15
> **mc4man said:**
> _No_
If you want to get vlc to work then when you go file ->  open disk make the device name /dev/scd0
...

Thanks a lot that did the trick.

---

