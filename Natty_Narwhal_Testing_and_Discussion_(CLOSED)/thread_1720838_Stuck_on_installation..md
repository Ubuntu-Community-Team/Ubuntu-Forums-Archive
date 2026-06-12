---
title: "Stuck on installation."
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by X82 on 2011-04-03
Watching the progress of Ubuntu 11.04, I decided to download the beta and try it out on my PC. 

I have 3 physical drives all SATA. One for Win 7, one for my documents/music etc and one as a backup for my other files.
Using windows 7, I partitioned my Win7(250gb) drive and allocated 100gb as a partition so Ubuntu could use it.
However, when I pop in the Ubuntu disk, restart and try to install Ubuntu, If I click the option which lets it work side by side with Win7, the only hard drive it will allow me to install to is my documents drive which is 1.5tb.
My windows 7 drive or even the backup drive are not an option. Why?
If I try to manually install it, it shows all my drives but not the partitions.
Its showing some fat32 partitions ( I have none). And for my windows 7 drive, it shows 100mb fat32 and 240gb free. Which there ISNT. Since I know Win7 is installed on that drive.

I cant even get past this point to even try out Ubuntu.
Any suggestions?

---

### Post by Dutch70 on 2011-04-03
When you boot up the live cd/usb, select "Try Ubuntu" instead of install. We can get more info from there. 

Also, if you have more than one hard drive, it's best to unplug the ones you're not installing Ubuntu onto. There very easy to unplug, and it makes things easier and leaves less room for error.

---

### Post by Hedgehog1 on 2011-04-03
> **X82 said:**
> Watching the progress of Ubuntu 11.04, I decided to download the beta and try it out on my PC. 

I have 3 physical drives all SATA. One for Win 7, one for my documents/music etc and one as a backup for my other files.
Using windows 7, I partitioned my Win7(250gb) drive and allocated 100gb as a partition so Ubuntu could use it.
However, when I pop in the Ubuntu disk, restart and try to install Ubuntu, If I click the option which lets it work side by side with Win7, the only hard drive it will allow me to install to is my documents drive which is 1.5tb.
My windows 7 drive or even the backup drive are not an option. Why?
If I try to manually install it, it shows all my drives but not the partitions.
Its showing some fat32 partitions ( I have none). And for my windows 7 drive, it shows 100mb fat32 and 240gb free. Which there ISNT. Since I know Win7 is installed on that drive.

I cant even get past this point to even try out Ubuntu.
Any suggestions?

The beta is not really ready for anyone other than advanced Ubuntu users who are doing bug reports.

