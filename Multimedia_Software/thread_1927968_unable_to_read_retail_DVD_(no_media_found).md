---
title: "unable to read retail DVD (no media found)"
date: 2012-02-19
forum: Multimedia Software
---

### Post by chandu870114 on 2012-02-19
Hi

My CD/DVD drive is reading all data CDs & DVDs but unable to recognize retail DVDs. I inserted a retail DVD Disc(movie) in my drive, it is trying to read for few seconds but it failed.

I installed 
> sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu

> sudo apt-get install ubuntu-restricted-extras


Result from fstab
**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro,user_xattr 0       1
/dev/sda5       none            swap    sw              0       0



Please tell if am missing anything !!!

---

### Post by ajgreeny on 2012-02-19
> **chandu870114 said:**
> Please tell if am missing anything !!!
You are probably missing libdvdcss2.

See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) for how to get it.  Asd you seem to have enabled the medibuntu repos you can also use ```
sudo apt-get install libdvdcss2
``` as I think it is still there for 11.10.

---

### Post by chandu870114 on 2012-02-19
Thanks for your response.
ya I already installed libdvdcss2.
I am using ubuntu 10.04 version

---

### Post by ajgreeny on 2012-02-19
I assume the DVD is not the wrong regional code?

---

### Post by winh8r on 2012-02-19
You could try this:

```
sudo apt-get install libdvdread4 libdvdnav4 vlc
```


taken from part 4 of this:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia]("http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia")

If this does not work then there is a lot of other info there too.

hope this helps.

---

