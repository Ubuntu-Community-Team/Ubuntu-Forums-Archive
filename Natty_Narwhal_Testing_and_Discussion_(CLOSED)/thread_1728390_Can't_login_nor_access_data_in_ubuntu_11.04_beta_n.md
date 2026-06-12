---
title: "Can't login nor access data in ubuntu 11.04 beta not even from mounted systems"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CesarOscar on 2011-04-13
After an disk-upgrade in the beta version of ubuntu natty 11.04 i had an issue that i couldn't log on in my account. Neither the mouse nor the keyboard react in the account selection menu. I [read]("http://www.ubuntuforums.org/showthread.php?t=1713332&highlight=upgrade+natty") that unselecting the quiet splash i'll be able to gasp better the issue. I did from the Debian partition i was in but lose the ubuntu kernel version on the os selection menu, showing only debian. As expected, ubuntu partition still exist. 

As you may be aware of, the last natty updata brought an data security app, that does not allow me to access the folders in /home/user. As it is a .desktop file i tried to execute it by 
```
exec Access-Your-Private-Data.desktop
```
&
```
 Access-Your-Private-Data.desktop
```
Neither worked.

I would like help in one of these, recover the access to natty or recover the data in natty's home folder. 

If it helps: /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=875b2073-f608-4c8f-932d-815cb434ebb6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=575001f2-70ae-4483-8e46-243386136881 none            swap    sw              0       0

```

fdisk
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7f1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4507    36196676   83  Linux
/dev/sda2            4507       14594    81021953    5  Extended
/dev/sda5           14345       14594     2000896   82  Linux swap / Solaris
/dev/sda6            4507       13974    76041216   83  Linux
/dev/sda7           13974       14345     2977792   82  Linux swap / Solaris

```

---

### Post by CesarOscar on 2011-04-14
Bump

---

### Post by uRock on 2011-04-14
Moved to Natty Narwhal Testing & Discussion.

---

### Post by CesarOscar on 2011-04-14
thanks

---

### Post by cariboo on 2011-04-14
I assume you have an encrypted home directory? this link may help:

[http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/](http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/)

---

### Post by CesarOscar on 2011-04-14
> **cariboo907 said:**
> I assume you have an encrypted home directory? this link may help:

[http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/](http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu/)

Thanks, i tried but i get an error, it says: Error mounting eCryptfs: [-20] Not a directory

How can i fix it?

---

