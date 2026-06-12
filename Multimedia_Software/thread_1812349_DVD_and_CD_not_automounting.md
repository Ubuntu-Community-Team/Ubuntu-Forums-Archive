---
title: "DVD and CD not automounting"
date: 2011-07-26
forum: Multimedia Software
---

### Post by Sylos on 2011-07-26
Hello and thanks for looking.

As the title says I am having problems with disk mounting. Most of the time drive will not mount my disk so I cant get at it. Im using 10.04 with LXDE slapped on top. Here are some semi-useful outputs:

sudo lshw -C disk:
```
  *-cdrom
       description: DVD reader
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd
       configuration: status=open

```

Seems odd that it registers the drive as open when it is not (is closed with a disk in).

I have attempted to manually mount it with a number of commands eg:
```
sudo mount /dev/sr0 /media/CD
```

but I get the following error
```
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab
```

I have tried with this on a number disks so its unlikely to be the media. Restarting didnt help until I did it so many times the disk got checked for errors at boot and then it worked again....once... then the next disk I try Im back to square one.

I have also tried opening the disk from VLC but again just errors.

Any help would be gratefully received.

Thanks

PS - I have also tried using a Live CD and that began to boot up so I dont think its the drive gone Kaput.

---

### Post by coffeecat on 2011-07-26
> **Sylos said:**
> 
PS - I have also tried using a Live CD and that began to boot up so I dont think its the drive gone Kaput.

Ah, but did it finish booting up? 

If it sometimes works and sometimes doesn't I certainly would suspect failing hardware, but try this (with a disc in the optical drive):

```
udisks --mount /dev/sr0
```

---

### Post by Sylos on 2011-07-26
> **coffeecat said:**
> Ah, but did it finish booting up? 

If it sometimes works and sometimes doesn't I certainly would suspect failing hardware, but try this (with a disc in the optical drive):

```
udisks --mount /dev/sr0
```

Thanks for the post.

I didnt let it finish booting so I suppose you are right - it could still be the drive.

However, the anicdotes are now adding up to give a little more direction as to the cause.
The problem occurred again but was sparked off whilst using Acidrip. I finished ripping a disc and put in another. When I click "Load" acidrip becomes unresponsive and the problem begins. This latest time as soon as acid rip became unresponsive I opened up a terminal and did "eject /dev/sr0 and the disc pops out and I was able to just close the draw and it automounted again. Close acidrip and re-open it and away we go.

So the problem appears to begin with acidrip. I dont see how a problem with that app could cause such a wide ranging problem that persist outside of the prog itself. 
Im gonna try and keep probing it and see what happens. I suppose the sensible first move is to reinstall acid rip andsee if that helps. I will of course also try your command suggestion next time it happens.

Cheers

---

