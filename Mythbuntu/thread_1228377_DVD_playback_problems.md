---
title: "DVD playback problems"
date: 2009-07-31
forum: Mythbuntu
---

### Post by laffinet on 2009-07-31
Hi.

My DVD drive is driving me nuts.

It sort of works, but I do get problems here and there.

Here are a few examples of what's going on

1. DVD: Oz Season1 Disc1
Plays without a problem in myth and vlc
But, if I hit eject on the drive I get this error message:
> Failed to eject "/org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_216".
Given device "/org/freedesktop/Hal/devices/storage_model_DVD_RW__DVR_216" is not a volume or drive.

I can eject the DVD via right click->eject in thunar though

2. DVD: Grey's Anatomy Season4 Disc4
Doesn't play in vlc
Doesn't play in myth. When selecting "play DVD" in myth nothing happens at first, then black screen, have to kill frontend

Any ideas ?

---

### Post by jb5 on 2009-08-01
> **laffinet said:**
> 
1. DVD: Oz Season1 Disc1
Plays without a problem in myth and vlc
But, if I hit eject on the drive I get this error message:


I can eject the DVD via right click->eject in thunar though

Any ideas ?

From [here](http://www.uluga.ubuntuforums.org/showthread.php?t=1149489&highlight=hot+plugged) I found the following helped

under settings (Xfce 4 settings Manager)
Open up Removable drives and media
and under Storage
de-select Mount removable drives when hot plugged

This has cured my problem with failed to eject errors. (Certainly when I use the button on the drive itself to eject the disc). 

HTH

---

### Post by laffinet on 2009-08-02
Thanks for the suggestion, tried that, didn't change a thing :(

---

### Post by larsolav on 2009-08-03
Regarding issue no 2, the internal MythTV player seems to have difficulty playing certain DVDs and ripped ISO files. 

MythTV seems not to like Disney movies in particular, and will often stall at the first flash screen (either a black screen, or the FBI/copyright warning [somewhat ironic...]). And Grey's anatomy is on ABC, a Disney owned network...

For ISO files Mythbuntu 9.04 is set to use Xine as the player (at least that is what I saw after recently installing a 9.04 frontend, it was changed from internal player in 8.04). Maybe you can try the DVD using Xine, and if it works, set Xine as the default DVD player. Xine seems to handle Disney movies better than the MythTV internal player,

Cheers!

---

### Post by laffinet on 2009-08-03
Thanks for the reply.
I'm running 9.04, so have to check if it's using Xine ? I also tried playing it in vlc outside of myth, no luck there either.

---

### Post by larsolav on 2009-08-03
For DVD it is probably set up to use the internal player. You can see if Xine can play the DVD outside of myth. Xine seems to be the preffered dvd and/or iso player on this forum...

---

### Post by KillerKiwi on 2009-08-04
Every single time I have this issue its been because the drive hasn't had its region set

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes)

```

sudo apt-get install regionset
sudo regionset

```

Make sure you select the correct region code
[http://en.wikipedia.org/wiki/DVD_region_code#Region_codes_and_countries](http://en.wikipedia.org/wiki/DVD_region_code#Region_codes_and_countries)

---

### Post by larsolav on 2009-08-05
> **KillerKiwi said:**
> Every single time I have this issue its been because the drive hasn't had its region set

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes)

```

sudo apt-get install regionset
sudo regionset

```

