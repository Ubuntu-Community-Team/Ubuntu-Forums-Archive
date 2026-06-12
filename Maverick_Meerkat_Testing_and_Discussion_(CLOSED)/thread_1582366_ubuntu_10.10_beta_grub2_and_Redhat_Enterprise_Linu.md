---
title: "ubuntu 10.10 beta grub2 and Redhat Enterprise Linux 5.5 dual boot"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by MDguy on 2010-09-26
We intalled Redhat Enterprise Linux on our ubuntu box which has ubuntu and Windows 7. After installation, the boot menu disappeared, only Redhat booted. We then fixed grub with the ubuntu live CD,  and grub2 was installed and updated.
However, Redhat did not appear on the boot menu and we can not launch Redhat. Our ubuntu is on /dev/sda5 while our Redhat Linux is on /dev/sda12. Does anybody know how to modify the grub.cfg file on ubuntu to resolve the problem? 
Thanks.

---

### Post by Irony on 2010-09-26
Open up;

```
/etc/grub.d/40_custom
```

Add to it your own links and it will look something like this;

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Redhat" {
	insmod ext2
	set root=(hd0,3)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 ro
	initrd /boot/initrd.img-2.6.32-24-generic
}
```

Then save it and do;

```
sudo update-grub
```

---

### Post by MDguy on 2010-09-26
Thanks. Tried but no luck. here is result of "sudo fdisk -l"
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004930c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        6547    52479456    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            6547       27475   168103600    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           27475       60802   267699201    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           34323       47071   102403215+  83  Linux
/dev/sda6           47072       58607    92657472   83  Linux
/dev/sda7           59529       60063     4287488   82  Linux swap / Solaris
/dev/sda8           60063       60802     5934080   82  Linux swap / Solaris
/dev/sda9           58607       59529     7403302+  82  Linux swap / Solaris
/dev/sda10          34037       34323     2290688   82  Linux swap / Solaris
/dev/sda11          33764       34037     2198528   82  Linux swap / Solaris
/dev/sda12          27475       27488      102382   83  Linux
/dev/sda13          27488       33764    50412526   8e  Linux LVM

Partition table entries are not in disk order
/dev/sda6 is my ubuntu and dev/sda12 is Red hat.

I wrote 40_custom as

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Redhat" {
	insmod ext2
	set root=(hd0,12)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda12 ro
	initrd /boot/initrd.img-2.6.32-24-generic
}
It did not work, I changed root to root=(hd0,11) and root=/dev/sda11, still no luck.
Where is my problem?
After update-grub, I could not see any changes on file /boot/grub/grub.cfg, which is the boot menu that really appears.
I appreciate your help very much.

---

### Post by Irony on 2010-09-26
Make sure the links are correct, I very much doubt they are actually;

```
/boot/vmlinuz-2.6.32-24-generic root=/dev/sda12 ro
/boot/initrd.img-2.6.32-24-generic
```

To find these links navigate to your **redhat boot folder** from ubuntu and find out what they actually are.

Make sure afterwards to;

```
sudo update-grub
```

The changes to;

```
/boot/grub/grub.cfg
```

should appear at the bottom of the file.

---

### Post by Irony on 2010-09-26
Also you only need one swap not 5!

---

### Post by Elfy on 2010-09-26
moved to meerkat forum

---

### Post by MDguy on 2010-09-26
Changed 40-custom as follows
 
menuentry "Redhat" {
#insmod ext2
	set root=(hd0,12)
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sda12 ro
	initrd /initrd-2.6.18-194.el5.img
}
 
This time redhat launched but failed. The last error message is "kernel Panic. Attemped to kill init"
 
I checked /dev/sda5, Linux Image and Kernel image are there. Any problem this time?

---

### Post by drs305 on 2010-09-26
> **MDguy said:**
> 
menuentry "Redhat" {
#insmod ext2
	set root=(hd0,12)
	linux /vmlinuz-2.6.18-194.el5 root=/dev/sda12 ro
	initrd /initrd-2.6.18-194.el5.img
}


Don't know about RedHat, but Ubuntu's boot files are normally in:

> 	linux [COLOR="Red"]/boot[/COLOR]/vmlinuz-2.6.18-194.el5 root=/dev/sda12 ro
	initrd [COLOR="Red"]/boot[/COLOR]/initrd-2.6.18-194.el5.img

From the grub prompt, you should find the kernel and image if you run:
```
ls (hd0,12)/boot
```

/boot is only omitted for the 'shortcuts' **vmlinuz** and **initrd.img** - not when the entire kernel is referenced.

---

### Post by Irony on 2010-09-26
> **MDguy said:**
> I checked /dev/sda5, Linux Image and Kernel image are there. Any problem this time?
You said redhat was in sda12 now you are saying it is in sda5?

Also check what drs305 said, your boot path is wrong.

---

### Post by MDguy on 2010-09-26
Sorry, I typed wrong, I checked /dev/sda12 and found both Linux Image and Kernel Image are there. It appears that Redhat Enterprise is very different from other Linux.
The boot part is in /dev/sda12, but all others are in /dev/sda13 using logical volume (LVM). Should we configure differently?
The problem has not been resolved. Wondering....

---

### Post by MDguy on 2010-09-26
I tried what drs305 said, it did not work. the images are not under /boot, just directly under /dev/sda12. If I add /boot, I got error msgs  that files are not found.

---

### Post by MDguy on 2010-09-26
The problem was resolved by reinstalling Redhat Enterprise and using Redhat as the boot partition. Modify menu.lst and and uncomment the "hiddenmenu" line. It appears that grub2 on ubuntu is unable to boot Redhat Enterprise Linux while grub on Redhat can boot ubuntu and Windows.

---

