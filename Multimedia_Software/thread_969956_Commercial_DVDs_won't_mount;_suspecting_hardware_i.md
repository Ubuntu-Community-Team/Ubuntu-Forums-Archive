---
title: "Commercial DVDs won't mount; suspecting hardware issue"
date: 2008-11-03
forum: Multimedia Software
---

### Post by Silver Streak on 2008-11-03
I have attempted to play several commercial DVDs on my system (HP Pavilion zv6000 with 8.10), and I can't even get the disk to properly mount. I have installed all the necessary packages from Medibuntu (libcss2, libdvdread3, etc.) and yet no DVD will successfully mount and/or play. I have tried manually setting both VLC and Totem to play from its hardware address according to lshw (/dev/cdrom). The drive in question is a combo DVD/RW and CD/RW laptop DVD drive. I have successfully gotten DVD playback to work in earlier versions of Ubuntu. I checked previously installed kernels, and none of them allow me to mount or play back said DVDs. 

This is just one particular "show-stopping" regression that's been bothering me a lot (along with gamepads being mis-detected, MTP devices losing functionality in Rhythmbox.. But that's for another thread)

---

### Post by mc4man on 2008-11-03
That would be /dev/dvd though probably a moot point.
If you were to place a dvd in the drive and run 
sudo lshw -C disk

Does the output show any indication of a file system being found?
If not no amount of libs or codecs, players will help playback of what's not there.

Can you play an audio cd or access any kind of data disk?

I happen to have the same laptop sitting on the shelf. (hinges broke after about 18 months, power cord wore thru at connector breaking ground. If i jimi rig the cord with a small nail and electric tape it'll charge up in about an hr. I'll throw 8.10 on it and see if it works.

---

### Post by Silver Streak on 2008-11-03
```
  *-cdrom
       description: DVD writer
       product: DVD-RW GCA-4080N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 0C35
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```

The hardware itself is obviously being recognized, but the disk is still not properly mounting. One odd thing though: the first Lord of the Rings DVD will successfully mount and play, but I believe that has to do with how the DVD is laid out (it has some extra software you can run if you're running Windows). All other DVDs have failed up to this point.

I've also been having problems burning DVDs as well. I burned an MP3 (data) CD yesterday, so that's not crippled. The strange part is that I can no longer read the MP3 CD, even though it's a valid disk, having checked it in my car's MP3 CD player.

I haven't read about any widespread failure of CD/DVD drives reading, which is odd...

By the way, if you do install 8.10, don't use the volume buttons: there's another bug that will cause the keyboard to lock when pressing some of the multimedia keys that don't send keyup events.

---

### Post by mc4man on 2008-11-03
This is what you'd want to see with a dvd in the drive
> *-cdrom:0               
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted

I'll install 8.10 once the battery is charged.

You could run dmesg | tail and see if anything interesting is shown or ck. your logs.

grep 'CD-ROM' /var/log/kern.log and grep 'DMA' /var/log/kern.log 
will pull up some info as will
grep 'hal' /var/log/debug

---

### Post by mc4man on 2008-11-04
Well everything works fine, exact same dvd drive make and model (DVD-RW GCA-4080N0)
Was playing dvds in a min or so, no issues.
That eliminates the laptop hardware per se, sorta points to your drive being the issue. 

Pm me if you want this hardware, i've got no use for it.

---

### Post by brancheb on 2008-11-16
I'm having the same problem.  My machine had a Samsung SH-S202 DVD writer that worked fine under Hardy Heron.  Suspecting it was a hardware problem, I replaced the drive with the exact same model.  No joy.  I suspect that something got broken between Heron and Ibex.


P.S.:  Did a fresh installl of Hardy Heron, reloaded my codecs, and it's all good.

---

