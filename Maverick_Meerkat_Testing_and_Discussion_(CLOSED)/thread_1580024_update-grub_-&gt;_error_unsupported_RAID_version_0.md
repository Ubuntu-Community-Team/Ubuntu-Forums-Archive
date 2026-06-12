---
title: "update-grub -&gt; error: unsupported RAID version: 0.91."
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Roderik on 2010-09-22
I've got a following setup

Quad code intel
8gb memory
6 x 1TB sata disk, in a raid5 array

I've installed maveric i386 on a 4x 1TB array. It boots just fine.
I've added the two other disks, and i'm currently reshaping the array to include the two extra disks. (i mention this because maybe it's relevant)

I've run dist upgrade this morning, no problems, but i noticed jus tnow that only 3GB memory was available. So i installed the pae kernel to fix this. Also tried to install the server kernel

Suddenly, i get a lot of errors from grub-update. During apt-get and by hand.

```

root@tenedos:~# update-grub
Generating grub.cfg ...
error: unsupported RAID version: 0.91.
error: unsupported RAID version: 0.91.
error: unsupported RAID version: 0.91.
error: unsupported RAID version: 0.91.
error: unsupported RAID version: 0.91.
error: unsupported RAID version: 0.91.
/usr/sbin/grub-probe: error: no such disk.

```

An update was available for grub-pc so i installed that one as well, no improvement.
No real info to be found on google.

I'm afraid to reboot, since i don't think it will boot anymore.

---

### Post by cariboo on 2010-09-22
You may want to have a look at [this]("http://ubuntuforums.org/showthread.php?t=1573192&highlight=raid") thread. They seem to have solved the problem.

---

### Post by Roderik on 2010-09-23
OK, purging grub and deleting /boot/grub before reinstalling grub did the trick! Thanks

---

