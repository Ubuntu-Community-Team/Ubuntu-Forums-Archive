---
title: "Ubuntu lost my dvd drive?"
date: 2012-09-20
forum: Multimedia Software
---

### Post by afulldeck on 2012-09-20
For some reason, ubuntu lost my dvd drive in my laptop. Any ideas how I get it back. Its not listed as a device and when I put in the dvds nothing happens. It was working most of this evening....
[ATTACH]224441[/ATTACH]

It used to reside at the top of this list.....

---

### Post by afulldeck on 2012-09-20
I did try sudo mount -t auto /dev/dvd /media/dvd

but got an error .... mount: mount point /media/dvd does not exist

a little lost here...

---

### Post by afulldeck on 2012-09-20
When I checked the Media folder there was nothing in it.....so media exist, but media/dvd doesn't

Any ideas? Anyone?

---

### Post by GeForce 9500GT on 2012-09-21
> **afulldeck said:**
> I did try sudo mount -t auto /dev/dvd /media/dvd but got an error .... mount: mount point /media/dvd does not exist
 
What happens when you do this first ```
sudo mkdir /media/dvd
``` and then perform ```
sudo mount -t auto /dev/dvd /media/dvd
```

---

### Post by afulldeck on 2012-09-21
Unfortunately, I get another error.

 mount: no medium found on /dev/sr0

Well I know the player exits and is spinning...

I think DVD encoder OMGrip somehow stomped all over my dvd player/writer with an abrupt stop. Removing that software. 

BTW, I'm using a T400.

---

### Post by afulldeck on 2012-09-21
BTW, Mount command gives me: 

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/afulldeck/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=afulldeck)

and cating  fstab I get: 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fd357674-2a4b-4ef7-b48b-c17e6c1e4efd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3e14f15b-fd0c-40f9-bed5-01b6ce648169 none            swap    sw              0       0


Not sure to go from here, any hints----Anyone?

---

### Post by afulldeck on 2012-09-21
From wodim I get: 

wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'    rwrw-- : 'Optiarc' 'DVD RW AD-7910S'
-------------------------------------------------------------------------

So part of ubuntu knows about this dvd player. Thought on what I should do to recover this and make it work?

---

### Post by afulldeck on 2012-09-21
And Ls -l   brings me to 
ls -l /dev/dvdrw
lrwxrwxrwx 1 root root 3 Sep 21 05:59 /dev/dvdrw -> sr0

So /dev/dvdrw      thinks I'm here     -->sr0
wodin                       says I'm here        -->sg1

and I'm nowhere....Does anyone have any idea what might have happened and how I can fix it?

---

### Post by GeForce 9500GT on 2012-09-21
> **afulldeck said:**
> From wodim..... 
Experience from my past is that Wodim causes a lot of troubles. Best indication for this is the usage of Brasero (icm. Wodim) which is an unstable program anyway. 
 

> # / was on /dev/sda1 during installation
UUID=fd357674-2a4b-4ef7-b48b-c17e6c1e4efd / ext4 errors=remount-ro 0 1

This is your internal HDD where you installed Ubuntu onto. This is normal.
 
> # swap was on /dev/sda5 during installation
UUID=3e14f15b-fd0c-40f9-bed5-01b6ce648169 none swap sw 0 0

This is your swap partition. Also here, normal.
 
CD/DVD drives are not mentioned in fstab since they are mounted a bit different than your HDD. So, not finding your CD/DVD drive in fstab is normal.
 
> Optiarc DVD RW AD-7910S
I also have a Sony/Optiarc DVD RW drive and had in the past similar things. I avoid programs who are using Wodim. But who knows what the real problem is....

---

### Post by afulldeck on 2012-09-21
Any ideas on what to do? Anyone? Am I really forced to reinstall ubuntu just to get my dvdrw working again?

---

### Post by afulldeck on 2012-09-21
So is the answer to those who know a complete reinstall of ubuntu?

---

### Post by afulldeck on 2012-09-21
Okay, out of frustration I reload Ubuntu. Unfortunately, it did not fix the problem. I still cannot see my dvdrw player. Does anyone in this forum know what I should do?

---

### Post by afulldeck on 2012-09-21
I should add that the bios certainly knows about the dvdplayer....folks, I'm running around in circles .... Anyone have any ideas what I should do?

---

### Post by acefromspace on 2012-09-21
I have similar dvd drive (got it used) and have had similar issues! Reading many threads others have too. I took my drive out and removed cover. The spindle that holds disc was dirty... cleaned it with alchohol on a swab. That seemed to help, but I must say this drive is noisy! It works now, but I also had issues with it mounting... still not sure about that. Also, sometimes it gets stuck trying to read disc, and if I hit eject button on drive it opens, then immediately shuts... can't remove disc until the drive finally gives up.
What ubuntu are you using? I have 10.04

---

### Post by afulldeck on 2012-09-21
Absolutely astounding. In my case, it wasn't really dirty. I just blew on the optical reader part and bingo, bob's your uncle it worked. Damn annoying considering (a) it worked during the reinstall of ubunut and (b) I reinstalled ubuntu....

---

### Post by acefromspace on 2012-09-21
Yep, many threads about dvd drives... about giving up on them myself. The only reason I keep them is to burn DVDs that play in home players to give to others.

---