The install is one area where some bugs exists (although in your case I don't think that the install bugs have anything to do with your issue, you never got to them).

If you **REALLY** want to install the beta, Dutch70 and I can show you how.  But it is **not ready for prime time just yet**, and I would **hate for you to get a bad impression** of Ubuntu because you were **trying unfinished software**.

But, if after all that **bold type** you still want to, please do this so we can get you installed:

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by X82 on 2011-04-03
I feel guilty for wasting time, as reading your last post, I realise that going from not using Ubuntu in years to leaping on a beta, is a bad move on my part.
I shall install version 10 and see how I progress. Maybe the problem will happen again..

Sorry to have wasted peoples time. No doubt I will be posting more here as what I know about Ubuntu isn't worth knowing. 
Thanks again.

---

### Post by Hedgehog1 on 2011-04-03
>  And for my windows 7 drive, it shows 100mb fat32

Actually, there is.  Windows hides it from you.  It is a tiny-tiny boot partition that Windows 7 always installs.

You will learn a lot about partitions and partition maps once you start dual-booting (with either the beta or the finished 11.04).  It is a fun learning experience.  ***Feed your inner nerd!***


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-03
> **X82 said:**
> I feel guilty for wasting time, as reading your last post, I realise that going from not using Ubuntu in years to leaping on a beta, is a bad move on my part.
I shall install version 10 and see how I progress. Maybe the problem will happen again..

Sorry to have wasted peoples time. No doubt I will be posting more here as what I know about Ubuntu isn't worth knowing. 
Thanks again.

You will still need some guidance as you have a complex setup with all those drives.  You are also making some partition assumptions that are 'Windows' based rather than 'Linux' based (And who can blame you?  You use what you know!)

If you want to install 10.04 or 10.10 - please still run that script so we can get your partition situation arranged before the install and you can enjoy an successful install!

My guides even have Pictures!

Please boot off the 10.04 or 10.10 LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by jerrylamos on 2011-04-03
I always have a 10.04 or 10.10 installed first then (try to) install 11.04 on another partition.  When the Alpha/Beta screws up as it will, often in the case of 11.04, then I boot the 10.04 or 10.10 to straighten things out.

I thought Natty Alpha/Beta were to test Unity.  Wrong, most of my test time and bugs have been about trying to install the !@#$%^ thing.

In particular for my setups Grub 1.99 on Natty gets the boot menu all fowled up and I run 10.10 or 10.04 to re-do Grub.

Good luck, Jerry

---

### Post by X82 on 2011-04-03
Ok. Im currently in live mode for Ubuntu 10.
The same problem occurs. When I open up gparted for example, it shows my backup 250gb sata drive as ntfs, my downloads drive 1.5tb sata as ntfs but my main windows 7 drive as empty. It states there is 233gb free.

Here is the results of the previously posted script. If it helps.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sdf2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   281,270,271   281,268,224   7 HPFS/NTFS
/dev/sda2         281,270,272   490,227,711   208,957,440   7 HPFS/NTFS


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System
/dev/sda1              40       409,639       409,600 System/Boot Partition
/dev/sda2         411,648   490,231,807   489,820,160 Linux or Data
/dev/sda121 4,564,900,403,951,788,0071,389,300,966,694,243,208-3,175,599,437,257,544,798 -
/dev/sda122 2,223,603,724,265,931,1161,569,723,995,843,998,779-653,879,728,421,932,336 -
/dev/sda123 1,233,275,709,679,975,0664,045,833,384,455,372,2852,812,557,674,775,397,220 -
/dev/sda124 1,086,053,320,912,551,0644,184,917,830,532,724,8823,098,864,509,620,173,819 -

Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                   1   488,281,249   488,281,249  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdf1              40       409,639       409,600 System/Boot Partition
/dev/sdf2         411,648   488,280,063   487,868,416 Linux or Data

Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1               2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9AD8D4FDD8D4D919                       ntfs       Windows 7                     
/dev/sda2        E68CE85E8CE82B2F                       ntfs       Ubuntu                        
/dev/sda: PTTYPE="dos" 
/dev/sdf1        70D6-1701                              vfat       EFI                           
/dev/sdf2        FADA84AADA8464AB                       ntfs       Backup                        
/dev/sdf: PTTYPE="gpt" 
/dev/sdg1        9CF20B5BF20B38D2                       ntfs       1.5 TB                        
/dev/sdg: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown GPT Partiton Type
d441a0f503000300321fa1e2339bca7f
Unknown GPT Partiton Type
348d77adeb842d75f8a4f3316c60d488
Unknown GPT Partiton Type
a54230e47007919d8f0c37d032587ece
Unknown GPT Partiton Type
d9d8bb8bba941bd2e00442f7ccf0fcc9

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by srs5694 on 2011-04-04
Your /dev/sda seems to have used the GUID Partition Table (GPT) partitioning system at some point but been incompletely converted to Master Boot Record (MBR) form, leaving GPT data behind. This is confusing the Ubuntu installer. This problem can be corrected by my [FixParts](http://www.rodsbooks.com/fixparts/) program, but you'll need to download and install it from [its SourceForge download page,](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/) since it's not part of a standard installation. (You should be able to install it to an Ubuntu disc booted into live CD mode.)

Your /dev/sdf disk is a pure-GPT disk. This is fine, and it may account for at least one of the FAT partitions you're seeing, since the disk includes an EFI System Partition, which is a FAT partition intended for storing drivers and boot loaders used by the EFI firmware. Ubuntu *should* be happy to install to this disk, although you'd need to resize the second partition, which currently uses NTFS. If the installer is refusing to install here, I'd call that a bug in the beta, although it's possible I've missed some other sign of trouble on this disk -- or maybe the latest beta is insisting on seeing a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) on GPT disks before it'll install there, at least on BIOS-based computers.

Your /dev/sdg disk is a pure-MBR disk, which doesn't seem very unusual. It's probably the one that Ubuntu would happily install to.

---

### Post by sergio.otero on 2011-04-22
Hi

I had a similar problem after erasing all partitions and finished  installing Windows 7, because Ubuntu installation keep saying my HDD was  empty but it wasn't. 

Inside "Disk Utility" i could see the partitions and Windows worked perfectly.

I've runned FixParts and it has detected traces of a GPT partition. After deleting these traces, the installations has gone perfect.

Thanks !!!

---

### Post by sergio.otero on 2011-04-22
Only 1 thing about the program: i couldn't install the ".deb" within "Ubuntu Software Center" in a 11.04Beta2 live session because it said that it was a "Bad quality package" or something similar (maybe the wrong email provided ??)

I could install it in the same live session using dkpg

---

