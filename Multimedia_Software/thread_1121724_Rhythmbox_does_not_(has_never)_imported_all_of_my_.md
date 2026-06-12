---
title: "Rhythmbox does not (has never) imported *all* of my music"
date: 2009-04-10
forum: Multimedia Software
---

### Post by nc_jed on 2009-04-10
I have had a continuous issue with Rhythmbox spanning several versions of RB and Ubuntu but am finally fed up enough that I am going to post it.

My music is in FLAC, MP3 and Ogg formats and is contained on an external USB hard drive.  I am able to open/listen to the music via Totem, but RB refuses to import it correctly via ('Music > Import Folder' or via the defined Music Library in the Preferences).

No errors seem to occur, just.... nothing happens.

I was able to locate this bug, filed in the Fedora bugzilla ([https://bugzilla.redhat.com/show_bug.cgi?id=425942](https://bugzilla.redhat.com/show_bug.cgi?id=425942)) and at it's suggestion, I reinstalled the gstreamer plugins (good, bad, and ugly).  Of note, all three are versions including 'ubuntu' in the version level, so I assume that's as close as I can get to a non-third party plugin (as was described was the problem in the FC bug).

Please let me know your suggestions, I've got many GBs of music just waiting to be free...

- Jed

---

### Post by logos34 on 2009-04-10
> **nc_jed said:**
> 
I was able to locate this bug, filed in the Fedora bugzilla ([https://bugzilla.redhat.com/show_bug.cgi?id=425942](https://bugzilla.redhat.com/show_bug.cgi?id=425942)) and at it's suggestion, I reinstalled the gstreamer plugins (good, bad, and ugly).

what you want is ubuntu-restricted-extras pkg (it will drag in all the gstreamer - good, -bad -ugly stuff)

My guess is it's something to do with where and how the volume is mounting (permissions, etc)

---

### Post by nc_jed on 2009-04-11
Just tried that, no luck.  Same issue.  Any more ideas?

> My guess is it's something to do with where and how the volume is mounting (permissions, etc) 

For what it's worth, all of the music is on the same (removable) drive where some directories are being picked up and others are not.  Not sure if the permissions can toggle on/off that quickly, but I thought it worth mentioning.

- Jed

---

### Post by djbushido on 2009-04-11
is your music in just one folder? I.e. like /media/disk/Music?
If so, output the result of "ls -l" where that is LS -L only in lowercase. This will help us with file permissions (which is what I think it is). The only problem is that it should be able to at least read the files...
Anyway, output the result of that, as well as "sudo fdisk -l" where it is -L and "cat /etc/fstab"
If you want to try just changing all permissions at once, in the root music directory do "sudo chmod ugo=rwx -r *"
Hope that works!

---

### Post by cubeist on 2009-04-11
I've had the same problem, I think if the file extension is a format that rhythmbox can't play, it skips importing it.  I never found a solution, so I switched to banshee, sorry can't be more help

---

### Post by djbushido on 2009-04-11
rhythmbox should be able to support all of the above formats. try amarok or another player just to make sure though. besides, I enjoy amarok over rhythmbox.

---

### Post by nc_jed on 2009-04-12
> is your music in just one folder? I.e. like /media/disk/Music?

Unless I misunderstand your question, yes.  I use one folder /media/IOMEGA_HDD/music/ with lots of subfolders to segregate the music by Artist, etc.

> If so, output the result of "ls -l" where that is LS -L only in lowercase. This will help us with file permissions (which is what I think it is). The only problem is that it should be able to at least read the files...

Here is a trimmed version with 2 specific directories shown (one that is automatically included in the RhythmBox pull and one that is not).

**GOOD / INCLUDED**
[INDENT]> ./wsp/wsp20080404.flac16:
total 1189312
-rwx------ 1 blake root     1578 2008-04-05 16:01 ffp.txt
-rwx------ 1 blake root    20482 2008-04-05 16:01 mrman.jpg
-rwx------ 1 blake root    21333 2008-04-05 16:01 tree.jpg
-rwx------ 1 blake root     4943 2008-04-05 16:01 wsp20080404_16.txt
-rwx------ 1 blake root  2811504 2008-04-05 22:41 wsp20080404d1t01_Intro.flac
-rwx------ 1 blake root 52383536 2008-04-06 07:52 wsp20080404d1t02_Holden_Oversoul.flac
-rwx------ 1 blake root 38842986 2008-04-06 07:52 wsp20080404d1t03_Better_Off.flac
-rwx------ 1 blake root 53739290 2008-04-06 08:02 wsp20080404d1t04_Climb_To_Safety.flac
-rwx------ 1 blake root 81566525 2008-04-06 08:02 wsp20080404d1t05_Papa_Johnny_Road.flac
-rwx------ 1 blake root 50981522 2008-04-06 07:57 wsp20080404d1t06_Watching_The_Sleeping_Man.flac
-rwx------ 1 blake root 56544571 2008-04-06 07:55 wsp20080404d1t07_Sleepy_Monkey.flac
-rwx------ 1 blake root 28553682 2008-04-06 07:59 wsp20080404d1t08_Free_Somehow.flac
-rwx------ 1 blake root 43383514 2008-04-06 07:54 wsp20080404d1t09_Pleas.flac
-rwx------ 1 blake root 55879049 2008-04-06 08:02 wsp20080404d1t10_Love_Tractor.flac
-rwx------ 1 blake root  6722741 2008-04-06 00:57 wsp20080404d2t01_Intro.flac
-rwx------ 1 blake root 69858637 2008-04-06 08:00 wsp20080404d2t02_Space_Wrangler.flac
-rwx------ 1 blake root 86491722 2008-04-06 08:03 wsp20080404d2t03_Radio_Child.flac
-rwx------ 1 blake root 57978212 2008-04-06 07:46 wsp20080404d2t04_Jack.flac
-rwx------ 1 blake root 67032811 2008-04-06 07:46 wsp20080404d2t05_Wonderin.flac
-rwx------ 1 blake root 98861741 2008-04-06 08:02 wsp20080404d2t06_Second_Skin.flac
-rwx------ 1 blake root 38787646 2008-04-06 08:01 wsp20080404d2t07_Drums.flac
-rwx------ 1 blake root 95425805 2008-04-05 16:49 wsp20080404d3t01_Surprise_Valley.flac
-rwx------ 1 blake root 36866973 2008-04-06 07:55 wsp20080404d3t02_Protein_Drink.flac
-rwx------ 1 blake root 62250534 2008-04-06 07:47 wsp20080404d3t03_Sewing_Machine.flac
-rwx------ 1 blake root 26227905 2008-04-06 07:47 wsp20080404d3t04_Crowd.flac
-rwx------ 1 blake root 42682976 2008-04-06 07:57 wsp20080404d3t05_This_Part_Of_Town.flac
-rwx------ 1 blake root 63482171 2008-04-06 07:56 wsp20080404d3t06_Walk_On_The_Flood.flac


**BAD / SKIPPED**
./wsp/wsp2008-04-25.flac16.4channel:
total 1058080
-rwx------ 1 blake root  4471424 2008-04-29 07:58 wsp2008-04-25d1t01.flac
-rwx------ 1 blake root 54406264 2008-04-29 10:34 wsp2008-04-25d1t02.flac
-rwx------ 1 blake root 77680907 2008-04-29 10:35 wsp2008-04-25d1t03.flac
-rwx------ 1 blake root 31105981 2008-04-29 10:32 wsp2008-04-25d1t04.flac
-rwx------ 1 blake root 25686192 2008-04-29 10:27 wsp2008-04-25d1t05.flac
-rwx------ 1 blake root 45171558 2008-04-29 10:35 wsp2008-04-25d1t06.flac
-rwx------ 1 blake root 18543588 2008-04-29 18:39 wsp2008-04-25d1t07.flac
-rwx------ 1 blake root 19813433 2008-04-29 10:34 wsp2008-04-25d1t08.flac
-rwx------ 1 blake root 92061362 2008-04-29 10:34 wsp2008-04-25d1t09.flac
-rwx------ 1 blake root 56761505 2008-04-29 10:34 wsp2008-04-25d1t10.flac
-rwx------ 1 blake root  6656342 2008-04-29 08:31 wsp2008-04-25d2t01.flac
-rwx------ 1 blake root 32288633 2008-04-29 10:30 wsp2008-04-25d2t02.flac
-rwx------ 1 blake root 92795144 2008-04-29 10:33 wsp2008-04-25d2t03.flac
-rwx------ 1 blake root 78394112 2008-04-29 10:35 wsp2008-04-25d2t04.flac
-rwx------ 1 blake root 36152697 2008-04-29 10:23 wsp2008-04-25d2t05.flac
-rwx------ 1 blake root 79040628 2008-04-29 10:34 wsp2008-04-25d2t06.flac
-rwx------ 1 blake root  5549871 2008-04-29 07:47 wsp2008-04-25d3t01.flac
-rwx------ 1 blake root 68193690 2008-04-29 10:31 wsp2008-04-25d3t02.flac
-rwx------ 1 blake root 60321211 2008-04-29 10:34 wsp2008-04-25d3t03.flac
-rwx------ 1 blake root  9017570 2008-04-29 09:04 wsp2008-04-25d3t04.flac
-rwx------ 1 blake root 57613375 2008-04-29 10:34 wsp2008-04-25d3t05.flac
-rwx------ 1 blake root 59377104 2008-04-29 10:33 wsp2008-04-25d3t06.flac
-rwx------ 1 blake root 71911227 2008-04-29 10:33 wsp2008-04-25d3t07.flac
-rwx------ 1 blake root     4078 2008-04-29 07:58 wsp2008-04-25.txt
[/INDENT]

> Anyway, output the result of that, as well as "sudo fdisk -l" where it is -L and "cat /etc/fstab"
blake@desktop:/media/IOMEGA_HDD/music/Various/Misc$ **sudo fdisk -l**
[sudo] password for blake: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e5bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29646   238131463+  83  Linux
/dev/sda2           29647       30401     6064537+   5  Extended
/dev/sda5           29647       30401     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41b9fc71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

[COLOR="DarkGreen"]Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3941a02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    b  W95 FAT32
[/COLOR]

blake@desktop:/media/IOMEGA_HDD/music/Various/Misc$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bfa09907-c104-48a5-8cbd-4d7ce047632c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=15fbac3c-fde0-4cb9-92dd-f4860147aa11 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



Please let me know if there's any thing else you need.  I tried changing the perms to 775 for a single dir structure and it dfidn't work as expected.

- Jed

---

### Post by djbushido on 2009-04-12
Yep, the problem is with permissions, I believe. The first "rwx" indicates that the creator (not specifically you) can **r**ead, **w**rite, and e**x**ecute the files. Group and others (the next two sets of 3 dashes) don't have permissions at all, meaning that they can't do anything. So, try doing this command and see if anything happens: ```
sudo chmod o=rwx * -r
```This command will set the 'other' (chmod **o**) permissions so that they can **r**ead, **w**rite, and e**x**ecute the files. The * is a wildcard that indicates all files, and the -r means to do this recursively (to all files). Try that and see if it works.

---

### Post by logos34 on 2009-04-12
> **djbushido said:**
> CODE]sudo chmod o=rwx * -r[/CODE]


and make sure you cd into the music parent directory before running that or include the full path!

/media/IOMEGA_HDD/music/

Or would this be better:

sudo chmod -R 755

(755= rwxr-xr-x, all permissions for user/root, read and execute only for group and others)

???

---

### Post by nc_jed on 2009-04-12
djbushido/logos34, Thank you both for your suggestions, but they are not working.  Actually, it is the chmod operation that is not working correctly at this time.  Please review just an example change in a sub directory.

> blake@desktop:/media/IOMEGA_HDD/music/wsp/wsp20080404.flac16$ ls -al
total 1189376
drwx------  2 blake root    32768 2008-04-05 12:35 .
drwx------ 54 blake root    32768 2008-06-18 10:13 ..
-rwx------  1 blake root     1578 2008-04-05 16:01 ffp.txt
-rwx------  1 blake root    20482 2008-04-05 16:01 mrman.jpg
-rwx------  1 blake root    21333 2008-04-05 16:01 tree.jpg
-rwx------  1 blake root     4943 2008-04-05 16:01 wsp20080404_16.txt
-rwx------  1 blake root  2811504 2008-04-05 22:41 wsp20080404d1t01_Intro.flac
-rwx------  1 blake root 52383536 2008-04-06 07:52 wsp20080404d1t02_Holden_Oversoul.flac
-rwx------  1 blake root 38842986 2008-04-06 07:52 wsp20080404d1t03_Better_Off.flac
-rwx------  1 blake root 53739290 2008-04-06 08:02 wsp20080404d1t04_Climb_To_Safety.flac
-rwx------  1 blake root 81566525 2008-04-06 08:02 wsp20080404d1t05_Papa_Johnny_Road.flac
-rwx------  1 blake root 50981522 2008-04-06 07:57 wsp20080404d1t06_Watching_The_Sleeping_Man.flac
-rwx------  1 blake root 56544571 2008-04-06 07:55 wsp20080404d1t07_Sleepy_Monkey.flac
-rwx------  1 blake root 28553682 2008-04-06 07:59 wsp20080404d1t08_Free_Somehow.flac
-rwx------  1 blake root 43383514 2008-04-06 07:54 wsp20080404d1t09_Pleas.flac
-rwx------  1 blake root 55879049 2008-04-06 08:02 wsp20080404d1t10_Love_Tractor.flac
-rwx------  1 blake root  6722741 2008-04-06 00:57 wsp20080404d2t01_Intro.flac
-rwx------  1 blake root 69858637 2008-04-06 08:00 wsp20080404d2t02_Space_Wrangler.flac
-rwx------  1 blake root 86491722 2008-04-06 08:03 wsp20080404d2t03_Radio_Child.flac
-rwx------  1 blake root 57978212 2008-04-06 07:46 wsp20080404d2t04_Jack.flac
-rwx------  1 blake root 67032811 2008-04-06 07:46 wsp20080404d2t05_Wonderin.flac
-rwx------  1 blake root 98861741 2008-04-06 08:02 wsp20080404d2t06_Second_Skin.flac
-rwx------  1 blake root 38787646 2008-04-06 08:01 wsp20080404d2t07_Drums.flac
-rwx------  1 blake root 95425805 2008-04-05 16:49 wsp20080404d3t01_Surprise_Valley.flac
-rwx------  1 blake root 36866973 2008-04-06 07:55 wsp20080404d3t02_Protein_Drink.flac
-rwx------  1 blake root 62250534 2008-04-06 07:47 wsp20080404d3t03_Sewing_Machine.flac
-rwx------  1 blake root 26227905 2008-04-06 07:47 wsp20080404d3t04_Crowd.flac
-rwx------  1 blake root 42682976 2008-04-06 07:57 wsp20080404d3t05_This_Part_Of_Town.flac
-rwx------  1 blake root 63482171 2008-04-06 07:56 wsp20080404d3t06_Walk_On_The_Flood.flac
[email]blake@desktop:/media/IOMEGA_HDD/music/wsp/wsp20080404.flac[/email]16$ **sudo chmod 777 -R ***
[email]blake@desktop:/media/IOMEGA_HDD/music/wsp/wsp20080404.flac[/email]16$ ls -al
total 1189376
drwx------  2 blake root    32768 2008-04-05 12:35 .
drwx------ 54 blake root    32768 2008-06-18 10:13 ..
-rwx------  1 blake root     1578 2008-04-05 16:01 ffp.txt
-rwx------  1 blake root    20482 2008-04-05 16:01 mrman.jpg
-rwx------  1 blake root    21333 2008-04-05 16:01 tree.jpg
-rwx------  1 blake root     4943 2008-04-05 16:01 wsp20080404_16.txt
-rwx------  1 blake root  2811504 2008-04-05 22:41 wsp20080404d1t01_Intro.flac
-rwx------  1 blake root 52383536 2008-04-06 07:52 wsp20080404d1t02_Holden_Oversoul.flac
-rwx------  1 blake root 38842986 2008-04-06 07:52 wsp20080404d1t03_Better_Off.flac
-rwx------  1 blake root 53739290 2008-04-06 08:02 wsp20080404d1t04_Climb_To_Safety.flac
-rwx------  1 blake root 81566525 2008-04-06 08:02 wsp20080404d1t05_Papa_Johnny_Road.flac
-rwx------  1 blake root 50981522 2008-04-06 07:57 wsp20080404d1t06_Watching_The_Sleeping_Man.flac
-rwx------  1 blake root 56544571 2008-04-06 07:55 wsp20080404d1t07_Sleepy_Monkey.flac
-rwx------  1 blake root 28553682 2008-04-06 07:59 wsp20080404d1t08_Free_Somehow.flac
-rwx------  1 blake root 43383514 2008-04-06 07:54 wsp20080404d1t09_Pleas.flac
-rwx------  1 blake root 55879049 2008-04-06 08:02 wsp20080404d1t10_Love_Tractor.flac
-rwx------  1 blake root  6722741 2008-04-06 00:57 wsp20080404d2t01_Intro.flac
-rwx------  1 blake root 69858637 2008-04-06 08:00 wsp20080404d2t02_Space_Wrangler.flac
-rwx------  1 blake root 86491722 2008-04-06 08:03 wsp20080404d2t03_Radio_Child.flac
-rwx------  1 blake root 57978212 2008-04-06 07:46 wsp20080404d2t04_Jack.flac
-rwx------  1 blake root 67032811 2008-04-06 07:46 wsp20080404d2t05_Wonderin.flac
-rwx------  1 blake root 98861741 2008-04-06 08:02 wsp20080404d2t06_Second_Skin.flac
-rwx------  1 blake root 38787646 2008-04-06 08:01 wsp20080404d2t07_Drums.flac
-rwx------  1 blake root 95425805 2008-04-05 16:49 wsp20080404d3t01_Surprise_Valley.flac
-rwx------  1 blake root 36866973 2008-04-06 07:55 wsp20080404d3t02_Protein_Drink.flac
-rwx------  1 blake root 62250534 2008-04-06 07:47 wsp20080404d3t03_Sewing_Machine.flac
-rwx------  1 blake root 26227905 2008-04-06 07:47 wsp20080404d3t04_Crowd.flac
-rwx------  1 blake root 42682976 2008-04-06 07:57 wsp20080404d3t05_This_Part_Of_Town.flac
-rwx------  1 blake root 63482171 2008-04-06 07:56 wsp20080404d3t06_Walk_On_The_Flood.flac
[email]blake@desktop:/media/IOMEGA_HDD/music/wsp/wsp20080404.flac[/email]16$ 


For sanity's sake, I created a dummy directory structure (1 master fir, 2 children and three files in both) and chmod'd it to 700, recursively.  Worked fine.  The drive oesn't show up as 'Read only' so I'm at a little bit of a loss here.  Not doubting this could be a perms issue, just hate that its getting compounded like this.

- Blake

---

### Post by nc_jed on 2009-04-12
djbushido/logos34, It's the drive/mounting.  I copied over a branch of the directory tree to the internal HD, chmod'd it and everything was fine.  Looks like a drive/mounting issue.

Thanks for the help anyway,

Blake

---

### Post by djbushido on 2009-04-13
From this it looks like you cd'd into the file. In fact, I'm quite confident you did.
Try this:```
sudo chmod o=rx /media/IOMEGA_HDD/music -R
```
And output any error codes generated.
Also, try remounting the drive yourself, then doing this.

---

### Post by nc_jed on 2009-04-13
djbushido,
Did as directed, no difference.

> blake@desktop:~$ sudo chmod o=rx /media/IOMEGA_HDD/music -R


After running (quickly), I ls -lR the structure and get the below (a subset, of course)

> ./wsp/wsp2008-06-15.mk4v.flac16:
total 1139296
-rwx------ 1 blake root  40865618 2008-06-18 13:19 wsp2008-06-15d1t01.flac
-rwx------ 1 blake root  27791641 2008-06-18 12:51 wsp2008-06-15d1t02.flac
-rwx------ 1 blake root  30717242 2008-06-18 12:49 wsp2008-06-15d1t03.flac
-rwx------ 1 blake root  44558949 2008-06-18 13:15 wsp2008-06-15d1t04.flac
-rwx------ 1 blake root  57594048 2008-06-18 13:16 wsp2008-06-15d1t05.flac
-rwx------ 1 blake root  24032217 2008-06-18 13:21 wsp2008-06-15d1t06.flac
-rwx------ 1 blake root  33918198 2008-06-18 13:22 wsp2008-06-15d1t07.flac
-rwx------ 1 blake root  37212479 2008-06-18 13:18 wsp2008-06-15d1t08.flac
-rwx------ 1 blake root  50999301 2008-06-18 13:18 wsp2008-06-15d1t09.flac
-rwx------ 1 blake root  80360968 2008-06-18 13:23 wsp2008-06-15d1t10.flac
-rwx------ 1 blake root  49266606 2008-06-18 13:23 wsp2008-06-15d1t11.flac
-rwx------ 1 blake root  33751973 2008-06-18 13:20 wsp2008-06-15d2t01.flac
-rwx------ 1 blake root  55487169 2008-06-18 13:20 wsp2008-06-15d2t02.flac
-rwx------ 1 blake root   8116897 2008-06-18 13:21 wsp2008-06-15d2t03.flac
-rwx------ 1 blake root  28477355 2008-06-18 13:07 wsp2008-06-15d2t04.flac
-rwx------ 1 blake root  64009103 2008-06-18 13:22 wsp2008-06-15d2t05.flac
-rwx------ 1 blake root 104268611 2008-06-18 13:22 wsp2008-06-15d2t06.flac
-rwx------ 1 blake root  34961138 2008-06-18 13:23 wsp2008-06-15d2t07.flac
-rwx------ 1 blake root  44372505 2008-06-18 13:10 wsp2008-06-15d2t08.flac
-rwx------ 1 blake root  34082731 2008-06-18 13:13 wsp2008-06-15d2t09.flac
-rwx------ 1 blake root  50911553 2008-06-18 13:02 wsp2008-06-15d2t10.flac
-rwx------ 1 blake root  80616766 2008-06-18 13:22 wsp2008-06-15d3t01.flac
-rwx------ 1 blake root  51128570 2008-06-18 13:17 wsp2008-06-15d3t02.flac
-rwx------ 1 blake root  46163206 2008-06-18 13:11 wsp2008-06-15d3t03.flac
-rwx------ 1 blake root  52428879 2008-06-18 13:18 wsp2008-06-15d3t04.flac
-rwx------ 1 blake root      4856 2008-06-18 10:17 wsp2008-06-15.txt


I also unmounted the drive, turned it off for a few minutes then turned it back on (effectively remounting it).  Reran the chmod from ~ and same effect.

- Jed

---

### Post by djbushido on 2009-04-13
what i meant was to do "sudo umount /media/IOMEGA_HDD" and then "sudo mount /dev/sdx" where x is the drive letter. Try that.

---

### Post by nc_jed on 2009-04-13
FWIW, I always rely on HAL to automount it.  Below is as you request (mount pount not found in /etc/fstab):

> blake@desktop:~$ sudo umount /media/IOMEGA_HDD
[sudo] password for blake: 
blake@desktop:~$ sudo mount /dev/sdc
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab

blake@desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bfa09907-c104-48a5-8cbd-4d7ce047632c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=15fbac3c-fde0-4cb9-92dd-f4860147aa11 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

blake@desktop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-11-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/blake/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=blake 0 0


Ok, now I'm lost since there is no mountpoint defined in fstab.  perhaps that is a bell/whistle associated with USB drives/HAL.

- Jed

---

### Post by djbushido on 2009-04-13
Ooops. You forgot the partition number. It should read "sudo mount /dev/sdc1 /media/disk"
Also, the /media/disk is just any mountpoint, really any folder.

---

