---
title: "What??? Dual Boot?  Am I nutzz???"
date: 2011-02-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Dscottmc7 on 2011-02-26
[/B][/B]](*,)**"No root system defined"**  I know, it's been on a thousand posts...I've spent 7 days now searching---I can't find a post with my specific problem.  Running a 32bit HP Pavilion on Ubuntu 11.04, AND have new HP Pavilion 64 with Win7, partitioned for **dual boot** and stuck.
AMD Phenom 
8Gb RAM
1Tb HDD =sda
Present partitioning in process:
1st Primary Partition sda1 = 100Mib. ntfs Windows7 MBR flag=boot
2nd Primary Partition sda2 = 353.84Gb. ntfs Windows junk including about 300Gb free
3rd Primary sda3= Extended, 518.66GB (53.33Gb unallocated)
-sda5 = ext4 15.56Gb.logical
-sda6 = ext4 449.77Gb logical
Balance 58.91Gb unallocated
Tried 7 different configuratins with GPartEd and still have the same problem.
-Boot w/live 10.10 disk. --all OK.
-Boot_Script (TXT) says I'm cool.
-Can see and do everything from the live disk- OK
-But when I INSTALL I get to the "Allocate Space" with no options available.  It only has /dev/sda option on the bar but nothing else.  Install pops up the **No Root System Defined **Use paritioning to correct it.  I CAN'T GET PAST THAT PART TO THE UBUNTU OPTIONS! ( e.g. partitioning, "/" and "/Home" options, etc.)
I've tried slipping Grub2 in ahead of time, EVERYTHING...there MUST be a solution. CAN ANYONE HELP??? (I stupidly have all my stuff backed up on a 2Tb.ExtHDD...with Windows only...so I can't get back to my work.l $^%#^%&  
What??? I must be nuts!!!  HELP ANYONE, PLEASE!! ](*,)
Thanks mucho...
Scott

---

### Post by Hakunka-Matata on 2011-02-26
> -But when I INSTALL I get to the "Allocate Space" with no options available. It only has /dev/sda option on the bar but nothing else. Install pops up the No Root System Defined Use partitioning to correct it. I CAN'T GET PAST THAT PART TO THE UBUNTU OPTIONS! ( e.g. partitioning, "/" and "/Home" options, etc.)

You have to use Gparted and set the root partition on whatever partition it is you want to use for the Operating System.  See the Mount point on Sda2, that's what you need to do using Gparted.

---

### Post by PRC09 on 2011-02-26
I think the problem you have is that you have formatted the install area ahead of time and Ubuntu is identifying your partitions as already in use.It is easier to set your total space as unallocated and create your partitions manually and format during the install.

---

### Post by Hakunka-Matata on 2011-02-26
> Present partitioning in process:
1st Primary Partition sda1 = 100Mib. ntfs Windows7 MBR flag=boot
2nd Primary Partition sda2 = 353.84Gb. ntfs Windows junk including about 300Gb free
3rd Primary sda3= Extended, 518.66GB (53.33Gb unallocated)
-sda5 = ext4 15.56Gb.logical
-sda6 = ext4 449.77Gb logical
Balance 58.91Gb unallocated

Your disk is not prepared for a new Ubuntu installation yet. Look at the 9.10_Partition.png attached Thumbnail to see what you need for an Ubuntu installation.  Although you have two unused ext4 partitions, they are both extended partitions, they do not need to be extended partitions, I don't even know if extended ext4 partitions will work for the OS.  And the sizes are not optimal either.  What is required (in addition to your windows partitions) is
[LIST]
[*]One primary ext4 partition: maybe 50 GB.  set as ROOT / (Mount point)
[*]One extended partition of about twice the size of your RAM
[*]one linux/swap partition about twice the size of your RAM
[/LIST]

I think the best way for you to proceed is to boot into Ubuntu using a LiveCD.  Use Gparted to redo your current partitioning to create the list above, and that list is the same as what you see in the graphic 9.10_Partition.png.

If you have anything on your windows partitions then it's up to you to make sure it's either backed up, or you're ready to take the consequences if you mess those partitions up while using GParted.  It's late now, I'll drop in tomorrow to see how you're doing.  At any rate, the graphic included is a simple straight forward single boot (not multiboot) picture of a correctly partitioned drive for Unbuntu 10.10.  It's completely safe to partition ahead of time vs. letting the LiveCD installer (ubiquity) do it for you.  10.10s liveCD Installer has some bugs and could get you in trouble, do NOT use the "Install alongside other operating system" option if you choose to use it.

