---
title: "DVD Not working"
date: 2016-06-18
forum: Multimedia Software
---

### Post by wildbuttrueblue on 2016-06-18
Greetings,

Currently experiencing issues with my DVD, which was previously working.  Not sure when or why it ceased working, as I do not use it often.  Seems that the system recognizes it as indicated below.

OS Ubuntu 16.04

Have tried multiple Video and Audio CDs that work in other devices.  Appreciate any assistance in resolving this issue.  Thank you in advance.

```
sudo lshw -C disk
[sudo] password for kevin: 
  *-disk                  
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdb
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: logicalsectorsize=512 sectorsize=512 signature=7206c6f6
  *-disk
       description: ATA Disk
       product: Hitachi HTS54107
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: A4D0
       serial: J8430078G10YBC
       size: 698GiB (750GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=a7bb3853-5fec-4ba1-b301-9c0030565c1b logicalsectorsize=512 sectorsize=4096
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GU70N
       vendor: hp
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: U702
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```

---

### Post by TheFu on 2016-06-18
> experiencing issues with my DVD
is a little vague. Please be more specific.  Who is the maker? What software have you tried? What exact formats are the source discs?  Were any patches applied that would have impacted this?  

Please be specific.

> Previously working is also vague.  10 minutes before?  Last week?  Last month?  Before the last patches were applied? Before the last OS upgrade happened?  

Please help us to help you. Specifics help.

---

### Post by wildbuttrueblue on 2016-06-18
LOL  vague largely because I do not use it often.  Remember is was working on Ubuntu 14 and ceased.  Didn't have the time to pursue a solution at the time.  The only  patches that have been applied at those through the software updater include with Ubuntu.

Software?  The disks inserted were retail movie DVDs and music CDs.  When a disc is inserted can hear the drive 'cycling' but receive no prompts to indicate it is recognized by the system.  All the information I have about the DVD drive is that listed in my original post.  The vendor being HP - any suggestions on how to arrive at additional information on the drives, such as the maker requested in your post.  

the /home/cd directory is empty if that makes any difference.  Seems to me that it does, but has been many years since I worked with Unix.

Appreciate your time, assistance and patience.  Definitely I am not an experienced user in Ubuntu!

---

### Post by TheFu on 2016-06-18
If that is all the info you have about the drive, perhaps opening the case and looking for the real manufacturer as branded is needed?  I wouldn't do that yet, but there will be a vendor and part number there.

So - it worked at some point under 14.04, then it broke.  Then you updated the OS to 16.04?  Those are some fairly large steps.

What software are you using to playback the music?
What software are you using to playback the videos?

Did you load any required DRM modules for the playback to work?  
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28%28RestrictedFormats%7CPlayingDVDs%29%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28%28RestrictedFormats%7CPlayingDVDs%29%29)

I don't understand the /home/cd reference. Please explain.

---

### Post by wildbuttrueblue on 2016-06-18
LOL yeah not ready to go to that step yet!  Believe it is something in the OS config.  Installed VLC just to see what the outcome was in trying to place a disk and received the msg:

 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]
 [COLOR=#000000]
seems that perhaps something is missing or not configured correctly  ???

[/COLOR]

---

### Post by TheFu on 2016-06-18
Did you follow the instructions in the provided link?

---

### Post by QDR06VV9 on 2016-06-18
For 16.04 you will need to install "libdvd-pkg"
```
sudo apt-get install libdvd-pkg
```

Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss.

---

### Post by wildbuttrueblue on 2016-06-18
Thanks runrickus installing it now -  in the process of installing mscorefonts  ??? (part of the install?)

Prior to executing this install - I viewed my /etc/fstab which does not seem to have the CDROM listed - should it?  Will this install take care of that?

  ```
 # /etc/fstab: static file system information.
 #
 # Use 'blkid' to print the universally unique identifier for a
 # device; this may be used with UUID= as a more robust way to name devices
 # that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 # / was on /dev/sda2 during installation
 UUID=2f451d84-3222-462b-9c1d-85314a48a4c3 /               ext4    errors=remount-ro 0       1
 # /boot/efi was on /dev/sda1 during installation
 UUID=ABF2-0D3C  /boot/efi       vfat    umask=0077      0       1
 # swap was on /dev/sda3 during installation
 #UUID=7bde6408-0062-46a7-9322-a50165951d02 none            swap    sw              0       0
 /dev/mapper/cryptswap1 none swap sw 0 0
```


Thank you

---

### Post by gordintoronto on 2016-06-18
This really sounds like a hardware problem. It could be as simple as a cable coming loose, or the DVD drive has failed. A new drive costs about $20 these days.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204](http://www.newegg.com/Product/Product.aspx?Item=N82E16827135204)

(My only connection to Newegg is as a customer.)

---

### Post by TheFu on 2016-06-18
No need for CD/DVD lines in the fstab.
Did you read and follow the instructions in the first link I provided?

---

### Post by mc4man on 2016-06-18
The blue in the  line from your lshw, " configuration: ansiversion=5 [COLOR="#0000CD"]status=ready[/COLOR]" means a disk has been detected in the drive but no file system found.
This would be expected for blank media & audio cd's but not for data disks or dvd movies. So if that's what you're seeing on either of the later then the drive is the issue. It may have a dirty lens or may be broke.

---

### Post by wildbuttrueblue on 2016-06-19
yes I did and no change

---

### Post by coldraven on 2016-06-19
I had three brand new DVD movies and none would play. I cleaned the lens and two would play. I cleaned the lens again and all three would play. If you smoke and have pets you need to clean the lens regularly.

---

### Post by wildbuttrueblue on 2016-06-19
coldraven - had hoped it was going to be that for me, but not the case, had already cleaned it with the same results.  Did get the drive working for a 'second' last night.  Long enough to read the contents of the drive, but when I went to attempt to play the contents - it 'disappeared' from the system again.  Have not endeavoured yet to ts any further at this point in and time - am certain it is not the hardware or media though.  Hope I can get it to work again, long enough to ts before I do a clean re-install of the OS.

---

### Post by mc4man on 2016-06-19
> **wildbuttrueblue said:**
> Did get the drive working for a 'second' last night.  Long enough to read the contents of the drive, but when I went to attempt to play the contents - it 'disappeared' from the system again.  Have not endeavoured yet to ts any further at this point in and time - am certain it is not the hardware or media though.  Hope I can get it to work again, long enough to ts before I do a clean re-install of the OS.
The drive is shot

---

### Post by wildbuttrueblue on 2016-06-19
mcrman - might tend to agree did the drive not function properly when running from USB is 'demo.'  Am still not convinced that an entry is not required in fstab given some of the 'screams' from the OS during different ops.  Will likely do a clean install and just call it a day - hoping everything works as it should!

---

### Post by mc4man on 2016-06-20
> **wildbuttrueblue said:**
> mcrman - might tend to agree _did the drive not function properly when running from USB is 'demo._'  Am still not convinced that an entry is not required in fstab given some of the 'screams' from the OS during different ops.  Will likely do a clean install and just call it a day - hoping everything works as it should!
Must have missed you previously providing that little underlined  tidbit...

---

