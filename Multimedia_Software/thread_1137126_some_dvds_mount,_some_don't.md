---
title: "some dvds mount, some don't"
date: 2009-04-25
forum: Multimedia Software
---

### Post by vividia on 2009-04-25
I'm still running Intrepid and have dealt with this for some time.  Most DVDs mount themselves automatically.  I have libdvdcss.  Sometimes I can eject the disc, close the tray with it still on there and do this repeatedly until the disc "catches" and mounts.  There are some that are just plain stubborn.  I've tried manually mounting but come up empty.

Any ideas?

Viv

---

### Post by vividia on 2009-04-27
bump

---

### Post by VMC on 2009-04-27
So you open the DVD tray, place a DVD movie disc on the try. Close the try. then what happens? Do you see and light, hear any motor noise coming from the DVD? What output do you get from the mount command?

---

### Post by vividia on 2009-05-14
you I see a light.  the tray is active.  I hear motor sounds like its trying to read it.

---

### Post by vividia on 2009-06-16
All right.  problem is now really bad.  I'd say 75% of the commercial DVDs I put in DO NOT mount.  The drive attempts to read the disk multiple times before giving up.  Some disks do mount and play without a hitch.  But there are some that will not mount at all and I have tried numerous times.

I have tried reinstalling sources to get this back up and going.  But since some disks work and most don't, I think this is something else.

Help!!!  Please.

---

### Post by vividia on 2009-06-16
Oh yeah.  I tried manually mounting it.

misha@misha-laptop:~$ sudo mount /media/cdrom0/ -o unhide
[sudo] password for misha: 
mount: No medium found
misha@misha-laptop:~$

---

### Post by mc4man on 2009-06-16
What you're describing sounds like a dirty  or dying drive.
Try inserting one of your 'problem' disks (assuming a commercial dvd), wait till the activity dies down and run

```
sudo lshw -C disk
```

See what it says on the line "configuration:"  for *-cdrom

---

### Post by pauna on 2009-06-16
Ok, I know this is far fetched, but is there a general DVD mounting/playback problem around?

