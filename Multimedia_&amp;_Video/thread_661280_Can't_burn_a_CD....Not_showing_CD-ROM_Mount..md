---
title: "Can't burn a CD....Not showing CD-ROM Mount."
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by Mango84 on 2008-01-07
Hey,

I am new to Ubuntu and Linux in general.  A friend of mine installed Geubuntu for me on my Hewlett Packard.  Well, i tried to burn a CD today.  Everything went fine.  The CD burned (or at least convinced me that it burned) and ejected.  Well just to make sure it was there, I put the CD back into my computer and its icon appeared on my desktop.  The CD was even named after the file it had just burnt.  When I clicked on it, there was no file to be seen.  Later my friend, who installed Linux for me, walked me through what to do on the phone only to get no where.  He was stunned at how difficult this had become.  Upon looking at my disk free (df), we noticed this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              15G  3.8G   10G  28% /
varrun                248M  116K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   64K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              99M   24M   71M  25% /boot
/dev/sda4              22G  7.3G   13G  37% /home



There is nothing for "/dev/sda3" under "Mounted on", I'm not sure, but from what I gathered, it should have CDROM or something like that there.  Once again, I'm a newbie, but any help is much appreciated!  Thanks!!  :o)

---

### Post by schaumkeks on 2008-01-08
> **Mango84 said:**
> Hey,

I am new to Ubuntu and Linux in general.  A friend of mine installed Geubuntu for me on my Hewlett Packard.  Well, i tried to burn a CD today.  Everything went fine.  The CD burned (or at least convinced me that it burned) and ejected.  Well just to make sure it was there, I put the CD back into my computer and its icon appeared on my desktop.  The CD was even named after the file it had just burnt.  When I clicked on it, there was no file to be seen.  Later my friend, who installed Linux for me, walked me through what to do on the phone only to get no where.  He was stunned at how difficult this had become.  Upon looking at my disk free (df), we noticed this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              15G  3.8G   10G  28% /
varrun                248M  116K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   64K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              99M   24M   71M  25% /boot
/dev/sda4              22G  7.3G   13G  37% /home



There is nothing for "/dev/sda3" under "Mounted on", I'm not sure, but from what I gathered, it should have CDROM or something like that there.  Once again, I'm a newbie, but any help is much appreciated!  Thanks!!  :o)

/dev/sda3 is mounted on /. That is your root filesystem.
But you should have a look at the output of "mount" instead of df after inserting the CD. You have to look for the name of your CD/DVD reader device. Perhaps it is /dev/cdrom, /dev/dvd, /dev/scd0 or similar.

Bye, Sven

---

### Post by vamsibethapudy on 2008-01-08
what was the software u used for burning??
i had some problems with gnomebaker while writing files to my dvd-rw

---

### Post by Mango84 on 2008-01-08
> **schaumkeks said:**
> /dev/sda3 is mounted on /. That is your root filesystem.
But you should have a look at the output of "mount" instead of df after inserting the CD. You have to look for the name of your CD/DVD reader device. Perhaps it is /dev/cdrom, /dev/dvd, /dev/scd0 or similar.

Bye, Sven

Where would I go to see this information?  What would I have to type?

---

### Post by Mango84 on 2008-01-08
> **vamsibethapudy said:**
> what was the software u used for burning??
i had some problems with gnomebaker while writing files to my dvd-rw

I used three different disc burning systems.  Gnomebaker was one of them.

---

### Post by Yellow Pasque on 2008-01-08
Type ```
lshw -C disk
```

Also, please post your /etc/fstab file.

---

### Post by Mango84 on 2008-01-09
> **Temüjin said:**
> Type ```
lshw -C disk
```

Also, please post your /etc/fstab file.

Ok, I typed lshw -C disk and this is what I got:

WARNING: you should run this program as super-user.
  *-cdrom                 
       description: DVD reader
       product: CDW/DVD TS-L462C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HP10
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom


I don't remember how to get my /etc/fstab file.  I've asked my friend and he's supposed to reply with how to do it.

---

### Post by vamsibethapudy on 2008-01-09
> **Mango84 said:**
> 
I don't remember how to get my /etc/fstab file.  I've asked my friend and he's supposed to reply with how to do it.

type this in terminal
Code:
```
gedit /etc/fstab
```

---

### Post by Mango84 on 2008-01-09
> **vamsibethapudy said:**
> type this in terminal
Code:
```
gedit /etc/fstab
```

Ok here is my fstab info:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6d6896ba-2835-451e-9594-bde0462d6da6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=04d7162e-3bc8-45ad-b2d4-99d08ee10bc8 /boot           ext3    defaults        0       2
# /dev/sda4
UUID=308d3874-3d01-45e6-8f78-9631bc4f19e7 /home           ext3    defaults        0       2
# /dev/sda2
UUID=f6fd5f59-4fa1-4154-89c9-f0b535d52416 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

