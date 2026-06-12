---
title: "New Motherboard / Mount Problems"
date: 2012-01-22
forum: Mythbuntu
---

### Post by Senkoboy on 2012-01-22
I had to replace my motherboard. I am running a ATA drive for my operating system and  Sata Drive for recordings.  My operating system will boot, but won't mount my second hard drive, (error mounting media/sdb1).  If I run a live CD of Linux Puppy it works fine. I shows up in th bios also. I am sure it is a simple fix, I am not a Linux expert. My new board is  Intel DP35DPM.

Thanks

---

### Post by Senkoboy on 2012-01-22
It appears that the names of my drives have changed.  

When I run f disk-1 I show:
Disk /dev/sda:1000.2 GB
      dev/sda1

**** /dev sdb:80.0 GB 
     dev/sdb1  Linux
     dev/sdb2  extended
     dev/sdb5 Swap

I know my mount point for my 1000 GB drive was /media/sdb1/
It looks like that is pointing to the wrong drive, what is the best way to fix this?   I have Pysdm installed.

My 1000.2 GB drive is xfs filesystem
My 80.0 GB drive is  ext4 filesystem
My fstab file looks screwed up to me.


 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
/dev/sda1                                  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=db9e9484-96a4-48e0-b357-ef0ce7e670d1  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  xfs   defaults             0  0

---

### Post by nickrout on 2012-01-22
> **Senkoboy said:**
> It appears that the names of my drives have changed.  

When I run f disk-1 I show:
Disk /dev/sda:1000.2 GB
      dev/sda1

**** /dev sdb:80.0 GB 
     dev/sdb1  Linux
     dev/sdb2  extended
     dev/sdb5 Swap

I know my mount point for my 1000 GB drive was /media/sdb1/
It looks like that is pointing to the wrong drive, what is the best way to fix this?   I have Pysdm installed.

My 1000.2 GB drive is xfs filesystem
My 80.0 GB drive is  ext4 filesystem
My fstab file looks screwed up to me.


 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
/dev/sda1                                  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=db9e9484-96a4-48e0-b357-ef0ce7e670d1  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  xfs   defaults             0  0

the best way to fix it is to use the UUID in the fstab file, as per swap in your example.

You can get a list of UUIDs on your system by running ```
sudo blkid
```

Then use the UUID in /etc/fstab instead of /dev/sdb1

---

### Post by Senkoboy on 2012-01-23
Thanks for the information, I'll try to look at it in a couple of days.  Went to work at 5:30 am this morning...........

---

