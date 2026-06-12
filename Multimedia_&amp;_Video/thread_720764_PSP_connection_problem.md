---
title: "PSP connection problem"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by twooften on 2008-03-10
I have just hooked up my PSP to my PC, it see's it, sets it up as an IPOD, says there is 880K free, there is a 1G card in there with about half empty/full. It shows no files or dir's, hidden files are to be shown, and I do have permission to write, as long as its less than 880K.

mount tells me

/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sde on /media/disk-1 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree):KS

I tried (found here [http://ubuntuforums.org/showthread.php?t=670369&highlight=PSP+problems](http://ubuntuforums.org/showthread.php?t=670369&highlight=PSP+problems))

sudo rmmod ehci_hcd

how do I change back? because it didn't work.

And any advice on the problem would be a great help.

Thanx in advance!

---