Make sure you select the correct region code
[http://en.wikipedia.org/wiki/DVD_region_code#Region_codes_and_countries](http://en.wikipedia.org/wiki/DVD_region_code#Region_codes_and_countries)

I'm not sure the OP needs to do that. He is in Australia, and if they have not yet enacted their own version of the strict US DMCA anti circumvention laws, then he can legally download the deCSS plug-ins available for easy installation in MCC, and that issue becomes moot, I think...

Cheers!

---

### Post by KillerKiwi on 2009-08-05
> **larsolav said:**
> I'm not sure the OP needs to do that. He is in Australia, and if they have not yet enacted their own version of the strict US DMCA anti circumvention laws, then he can legally download the deCSS plug-ins available for easy installation in MCC, and that issue becomes moot, I think...

Cheers!

The issue is dsCSS wont work if the region is not set on some dvd players

Ill leave the legal issue to others

---

### Post by laffinet on 2009-08-08
> **KillerKiwi said:**
> 

```

sudo apt-get install regionset
sudo regionset

```


Tried that, here's what I get:
> ERROR: Could not open disc "/media/cdrom/"!
Please ensure there is a readable CD or DVD in the drive.

I've got a region 4 DVD in the drive that I can read with vlc, myth, thunar. 
My myth is set to use
```
/dev/sr0/
```
as the DVD drive. VLC is using that as well.

I tried
```
sudo regionset /media/cdrom/
```
and a few variations of this (/cdrom0/, /dev/sr0/, etc.), nothing works. However I can read *this* DVD just fine.
What is going on ???

---

### Post by Mister.Vash on 2009-08-10
If you insert a dvd, then type in
```
mount
```
it should all your mounted volumes along with the dvd drive.  The dvd line should look similar to the following:
**/dev/scd0** on /media/cdrom0 type udf (ro,noexec,nosuid,nodev,user=user)

then just take that output and try the regionset again

You might also want to make sure that the disc you insert is one of the ones that does play correctly in vlc just to make sure that the system is correctly able to mount the device

---

### Post by laffinet on 2009-08-11
:confused::confused::confused:

I've got a dvd in the drive that I can read (vlc is open and the dvd is playing), here's the output from "mount"
> /dev/sdb1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb6 on /var/lib type xfs (rw)
/dev/sda1 on /var/lib/mythtv/drive2 type xfs (rw,nodiratime,relatime)
/dev/sdc1 on /var/lib/mythtv/drive3 type xfs (rw,nodiratime,relatime)
securityfs on /sys/kernel/security type securityfs (rw)


Am I missing something ? I can't see a dvd drive :confused:

---

### Post by Mister.Vash on 2009-08-11
That seems a little odd - not sure why it wouldn't show but you would be able to play it in vlc

Could you post the output of:
```
sudo lshw -class disk
```

and:
```
cat /etc/fstab
```

---

### Post by laffinet on 2009-08-12
>   *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RW  DVR-216
       vendor: PIONEER
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/dvd2
       logical name: /dev/dvdrw2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.09
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom2
  *-disk:0
       description: ATA Disk
       product: WDC WD6400AAKS-2
       vendor: Western Digital
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WMASY5389531
       size: 596GiB (640GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0004d2b5
  *-disk:1
       description: ATA Disk
       product: WDC WD3200AAKS-0
       vendor: Western Digital
       physical id: 2
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 01.0
       serial: WD-WMAT13641885
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000ef831
  *-disk:2
       description: ATA Disk
       product: WDC WD10EAVS-00D
       vendor: Western Digital
       physical id: 3
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 01.0
       serial: WD-WCAU4A101469
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000e603f



> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=104ad978-dbcf-4b0c-a891-9b1e41f84d48 /               ext3    errors=remount-ro 0       1
# /var/lib was on /dev/sda6 during installation
UUID=c1bf6f10-b62a-442e-84f1-8b5c4114baa1 /var/lib        xfs     defaults        0       2
# swap was on /dev/sda5 during installation
UUID=85889bee-ae54-4552-8d2f-f8638eb98f80 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=f542cc0a-6b1b-43d2-8fe6-ffe2e9a2e31a /var/lib/mythtv/drive2        xfs     defaults,relatime,nodiratime        0       2

# /dev/sdc1
UUID=fe9f6183-2ea8-4b9e-9d1f-e13840faa92b /var/lib/mythtv/drive3        xfs     defaults,relatime,nodiratime        0       2


Hm, looks like my dvd drive is /dev/cdrom2, for whatever reason.

I tried 

```
sudo regionset /dev/cdrom2
``` and that worked, however that wasn't the solution to my original problem since the region code was already set. So still no luck there.

Also confused as to why the drive doesn't show up with "mount"

---

### Post by Mister.Vash on 2009-08-12
Your fstab shows some difference in that it references cdrom0 - we could change that to cdrom2, but lets try something else instead.

My guess is that at one point you upgraded the dvd drive in the system?  Let's try getting your DVD drive to show up as /dev/cdrom instead of /dev/cdrom2 

As a backup, copy over the file /etc/udev/rules.d/70-persistent-cd.rules to your home folder.

After doing that, edit the file
```
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```
You want to keep all the commented lines ( those that start with the hash sign # ) and remove everything else from the file.  Save the file and restart your system.  

When you restart, that file should be populated automatically, and at that point you should hopefully see /dev/cdrom

If it doesn't work, replace the file with the backup copy

If it does, check and see if the mount command shows the drive and mounted, and then check and see if the disks play, both the one that was working before and the one that wasn't

---

