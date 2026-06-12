---
title: "Recover files from possibly corrupt micro SD"
date: 2013-02-24
forum: Multimedia Software
---

### Post by TUOggy on 2013-02-24
I have a SanDisk 32gb class 10 microsd that I've been using in my phone. Yesterday, I kept getting this message that it was safe to remove. I checked it out when I got home. I can't mount it at all. Windows will not recognize that there's a card at all. When I try to mount in Ubuntu, it shows up as drive in disk manager, but I can't mount it. 

My question: Is there any way to recover the files on the card?

I tried PhotoRec, but the drive can't be found. Any other suggestions?

---

### Post by meteorrock on 2013-02-25
Yep. If you did not reformat your card you can recover it. If dd does not work in ubuntu try what others call "carving" tools for data recovery. Here is a link you can research as there are tons of free tools you can use for both linux and windows. Forensics wiki has a listing for you.  [http://www.forensicswiki.org/wiki/Tools%3aData_Recovery#Carving](http://www.forensicswiki.org/wiki/Tools%3aData_Recovery#Carving)

---

### Post by TUOggy on 2013-02-25
Yeah, I tried to use dd, parted, and gpart, but I keep getting errors when trying to access the drive.

```
$ sudo ddrescue -r 3 /dev/sdc /media/usbdrive/sd_backup/image /media/usbdrive/sd_backup/logfile
ddrescue: Can't open input file: No medium found 

```

```
$ sudo gpart /dev/sdc

*** Fatal error: open(/dev/sdc): No medium found.
```

---

### Post by fdrake on 2013-02-25
> **TUOggy said:**
> Yeah, I tried to use dd, parted, and gpart, but I keep getting errors when trying to access the drive.

```
$ sudo ddrescue -r 3 /dev/sdc /media/usbdrive/sd_backup/image /media/usbdrive/sd_backup/logfile
ddrescue: Can't open input file: No medium found 

```

```
$ sudo gpart /dev/sdc

*** Fatal error: open(/dev/sdc): No medium found.
```

install parted and show the output of the last command
```

sudo apt-get install parted
sudo parted -l

```
and then we can try with photorec

---

### Post by TUOggy on 2013-02-26
> **fdrake said:**
> install parted and show the output of the last command
```

sudo apt-get install parted
sudo parted -l

```
and then we can try with photorec

Doesn't recognize the micro sd, all I got are the two SSDs and my external.

```
Model: ATA RunCore 32G-C (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  29.9GB  29.9GB  primary   ext4            boot
 2      29.9GB  32.0GB  2136MB  extended
 5      29.9GB  32.0GB  2136MB  logical   linux-swap(v1)


Model: ATA ASUS-PHISON SSD (scsi)
Disk /dev/sdb: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  16.1GB  16.1GB  primary  ext3


Model: WD My Passport 070A (scsi)
Disk /dev/sdd: 499GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  499GB  499GB  primary  ntfs

```

---

### Post by TUOggy on 2013-03-04
Guess that means I'm SOL...

---

### Post by montgomeryj on 2013-03-05
[COLOR=#000000]Another option that you have depending on your technical abilities is to recover the data and information on your own. There is a tool called Autopsy which utilizes sleuthkit to explore crashed, erased hard drives as well as recover information from them. You can find information on how to download and install Autopsy (sleuthkit should install automatically) for windows and linux at [/COLOR][http://www.sleuthkit.org/autopsy/](http://www.sleuthkit.org/autopsy/)[COLOR=#000000]. I hope that this helps you out. Post here if you have any more questions in relation to those tools.[/COLOR]

---

### Post by Mark Phelps on 2013-03-06
Don't mean to be discouraging, but I have a Samsung SGS3 that trashes SD cards -- and I tried all the well-known Windows data recovery products (since the filesystem I used on the card was NTFS), and in ALL the cases, I was able to recover NOTHING from the two cards.  This surprised me because the same apps did great at recoverying hard drives.  My guess is that the MicroSD cards are just not so robust.

However, I switched over to using a Samsung MicroSD card -- and that has not failed since.

---

### Post by Zteam on 2013-03-07
Just try with photorec

---

### Post by TUOggy on 2013-03-08
> **montgomeryj said:**
> [COLOR=#000000]Another option that you have depending on your technical abilities is to recover the data and information on your own. There is a tool called Autopsy which utilizes sleuthkit to explore crashed, erased hard drives as well as recover information from them. You can find information on how to download and install Autopsy (sleuthkit should install automatically) for windows and linux at [/COLOR][http://www.sleuthkit.org/autopsy/](http://www.sleuthkit.org/autopsy/)[COLOR=#000000]. I hope that this helps you out. Post here if you have any more questions in relation to those tools.[/COLOR]

Thank you, I will try this tonight when I get home and let you know how it goes.

> **Mark Phelps said:**
> Don't mean to be discouraging, but I have a Samsung SGS3 that trashes SD cards -- and I tried all the well-known Windows data recovery products (since the filesystem I used on the card was NTFS), and in ALL the cases, I was able to recover NOTHING from the two cards.  This surprised me because the same apps did great at recoverying hard drives.  My guess is that the MicroSD cards are just not so robust.

However, I switched over to using a Samsung MicroSD card -- and that has not failed since.

Yeah, that was what I was thinking. Now I'm backing up all my photos now to the cloud, but there are a few I have on the old card that I'd like to recover as well. I'm keeping my fingers crossed.

> **Zteam said:**
> Just try with photorec

Tried it, same problem as the other tools.

Thanks for the advice though.

---

### Post by DirtyDroidX on 2013-04-30
I have a Samsung Galaxy Note 2, with a class 10 SanDisk SD card that was corrupted after a hard reboot. I noticed the card was acting up a few times in the past few weeks , with giving me RW problems and showing files. I usually back up frequently, but do to the fact of life I have not. We all know the personal information that we store on any storage device can mean the world to some of us. I do suggest keeping regular backups and using cloud based storage. Anyway so tried a windows machine, no go. Tried on my Ubuntu setup, no go. I did use gpart and finally with the use of testdisk 6.13 I was able to restore my data to my system then reformat the SD and was back in business  If you own a Samsung device I highly recommend backing up regularly because Samsung devices are known for eating cards, especially if you are using a different altered OS.

Thanks for the tips!

---

