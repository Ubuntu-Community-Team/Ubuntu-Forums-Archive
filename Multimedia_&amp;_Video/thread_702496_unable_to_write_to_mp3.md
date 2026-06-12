---
title: "unable to write to mp3"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by gorlando on 2008-02-20
i have previously written files to my mp3.

but now i get error stating that read only.

any help with what to do?

---

### Post by timcredible on 2008-02-20
what kind of mp3 player do you have?

---

### Post by gorlando on 2008-02-20
it's a generic no name brand.  actually mp4 i guess since it does videos?

---

### Post by Funky91 on 2008-02-20
go into it and see what the read/write permissions are and post your results. This is my first attempt at resolving a problem so go easy on me! Also try using a different usb port. That worked for me.

---

### Post by gorlando on 2008-02-20
chmod: changing permissions of `/media/disk': Read-only file system

disk permissions attached...

---

### Post by halflife28 on 2008-02-20
Go to the terminal with the MP3 player plugged in and type this in:

```
mount
```

And paste me the output

---

### Post by gorlando on 2008-02-20
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

---

### Post by Funky91 on 2008-02-21
It may sound silly but try it in a different usb port because my samsung mp3 player would not let me write to it but when I unplugged it and put it in a different usb port it worked fine.

---

### Post by gorlando on 2008-02-21
tried different port.  no good.

---

### Post by halflife28 on 2008-02-21
Its mounted just fine. Try going on a Windows PC, plug it in, then "safely remove" the device. Then try plugging the player on Ubuntu.

Sometimes Windows locks the device when you just unplug it.

---

### Post by gorlando on 2008-02-22
i tried safely remove but it didn't work.

---

### Post by gorlando on 2008-02-23
I formatted the mp3 using gparted to fat32.

This has corrected the problem and i can write files to the mp3 now.

---

### Post by gorlando on 2008-02-23
i formatted for fat32 and the device allows me to write files to it, but

now the files are not recognized by the player.

---

### Post by gorlando on 2008-02-23
I really don't know what I did unfortunately, but the player recognizes the files now. all ok.

---