---

### Post by highspider on 2011-02-26
WARnING THIS MY BE OFF BASE BUT IT HAPPENED TO ME.

Are you exceeding the Bois limitations?  of seek distance on your hard drive.  some version of bios can only look so far down the hard drive ?   like the first 100 MB. 

 yes this effects grub, grub2 and linux.


(stolen from [http://grub.enbug.org/Manual](http://grub.enbug.org/Manual))

Use grub-emu.  Perhaps a little bit about when/if GRUB 2 cares about differences between i386 and x86_64 code. 

[LIST]
[*]In  particular, machines with BIOS limitations on maximum disk size (e.g.  32 GiB or 128 GiB) or number of cylinders (e.g. 1024) need /boot  to be within the BIOS limits so that GRUB can finish loading using BIOS  calls. If the boot disk is larger than what the BIOS can access, a  partition containing /boot or a separate /boot  partition should be created at the start of the disk within the BIOS  limits. A bootable CD containing parted or gparted can be used to create  such a partition on a fresh disk or resize existing partitions and  create such a partition. Back up your files before resizing existing  partitions.
[*]As an alternative to having /boot  on a separate partition at the start of the disk to work around BIOS  limitations, if you have ATA disks or SATA disks in legacy mode you can  use **grub-install --disk-module=ata** to workaround the  BIOS limitations. If you have any other type of disk you'll have to wait  for you subsystem to be implemented.
[/LIST]

---

### Post by jeremyjjbrown on 2011-02-26
You can't install an os on an extended or logical partition it has to be primary. Choose manual specify partitions, make some space and create a primary partition, format it Ext4, and set it as / and then finish the installer.

---

### Post by kansasnoob on 2011-02-27
> **jeremyjjbrown said:**
> **You can't install an os on an extended or logical partition it has to be primary.** Choose manual specify partitions, make some space and create a primary partition, format it Ext4, and set it as / and then finish the installer.

That is just not true. Windows hates living in logical partitions but Ubuntu can be installed in logical partitions w/o trouble :)

---

### Post by Hakunka-Matata on 2011-02-27
retracted

---

### Post by kansasnoob on 2011-02-27
> **Dscottmc7 said:**
> [/B][/B]](*,)**"No root system defined"**  I know, it's been on a thousand posts...I've spent 7 days now searching---I can't find a post with my specific problem.  Running a 32bit HP Pavilion on Ubuntu 11.04, AND have new HP Pavilion 64 with Win7, partitioned for **dual boot** and stuck.
AMD Phenom 
8Gb RAM
1Tb HDD =sda
Present partitioning in process:
1st Primary Partition sda1 = 100Mib. ntfs Windows7 MBR flag=boot
2nd Primary Partition sda2 = 353.84Gb. ntfs Windows junk including about 300Gb free
3rd Primary sda3= Extended, 518.66GB (53.33Gb unallocated)
-sda5 = ext4 15.56Gb.logical
-sda6 = ext4 449.77Gb logical
Balance 58.91Gb unallocated
Tried 7 different configuratins with GPartEd and still have the same problem.
-Boot w/live 10.10 disk. --all OK.
-Boot_Script (TXT) says I'm cool.
-Can see and do everything from the live disk- OK
-But when I INSTALL I get to the "Allocate Space" with no options available.  It only has /dev/sda option on the bar but nothing else.  Install pops up the **No Root System Defined **Use paritioning to correct it.  I CAN'T GET PAST THAT PART TO THE UBUNTU OPTIONS! ( e.g. partitioning, "/" and "/Home" options, etc.)
I've tried slipping Grub2 in ahead of time, EVERYTHING...there MUST be a solution. CAN ANYONE HELP??? (I stupidly have all my stuff backed up on a 2Tb.ExtHDD...with Windows only...so I can't get back to my work.l $^%#^%&  
What??? I must be nuts!!!  HELP ANYONE, PLEASE!! ](*,)
Thanks mucho...
Scott

Please post the output of the Boot Info Script so we can see it too, and also post the output of:

```
sudo parted -l
```

BTW that's a lower case L at the end, and please use code tags so it's easier to read.

---

### Post by jeremyjjbrown on 2011-02-27
> **kansasnoob said:**
> That is just not true. Windows hates living in logical partitions but Ubuntu can be installed in logical partitions w/o trouble :)

