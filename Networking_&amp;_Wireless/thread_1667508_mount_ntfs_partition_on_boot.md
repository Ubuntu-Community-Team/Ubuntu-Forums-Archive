---
title: "mount ntfs partition on boot"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by boarder428 on 2011-01-14
On my tri boot system I have a 750 GB HD that is formatted with NTFS, I would like to share it between windows and linux.  How can I mount it at boot up so I can access it in Ubuntu?  I want to be able to set it as the default rip drive for Kino and it won't let me!

---

### Post by Naitsirhc Hsem on 2011-01-14
use the search bar on this site, "mount ntfs fstab"

---

### Post by DanPiazza on 2011-01-15
I'm also wondering about this.

---

### Post by I'mGeorge on 2011-01-15
you will have to edit the /etc/fstab file.In your terminal type

```
sudo gedit /etc/fstab
```

There if you mount an NTFS drive you will have to add a line something like this

```
/dev/sda1 /mnt/mount_point ntfs-3g defaults,locale=en_US.UTF-8	0 0
```

the /dev/sda1 it's your hdd partition, to find out which are your unmounted hdd partitions just do 

```
sudo /sbin/fdisk -l
```

/mnt/mount_point it's your mounting point, and it can be anywhere you want it to be

ntfs-3g it's your file system type

what follows after the file system type are some mounting options and the two zeros are dump and fsck options. If you wanna read more about it check out this quick brief [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Another much more straight forward way it would be to install a software named disk-manager

```
sudo apt-get install disk-manager
```

With it you will easily permanently mount and dismount any partition you want

---

### Post by vanadium on 2011-01-15
Chances are increasing that your drive will mount inconsistently between boots. In modern hardware, the device assignment can change between boots. That is why you should be referring to the partition using its unique identifier, rather than by device name.

The UUID can be seen from the command:
```

sudo blkid

```

In your fstab, replace the device name, e.g. /dev/sda1, by the corresponding UUID. You can just copy/paste the portion 'UUID="####...##"' from the above output.

---

### Post by boarder428 on 2011-01-16
thanks for the tuxfiles link "I'm George" I'm going to do some reading there first, I prefer to understand how it works over using software.  I'm not exactly sure what to put for the mount point. My partition i'm trying to mount is /dev/sda2. Also thanks vanadium I'll keep that in mind as well ```
corey@corey-laptop ~ $ sudo blkid
/dev/sda1: UUID="5CC8E160C8E138C2" TYPE="ntfs" 
/dev/sda2: UUID="A448C1AF48C18092" LABEL="Data" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="9cbc4d3d-5001-4cfd-9a70-0233172614da" 
/dev/sda6: UUID="c533c57d-7b4e-4250-8f8c-bf626256f09a" TYPE="ext3" 
```

---

### Post by agarzon on 2011-01-23
The mount point is the folder where you want your system to be on.

For example, if you want your system mounted in you home folder, you would create a folder there, or mounted directly (I personally would create a folder there), like this:

/home/corey/your-NTFS-drive

---

### Post by boarder428 on 2011-01-25
I found the information I needed by reading the info In this link [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html") that I'mGeorge supplied.  I entered the following line to /etc/fstab```
UUID=A448C1AF48C18092 /media/Data ntfs-3g auto,rw,user 0 0
```

---

