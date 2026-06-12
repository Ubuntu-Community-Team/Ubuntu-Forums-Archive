---
title: "Someone please help me with my Sansa!"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Joey French on 2008-04-26
I am about to go mad here! My Sansa e280 used to work fine up until recently, now it will not mount, I cannot put files on it, it crashes Rhythmbox. I have done regular updates on a very vanilla Ubuntu Hardy install, and I believe an update broke this functionality (in the last two weeks). I have searched on this forum and have looked at all the relevant threads to no avail. 
It seems that for the last little while my USB devices have been mounted to a slightly different place each time they are mounted. My Sansa, for example, mounts to SD_Player, then to SD_Player__, then to SD_Player___, and so on. Same with my WD external hard drive. 
When I run lsusb I get:
```
Bus 003 Device 014: ID 0781:7421 SanDisk Corp. Sansa E200 series
Bus 003 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 003: ID 1058:0404 Western Digital Technologies, Inc. 
Bus 003 Device 002: ID 0781:9940 SanDisk Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:6104 Hewlett-Packard DeskJet 5650c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```
but it will not mount, it crashes apps, it is very messed up (it used to work flawlessly). Please someone help me get it straight, as I am about to take a trip for a few weeks and need to have this working before I get out on the road.

Thanks,
Joey French

---

### Post by Joey French on 2008-04-26
Interestingly, it mounted today for a minute, and I was able to get some tunes onto it. But then I try it again later, no go. I don't know what to do....

---

### Post by catalina on 2008-04-26
Hi there,

My wife has a sansa as well and it looks like the port that you are plugging the sansa into different ports in your usb card.  I know that sometimes if I have not unmounted a device properly or if it gets hung up in one port the file system still thinks it is there even though it is plugged into another port.

It may be a result of updates, but I would try unmounting it and mounting it in another port, try lusb again and see where it is showing up.

I remember reading a long time ago about someone statically assigning their usb devices to avoid this type of issue.  You may want to scan some forums on this subject and see if any of this is relevant.

Hope it helps!

---

### Post by Joey French on 2008-04-27
Hmmm, you may have something there. When I issue an lsusb, with the unit unplugged, I get a 
```
Bus 003 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 003: ID 1058:0404 Western Digital Technologies, Inc. 
Bus 003 Device 002: ID 0781:9940 SanDisk Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```  
And there is the Sansa. Now, how do I get rid of it? How do I keep this from happening in the future? I always "Safely Remove", so I don't know What has happened...

---

### Post by Joey French on 2008-04-28
Anyone? I just need to know how to remove the Sansa from my system...? When I reboot and lsusb, it is still there, even with the device not plugged in.

---

### Post by Joey French on 2008-05-24
Still trying to get the Sansa to go away so I can mount it. Anyone have any ideas how to get the old mount point to go away so I can mount my player?


Please?

---

### Post by little_penguin on 2008-05-24
I don't have a solution to your problem but just suggest you create a fresh post with a more specific title about what the problem is and what you need help in doing, one that will catch attention, because "help me with my Sansa" is too general. If you use the right buzzwords, one of the experts is more likely to spot it and help you out.

---

### Post by cariboo on 2008-05-24
If it shows up on your desktop just right click on it, then click on unmount volume. If it doesn't show on your desktop you will probably have to unmount it in a terminal

eg:

```
jimk@alexis:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc6             6.5G  4.8G  1.4G  79% /
varrun                992M  264K  992M   1% /var/run
varlock               992M     0  992M   0% /var/lock
udev                  992M   84K  992M   1% /dev
devshm                992M  300K  992M   1% /dev/shm
lrm                   992M   43M  950M   5% /lib/modules/2.6.24-17-generic/volatile
/dev/sdc7             141G   53G   81G  40% /home
/dev/sdc1              79G   56G   23G  71% /media/hda1
/dev/sda1             147G  117G   24G  84% /media/sda1
/dev/scd0              96M   96M     0 100% /media/HIREN'SBOOTCD9.5
/dev/sdb1             147G  656M  139G   1% /media/disk
/dev/sdd1             2.0G  389M  1.6G  20% /media/disk-1

jimk@alexis:~$ umount /media/disk-1

jimk@alexis:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc6             6.5G  4.8G  1.4G  79% /
varrun                992M  264K  992M   1% /var/run
varlock               992M     0  992M   0% /var/lock
udev                  992M   84K  992M   1% /dev
devshm                992M  300K  992M   1% /dev/shm
lrm                   992M   43M  950M   5% /lib/modules/2.6.24-17-generic/volatile
/dev/sdc7             141G   53G   81G  40% /home
/dev/sdc1              79G   56G   23G  71% /media/hda1
/dev/sda1             147G  117G   24G  84% /media/sda1
/dev/scd0              96M   96M     0 100% /media/HIREN'SBOOTCD9.5
/dev/sdb1             147G  656M  139G   1% /media/disk



```

In this case I used a 2GB USB key, as you can see when I enter df -h it shows up at the very end of the listing as dev/sdd1 and it is mounted on /media/disk-1. When I enter the command:

```
umount /media/disk-1
```

and the do a df -h again you can see that the USB key is not longer mounted.

Good Luck

Jim

---

### Post by Joey French on 2008-05-28
Hmm, this is what I get:
```
joey@cnidaria:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G   32G  183G  15% /
varrun                506M  208K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M  260K  506M   1% /dev/shm
lrm                   506M   38M  469M   8% /lib/modules/2.6.24-17-generic/volatile
/dev/sdc1             299G  197G  102G  66% /media/WD USB 2
gvfs-fuse-daemon      227G   32G  183G  15% /home/joey/.gvfs

```

However, when I do this:
```
joey@cnidaria:~$ lsusb
Bus 003 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 003: ID 1058:0404 Western Digital Technologies, Inc. 
Bus 003 Device 002: ID 0781:9940 SanDisk Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:6104 Hewlett-Packard DeskJet 5650c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

It's still there (the player is not connected to the machine at this time). Any ideas?

---

### Post by chkneater on 2008-08-23
Why can't you right click on the volume icon in Computer folder to unmount the USB?

---