I've tried that on two occasions and it never worked out. Perhaps it was a different problem causing my issue.

---

### Post by RickJC on 2011-02-27
Hi guys i'm just wanting some help. I want to have a duel boot for my laptop so it'll run Win7 and Ubuntu Server 10.10. I've partitioned my HDD ready to install Ubuntu on it without wiping my Win7 off.

I've then loaded up the Laptop with the server CD in and run from CD, i'm now stuck as I'm unsure which option to go for. I'm new to installing Ubuntu server and the options aren't very clear, every time I try to install it seems to want to format why whole HDD and not the Linux partition I set up!

Can someone please tell me which option to go for so it'll just install on the Linux partition without formatting Win7. The reason I want to install Ubuntu Server is because I want to learn more about it.

Thanks.

---

### Post by kansasnoob on 2011-02-27
> **jeremyjjbrown said:**
> I've tried that on two occasions and it never worked out. Perhaps it was a different problem causing my issue.

It seems like it can be problematic if you start a "build" with nothing but an extended partition. That's probably why Ubuntu default "whole disc" installs begin with a primary partition. But I test a lot and you can see that I have many operating systems on nothing but logical partitions:

[ATTACH]184653[/ATTACH]

IMHO installing Windows in a logical partition is insane!

---

### Post by kansasnoob on 2011-02-27
> **RickJC said:**
> Hi guys i'm just wanting some help. I want to have a duel boot for my laptop so it'll run Win7 and Ubuntu Server 10.10. I've partitioned my HDD ready to install Ubuntu on it without wiping my Win7 off.

I've then loaded up the Laptop with the server CD in and run from CD, i'm now stuck as I'm unsure which option to go for. I'm new to installing Ubuntu server and the options aren't very clear, every time I try to install it seems to want to format why whole HDD and not the Linux partition I set up!

Can someone please tell me which option to go for so it'll just install on the Linux partition without formatting Win7. The reason I want to install Ubuntu Server is because I want to learn more about it.

Thanks.

Please start your own thread :D

