---
title: "Ubuntu 9.10 - Unable to play DVD movies"
date: 2010-03-13
forum: Multimedia Software
---

### Post by mouseriot on 2010-03-13
Hey guys,

I've googled the pants out of this and I'm getting no where.

I'm able to open DVD data discs, it's just playing DVD movies which is the problem now.

I've followed the official ubuntu guide on this and it hasn't worked. Even with all the numerous posts regarding the matter I'm still unable to find a fix.

Thus I'm posting here. If I can't get this to work I'm fooking back off to Windows because I've wasted far too many hours as it is.

I'm running P4 2.4 Ghz, NEC 2500a DVD-RW drive. I've also got two other DVD drives, a Pioneer slot drive which I get the exact same problem and another one which I haven't tested yet as it appears to be a software problem.


```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d9564b2e-9a80-461b-968c-4c7488ee9f1c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=46b8ecd0-9aa8-4ec6-9446-8abc3a30386c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  noauto    rw,user,noauto,exec,utf8 0       0
```

Any help would be great in trying to fix this.

---

### Post by subedistra7 on 2010-03-13
applications -> accessories -> terminal

copy + paste this into the opened terminal.

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install libdvdcss2
```

---

### Post by mouseriot on 2010-03-13
> **subedistra7 said:**
> applications -> accessories -> terminal

copy + paste this into the opened terminal.

```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install libdvdcss2
```

I've already tried it, I'll do it again anyway.

---

### Post by subedistra7 on 2010-03-13
> **mouseriot said:**
> I've already tried it, I'll do it again anyway.

are you using movie player to try to watch the dvd?

---

### Post by mouseriot on 2010-03-13
> **subedistra7 said:**
> are you using movie player to try to watch the dvd?

Some DVDs when I insert them the CD/DVD drive icon under My Computer completely disappears. With others sometimes I can see the DVD name but it complains that it's unable to mount it.

---

### Post by mouseriot on 2010-03-13
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by subedistra7 on 2010-03-13
> **mouseriot said:**
> Some DVDs when I insert them the CD/DVD drive icon under My Computer completely disappears. With others sometimes I can see the DVD name but it complains that it's unable to mount it.

that sounds like the mounting issue 9.10 has. its a total bitch with usb drives too.

---

### Post by mouseriot on 2010-03-13
> **subedistra7 said:**
> that sounds like the mounting issue 9.10 has. its a total bitch with usb drives too.

That's a shame.

Whenever I attempt to switch over to Linux from Windows there is usually at least 1 thing that ends up making me crawl back to Windows. Everything was going so well, even Flash works ok.

---

### Post by subedistra7 on 2010-03-13
> **mouseriot said:**
> Whenever I attempt to switch over to Linux from Windows there is usually at least 1 thing that ends up making me crawl back to Windows..

yeah same old. have you tried vlc btw? it may work. if not, screw it.

---

