---
title: "SD Card problem"
date: 2009-02-13
forum: Multimedia Software
---

### Post by Soepstengel on 2009-02-13
Hello all,


I have a problem reading an SD Card from a friend. He told me that he can't read/write to it anymore and that his Windows XP installation won't recognize it anymore.

When I insert it into my computer it isn't mounted automatically. The output of dmesg shows:

**dmesg**
```
mmc0: error -110 whilst initialising SD card
```

I get the same message, that message, every time I put it in the SD slot. I believe the -110 stands for a time-out, if I remember correctly (correct me if i'm wrong). The output of fdisk -l is:

**fdisk -l**
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe588e588

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9915    79642206   83  Linux
/dev/sda2   *        9916       13995    32772600    7  HPFS/NTFS
/dev/sda3           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris
```

It doesn't show any other device then /dev/sda, which is my harddrive and only drive connected. I tried *ddrescue* to try to read data from it (if that's even possible), but I don't really know what the location of the SD card is ("/dev/etc..").

Bottomline: I have a SD Card which I think (i'm still a beginner tho) is damaged, but I would like to know if theres some way to read data from it? I would be really thankful.

---

### Post by surj08 on 2009-02-13
i would check to see if the "read only" switch on the card is on. Just a guess linux might be trying to mount in RW when its RO.

Also a newbie btw so im not sure.

---

### Post by mc4man on 2009-02-13
I believe if there is no partition/volume or a recognizable one, then fdisk won't see anything

With the card inserted run 
```
sudo lshw -C disk
```

or start up (if installed) the partition editor (gparted

---

### Post by Bablefish on 2009-02-13
It's just a bug within the Ubuntu OS, it just can't read SD Cards. I heard if you get one of those SD Card to USB adaptors or even get one of those SD Cards with a USB already on it. I heard those do work.

---

### Post by mc4man on 2009-02-13
Well i have no problem reading or writing to sd cards in 8.10.

while I never tried to format/partition one in ubuntu a quick look shows that fdisk, lshw and gparted wll not find the card (using internal reader.

However this does (went ahead and formatted it (note it is  a little 16Mb that came with a camera, previously formatted in windows to vfat (fat16 volume label 'TEST'

> doug@doug-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             75443008   2784476  68826228   4% /
tmpfs                   256632         0    256632   0% /lib/init/rw
varrun                  256632       104    256528   1% /var/run
varlock                 256632         0    256632   0% /var/lock
udev                    256632      2732    253900   2% /dev
tmpfs                   256632       476    256156   1% /dev/shm
lrm                     256632      2000    254632   1% /lib/modules/2.6.27-7-generic/volatile
/dev/mmcblk0p1           14512      7680      6832  53% /media/TEST
................ unmounted sd card manually...................
doug@doug-laptop:~$ mkdosfs /dev/mmcblk0p1
mkdosfs 2.11 (12 Mar 2005)


Now df shows this (the format was successful
> 
/dev/mmcblk0p1           14484         2     14482   1% /media/disk

Re edit 
Though if the card doesn't mount then using df will be of no value. (won't show
What one could try in that case is to look in /dev for a mmcxxxxx to get the /dev/ of the card and then use that to format it. (if formatting the card was the only way to make useful
I'm not sure if something like testdisk could repair or retrieve the data (assuming you could find the /dev/ of the card

---

### Post by Soepstengel on 2009-02-13
Thank you all for the quick replies!

I will answer them tomorrow night, this is just a quick "thank you" message.

---

### Post by Soepstengel on 2009-02-16
Thank you all for your replies. I read them all and tried all the possible solutions you gave me. The results and my comments on them are posted in this message.

> i would check to see if the "read only" switch on the card is on. Just a guess linux might be trying to mount in RW when its RO.
I checked that. The SD card has a lock switch, but it's in not-locked mode.

The output for **sudo lshw -C disk** recognizes my hard-disk and my DVD player, but not the SD card. GParted only shows my hard-disk and also not the SD card. The output:
>   *-disk                  
       description: ATA Disk
       product: Hitachi HTS54161
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SBDO
       serial: SB3D0YE5G1ZPMA
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=e588e588
  *-cdrom
       description: DVD-RAM writer
       product: CD/DVDW TS-L632D
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: AS05
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

> It's just a bug within the Ubuntu OS, it just can't read SD Cards. I heard if you get one of those SD Card to USB adaptors or even get one of those SD Cards with a USB already on it. I heard those do work.
I tried two other SD Cards and I can read and write files on both on them. So my card reader works and it's possible in my Ubuntu installation (8.10).

The command **df** shows as output:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             78391844  48277404  26132332  65% /
tmpfs                  1036336         0   1036336   0% /lib/init/rw
varrun                 1036336       304   1036032   1% /var/run
varlock                1036336         0   1036336   0% /var/lock
udev                   1036336      2812   1033524   1% /dev
tmpfs                  1036336        12   1036324   1% /dev/shm
lrm                    1036336      2004   1034332   1% /lib/modules2.6.27-11-generic/volatile

I opened the location */dev* using **gksudo nautilus** (I thought that maybe if I run it as root I get to see more) and checked the whole folder but there is no */dev/mmc** or */dev/sd** or things which look like a removable card.

Again, thank you all, but unfortunately I can't read data from the card yet. Is it broken/unfix-able? If anyone has any idea's, I'd love to hear them. Thank you.

---

### Post by russu52 on 2009-02-16
if you have a pc on win xp (don't like saying this, but have to):
insert sd card into pc running win xp.

go to: > control panel 
> administrative tools
> computer managment
> disk managment

gives you a list of all media. there could be a conflict in drive letter assigned to sd card (with optical drive e.g. E:) 

in that case change drive letter. you can also format sd card over there.

---

### Post by Soepstengel on 2009-02-19
> **russu52 said:**
> if you have a pc on win xp (don't like saying this, but have to):
insert sd card into pc running win xp.

go to: > control panel 
> administrative tools
> computer managment
> disk managment

gives you a list of all media. there could be a conflict in drive letter assigned to sd card (with optical drive e.g. E:) 

in that case change drive letter. you can also format sd card over there.

Thank you for your reply. I installed Windows XP on the same laptop (to verify that the SD Card reader works and that it's not a hardware problem in the laptop), but Windows XP doesn't recognizes it at all. So there's no way that I can read the data or even format the card.

I think it's really broken. If anyone has an idea, I'd love to hear them. Thanks.

---

### Post by fishyf on 2009-03-02
> **Soepstengel said:**
> 

I think it's really broken. If anyone has an idea, I'd love to hear them. Thanks.

Well, I had exactly the same problem. It was actually a microSD card in an SD package. I rearranged the microSD card within the SD package and it worked.

So it might work if you clean the contacts. Or it might be that an internal connection is broken. There is a small possibility that if you place it firmly in the slot or if you apply a small bit of pressure to the card that it will work.

---

### Post by sinbin on 2010-08-16
I've had a similar problem as described by Soepstengel & fishyf

I was using my LG Mobile phone to take photos. The photos were saved to a 2GB microSD card. I wanted to look at some of the photos on my laptop so I took the microSD card out of the phone and put it in an integral microSD adapter. I inserted the integral microSD adapter in my laptop and could view the photos perfectly. I deleted a few of them.

Then when I put the microSD card back in the phone the LG phone could not see it. It kept saying "no external memory card." When I put the microSD card in a Nokia phone it sees the card but says it's locked and asks for a password. When I put the microSD card back in by laptop using the adapter nothing happens.

I am running 10.04 and other microSD cards work fine on my laptop using the adapter and in the 2 mobile phones. Also the lock switch on the side of the adapter is in the unlocked position. Changing the position of the switch makes no difference.

Is this problem to do with linux file type being ext4 and microSD being FAT?

I posted a thread in Hardware & Laptops section: [http://ubuntuforums.org/showthread.php?t=1551653](http://ubuntuforums.org/showthread.php?t=1551653) but have had no replies in 4 days. Hoping I might have better luck here. Any help is really appreciated

---

### Post by Soepstengel on 2010-08-16
> **sinbin said:**
> I've had a similar problem as described by Soepstengel & fishyf

I was using my LG Mobile phone to take photos. The photos were saved to a 2GB microSD card. I wanted to look at some of the photos on my laptop so I took the microSD card out of the phone and put it in an integral microSD adapter. I inserted the integral microSD adapter in my laptop and could view the photos perfectly. I deleted a few of them.

Then when I put the microSD card back in the phone the LG phone could not see it. It kept saying "no external memory card." When I put the microSD card in a Nokia phone it sees the card but says it's locked and asks for a password. When I put the microSD card back in by laptop using the adapter nothing happens.

I am running 10.04 and other microSD cards work fine on my laptop using the adapter and in the 2 mobile phones. Also the lock switch on the side of the adapter is in the unlocked position. Changing the position of the switch makes no difference.

Is this problem to do with linux file type being ext4 and microSD being FAT?

I posted a thread in Hardware & Laptops section: [http://ubuntuforums.org/showthread.php?t=1551653](http://ubuntuforums.org/showthread.php?t=1551653) but have had no replies in 4 days. Hoping I might have better luck here. Any help is really appreciated

Hello mate. I didn't managed to fix my SD card and pronounced it dead. I'm not really familiar with file systems (besides the basics) and SD card troubleshooting (hence I opened this thread).

I wish you good luck in solving your problem and hope that you manage to do so but I can't help you. I also hope that people who read this thread can give you more information.

---

### Post by sinbin on 2010-08-18
Thanks for the above reply ;)

Here's hoping someone can help

---