[LIST=1]
[*]The original poster has mounting issues. 
[*]I also have DVD issues in my MythBuntu (Hardy based) box. See [http://ubuntuforums.org/showthread.php?t=1148774](http://ubuntuforums.org/showthread.php?t=1148774) for details.
[*]The poster at [http://ubuntuforums.org/showthread.php?t=1183710](http://ubuntuforums.org/showthread.php?t=1183710) has DVD mounting issues.
[/LIST]

---

### Post by vividia on 2009-06-16
> **mc4man said:**
> What you're describing sounds like a dirty  or dying drive.
Try inserting one of your 'problem' disks (assuming a commercial dvd), wait till the activity dies down and run

```
sudo lshw -C disk
```

See what it says on the line "configuration:"  for *-cdrom

I really hadn't thought of it being dirty.  So I ran a lens cleaning disk through it.  Then slapped a commercial DVD in, waited like you said and ran the command.

> misha@misha-laptop:~$ sudo lshw -C disk
[sudo] password for misha: 
  *-disk                  
       description: ATA Disk
       product: Hitachi HTS54161
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SB4O
       serial: SB0442SJCB6YSH
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=aef4153a
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-T20N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: WG02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom


---

### Post by vividia on 2009-06-16
> **pauna said:**
> Ok, I know this is far fetched, but is there a general DVD mounting/playback problem around?

[LIST=1]
[*]The original poster has mounting issues. 
[*]I also have DVD issues in my MythBuntu (Hardy based) box. See [http://ubuntuforums.org/showthread.php?t=1148774](http://ubuntuforums.org/showthread.php?t=1148774) for details.
[*]The poster at [http://ubuntuforums.org/showthread.php?t=1183710](http://ubuntuforums.org/showthread.php?t=1183710) has DVD mounting issues.
[/LIST]

I don't know.  I'm guessing if there is something to go wrong in ubuntu the mounting of disks would be the most finicky.  I think that it may be a dirty/dying drive as the previous poster suggested.  At least in my case.  Its in a laptop and has seen a ton of use.

---

### Post by mc4man on 2009-06-16
> configuration: ansiversion=5 status=ready
*-medium
physical id: 0
logical name: /dev/cdrom 

That's indicating that media has been detected (status=ready), but no filesystem found.
You'd see the same thing for blank media or an audio cd (audio cd's have no filesystem to mount, they're accessed at a location

For a dvd (or any data dvd disk) then you'd expect something like this
> configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted


Considering the 'works for some disks' or works sometimes after repeated attempts the issue is most likely the drive itself. (you can't mount what is in essence not there.

Edit:
other factors that would affect older drives is the condition of the disk and the quality of it to begin with.
 I think overall the quality of commercial dvd's has gone down, possibly due to price  pressures and an attempt to maximize profits from it's (dvd format) remaining lifetime.

---

### Post by vividia on 2009-06-26
Well, thanks for the info.  I've now been dealing with a disk that won't UNmount!  rebooting works there but still... :confused:

---

### Post by k3lt01 on 2009-06-28
I have a similar problem with a particular dvd. It wont mount on my Desktop or laptop, the desktop has 2 dvd drives yet it will play on my tv's dvd player, my fathers Ubuntu laptop and my sisters XP Acer that is the exact same model as mine.

I don't believe it is a drive problem, 3 drives on 2 machines seems out of the bounds of normal probability.

---

### Post by pseudocube on 2010-11-24
Hello, I'm having the same sort of issue. When a DVD has been inserted:
```
user@user-desktop:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: WDC WD800JB-00JJ
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WCAM93944174
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ef2aef2a
  *-cdrom
       description: DVD writer
       product: DRW-6S160H
       vendor: DVDRW
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: CSG4
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

```
Like the OP, this only happens for some disks.

---

### Post by simormate on 2011-01-11
bump.

---

### Post by mc4man on 2011-01-11
> **simormate said:**
> bump.

Not sure what you're bumping - so.

If lshw shows nodisc or tray open then there's not much you can do, can't mount or access nothing.

If it shows ready then you could do 2 things
Create a mountpoint if one doesn't exist, then mount from cli
ex.
sudo mount /dev/sr0 /media/cdrom0

Or
A dvd doesn't need to be mounted to playback (or rip), just point your player to the device
Ex.
open vlc, - media - Open disk -  set vlc to use /dev/sr0 or /dev/sr1, ect.
It will then be played back fine.
(and when done no need to use sudo umount to unmount before ejecting the disk, just use button on drive.

---

### Post by BicyclerBoy on 2011-01-11
To solve most DVD problems you need the latest libdvdnav etc but the *buntu packages are to old. 

The best players have the latest builds/patches of the libdvdnav & read etc.
You need to compile or find 3rd party ppa.

Players:
mplayer
MythTV 0.24

or access via
HandBrake
makeMKV

You will need to build VLC from source.
note: VLC is the hosting website for some of the DVD access libraries.

---

### Post by simormate on 2011-01-13
Thank you for your answers!
> **mc4man said:**
> 
If lshw shows nodisc or tray open then there's not much you can do, can't mount or access nothing.

If it shows ready then you could do 2 things
Create a mountpoint if one doesn't exist, then mount from cli
ex.
sudo mount /dev/sr0 /media/cdrom0

Or
A dvd doesn't need to be mounted to playback (or rip), just point your player to the device
Ex.
open vlc, - media - Open disk -  set vlc to use /dev/sr0 or /dev/sr1, ect.
It will then be played back fine.
(and when done no need to use sudo umount to unmount before ejecting the disk, just use button on drive.

Actually, I don't want to mount it, just watch the contents. But when i insert it, it does not appear in my Places menu, it cannot be opened by vlc, nor mplayer.

lshw shows "ready"

> **BicyclerBoy said:**
> To solve most DVD problems you need the latest libdvdnav etc but the *buntu packages are to old. 

The best players have the latest builds/patches of the libdvdnav & read etc.
You need to compile or find 3rd party ppa.

Players:
mplayer
MythTV 0.24

or access via
HandBrake
makeMKV

You will need to build VLC from source.
note: VLC is the hosting website for some of the DVD access libraries.

I tried opening it with smplayer, but it did not work.

---

### Post by BicyclerBoy on 2011-01-13
You need a 3rd party ppa of MythTV0.24 or mplayer or VLC.
Just trying another old repos player isn't going to cut it..

Some DVDs take 2 insertions & couple of minutes to crack the css.
IMO Some optical drives should be avoided because the firmware can not be 'upgraded' in Linux or at all.

With MythTV 0.24:
And dozen new release DVDs no problems so far.

---

### Post by mc4man on 2011-01-13
> lshw shows "ready"
could you post that, only care about the *-cdrom: section(s)

---

### Post by simormate on 2011-01-14
> **BicyclerBoy said:**
> You need a 3rd party ppa of MythTV0.24 or mplayer or VLC.
Just trying another old repos player isn't going to cut it..

Some DVDs take 2 insertions & couple of minutes to crack the css.
IMO Some optical drives should be avoided because the firmware can not be 'upgraded' in Linux or at all.

With MythTV 0.24:
And dozen new release DVDs no problems so far.

the dvd i am trying to play is from 2002, i burnt it from an iso file, but i don't remember if i used this computer for it. it can be read by a laptop which is 2-3 years older than mine. it is a double layer dvd, i dont know if that counts.

> **mc4man said:**
> could you post that, only care about the *-cdrom: section(s)

*-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-T20N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: WW01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

---

### Post by BicyclerBoy on 2011-01-14
That DVD drive has a fairly bad track record...
Slimline & slow.
Could just be the drive is stuffed.

Have you considered a firmware upgrade.
This can get rid of the rip-stop feature etc..

Old optical drives don't always work with new media without firmware upgrade.

Firmware upgrades sometimes require windoze in safe mode IDE mode SATA.

---

### Post by simormate on 2011-01-14
> **BicyclerBoy said:**
> That DVD drive has a fairly bad track record...
Slimline & slow.
Could just be the drive is stuffed.

Have you considered a firmware upgrade.
This can get rid of the rip-stop feature etc..

Old optical drives don't always work with new media without firmware upgrade.

Firmware upgrades sometimes require windoze in safe mode IDE mode SATA.

The drive reads cds and other dvds. I don't know how to make a firmware upgrade, as I don't have windows.

Any other ideas?

---

### Post by simormate on 2011-01-14
> **BicyclerBoy said:**
> That DVD drive has a fairly bad track record...
Slimline & slow.
Could just be the drive is stuffed.

Have you considered a firmware upgrade.
This can get rid of the rip-stop feature etc..

Old optical drives don't always work with new media without firmware upgrade.

Firmware upgrades sometimes require windoze in safe mode IDE mode SATA.

ok, but how do i update firmware if i dont have windows?

---

### Post by BicyclerBoy on 2011-01-14
I think there are linux tools for flashing firmware for LG & Liteon.

Another problem is that most windoze installations will not boot in IDE mode if the install was done AHCI.

There are 3rd party firmware for some of these as well.
You need to be sure of the exact hardware inside the drive.

CDFreaks is the best web resource.

It might be easier to buy a new optical drive that is known work & recommended.

Are you using this drive in a laptop or some other odd hardware ?

---

### Post by simormate on 2011-01-14
> **BicyclerBoy said:**
> I think there are linux tools for flashing firmware for LG & Liteon.

Another problem is that most windoze installations will not boot in IDE mode if the install was done AHCI.

There are 3rd party firmware for some of these as well.
You need to be sure of the exact hardware inside the drive.

CDFreaks is the best web resource.

It might be easier to buy a new optical drive that is known work & recommended.

Are you using this drive in a laptop or some other odd hardware ?

unfortunately i did not understand anything from the first part of your comment. i googled for firmware, but did not find anything, but on the site it says it reads double-layer dvd-s. the dvd is from 2002, my laptop is from 2009, so i doubt that it is a compatibility problem.

---

### Post by BicyclerBoy on 2011-01-14
So more information..
The optical drive dates from 2007.

Is the problem DVD a stamped/bought disk or home made ?

Is it DVD-RW ?

-RW is much more difficult to read back. Not all media is created equal.
DL writers (& media) are not as reliable as single layer. 

Read the DVD on another PC ? 
Copy the DVD on another PC to USB stick or new media..

---

### Post by BicyclerBoy on 2011-01-14
..

---

### Post by simormate on 2011-01-14
> **BicyclerBoy said:**
> ..

it's home-made, dvd-r disc. it does work on another pc, but i would like it to work on mine:-?

---

### Post by mc4man on 2011-01-14
A few things - 
your drive, as noted, has a history of being inconsistent - nothing much to be done about that if that's the cause.

Your currently using firmware WW01, even if you could find an update suitable for that exact drive it's likely to be of no help. (flash with the wrong firmware and your drive is likely bricked

you mentioned the disk was a dual layer burned, then said dvd-r. No matter really, though if a dl-r then those are mostly junk, I'd only  use  dl +r's (and for those only verbatim. preferably made in singapore

Any way the the disk type (mediacode), condition and drive may all be factors - if you can't play it then you can't play it.
Because media is seen, even though unmounted you can try to play back and or mount and try to play. If no go then you could try to rip.

To directly try in vlc - from terminal
```
vlc dvd://
```

if you wished to try manually mounting
```
sudo mkdir /media/test
sudo mount /dev/sr0 /media/test
```
Then with vlc
```
vlc dvd:///media/test
```
To unmount 
sudo umount /media/test

Otherwise I rip it to an iso and try to play and or reburn a dl or rip to file and split into dvd5's
dvdisaster would work well there for an .iso (can be used  to recover unreadable sectors if any

---

### Post by simormate on 2011-01-18
> **mc4man said:**
> A few things - 
Because media is seen, even though unmounted you can try to play back and or mount and try to play. If no go then you could try to rip.

To directly try in vlc - from terminal
```
vlc dvd://
```


In fact, I don't see any signs that the media would be seen. Vlc gives this for the above command: 
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
[0x963c57c] dvdread demux error: DVDRead cannot open source: /dev/dvd
[0x963929c] main input error: open of `dvd://' failed: (null)

Time to give up?

---

### Post by sourchier on 2011-01-24
Did you try all the tips mentioned in the "Media Guide". You can find that here: [http://ubuntuforums.org/showthread.php?t=766683&highlight=libdvdcss]("http://ubuntuforums.org/showthread.php?t=766683&highlight=libdvdcss")

---