Things get confusing otherwise. I've never done a server install but since you're using 10.10 some of my notes here in post #1 and post #15 may be helpful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by Dscottmc7 on 2011-03-08
Troops, all:  THANK you...it is I who has a bad case of the stupids!! I've tried (most) everything and end up exactly where I was 56 working hours ago (when it should have taken me 1/2 working hour!)  The end is "No Root System Defined" ...partition, etc.  BUT it seems that everyone can get past that to the next screen to set,fix,etc. partitions, mountpoint, etc.  But I can't get there!
At every end of a direction I end up with a bug (as described in Sourceforge) that says, "Failed.  grub-error:  cannot stat 'aufs.'" --so I never get the Grub INSTALLED (I have /boot/Grub & contents on Sda3 but can't do anything to make it happen.
Partitions:
1Tb. HDD partitioned into
sda1 = ntfs Windows boot system 100MiB
sda2 = ntfs Windows misc. 338Gib.
sda3 = ext4 / root 16Gib
sda4 (primary to Extended) Extended
Sda5 = ext4 /home 575Gib.\
sda6 = swap 2.Gib.

Running HP Elite 110f -64
AMD64 Phenom (too tired to check the spelling!!)
8 Gib. RAM
onboard graphics card.

ubuntu@ubuntu:~$ sudo parted -l:=
Model: ATA WDC WD10EADS-65M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs
 2      106MB   363GB   363GB   primary   ntfs
 3      363GB   381GB   17.2GB  primary   ext4            boot
 4      381GB   1000GB  620GB   extended
 5      381GB   998GB   618GB   logical   ext4
 6      998GB   1000GB  2145MB  logical   linux-swap(v1)

Error: /dev/sr0: unrecognised disk label
I've listed all partitions by UUID in fstab...always changes and end up with "cannot stat 'aufs'"](*,)
(Hey, I may be old, but I'm stupid!):-({|= So, bohdi, Hakunka...anybody with an answer?  (Win7 partitions are clean and working) I sincerely appreciate the time you've taken to comment.=D>
Thanks from wannabe not-newb!
Scott
"mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sda4 Unknown BootLoader  on pdc_bcgeaaajfb1
ERROR: dos: partition address past end of RAID device -OK, I've never touched that.  I will and then crash (i.e. bed).  Thanks again...

---

### Post by Hakunka-Matata on 2011-03-08
Please restate your situation/problem.  I've sort of lost track of what the problem is.  If you wish to persevere restate, reset, refresh, and we'll see what's to do.

---

### Post by Dutch70 on 2011-03-08
Dscottmc7, it looks like you have a much better partitioning scheme, but I'm also not clear on what problem you're having now.

---

### Post by Dscottmc7 on 2011-03-08
> **Hakunka-Matata said:**
> Please restate your situation/problem.  I've sort of lost track of what the problem is.  If you wish to persevere restate, reset, refresh, and we'll see what's to do.
Desire:I want to dual boot Win 7 and natty 11.04 (I'm running 11.04 flawlessly on my other HP.
Problem: Problem with any current Live CD install (alternate, Desktop, DVD etc.) is that I can go to the third page to the **"No Root System Defined..."** and NO FURTHER.](*,)
-I've partitioned it [new HP] so-so (OK)(see all stats above)
-have / on SDA3 w/flag "root"
-have dedicated /home on SDA5 (logical)
-ANY effort (means) to get GRUB installed on SDA3 so that natty will see it fails with "Error: cannot stat 'aufs'.  But.../boot/grub with all the content is already on SDA3...??  Sourceforge says "cannot stat 'aufs' is a bug.
I truly appreciate you, guys. =D> I'm dead in the water.
Scott (same ole "so not wannabe noob!")
-I'm a dumb***!  I'm a well-intentioned, old noob of 6 years on Ubuntu...you'd think I'd know.  BUT...I'm a writer of books not code.
Much obliged, again!
Scott:mrgreen:
D. Scott McGregor

---

### Post by uRock on 2011-03-08
Moved to NNT&D.

---

### Post by Hakunka-Matata on 2011-03-08
> **Dscottmc7 said:**
> Desire:I want to dual boot Win 7 and natty 11.04 (I'm running 11.04 flawlessly on my other HP.
Problem: Problem with any current Live CD install (alternate, Desktop, DVD etc.) is that I can go to the third page to the **[COLOR="Magenta"]"No Root System Defined..."[/COLOR]** and NO FURTHER.](*,)
-I've partitioned it [new HP] so-so (OK)(see all stats above)
-have / on SDA3 w/flag "root"
-have dedicated /home on SDA5 (logical)
-ANY effort (means) to get GRUB installed on SDA3 so that natty will see it fails with "Error: cannot stat 'aufs'.  But.../boot/grub with all the content is already on SDA3...??  Sourceforge says "cannot stat 'aufs' is a bug.
I truly appreciate you, guys. =D> I'm dead in the water.
Scott (same ole "so not wannabe noob!")
-I'm a dumb***!  I'm a well-intentioned, old noob of 6 years on Ubuntu...you'd think I'd know.  BUT...I'm a writer of books not code.
Much obliged, again!
Scott:mrgreen:
D. Scott McGregor

please attach a GParted picture of [COLOR="Magenta"]that drive[/COLOR]?

---

### Post by Dscottmc7 on 2011-03-08
Thanks to you guys I'm in business!!!=D> (re:dual boot w/ install not recognizing boot [Sda3]]
I tried installing GRUB2 (image)by every means listed, (from PXE, to weird extensions for "install") and rebooted.  SHOCK, grub> came up as a prompt!
I exited "grub>" and rebooted natty 11.04 Live CD (Desktop amd64).
In "Applications" -->"Accessories" -->"Terminal"
Typed in:  "sudo apt-get remove dmraid"
then rebooted the CD for about the 100th time!
BINGO!  Perfect Dual Boot!! Champagne time!!!  All is perfect.:guitar:
THANKS MUCHO!!
Scott8-)

---

### Post by Dutch70 on 2011-03-08
> **Dscottmc7 said:**
> Thanks to you guys I'm in business!!!=D> (re:dual boot w/ install not recognizing boot [Sda3]]
I tried installing GRUB2 (image)by every means listed, (from PXE, to weird extensions for "install") and rebooted.  SHOCK, grub> came up as a prompt!
I exited "grub>" and rebooted natty 11.04 Live CD (Desktop amd64).
In "Applications" -->"Accessories" -->"Terminal"
Typed in:  "sudo apt-get remove dmraid"
then rebooted the CD for about the 100th time!
BINGO!  Perfect Dual Boot!! Champagne time!!!  All is perfect.:guitar:
THANKS MUCHO!!
Scott8-)

Sweet!!! Good work Scott!

---

