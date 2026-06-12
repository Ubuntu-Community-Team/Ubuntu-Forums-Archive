---
title: "Partition not recognised by Ubuntu 10.10 new installation"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Ambij on 2010-09-07
Hi,

Partition not recognised by Ubuntu 10.10 new installation

I have dual boot (Windows vista and Ubuntu 9) on dell inspiron. I am trying to install Ubuntu 10 on the partition in which previous Ubuntu 9 was installed. But while installing ubuntu does not recognise any of the previous partitions. I tried TestDisk to fix the partition table but no success yet. Output of TestDisk Deep search and fdisk -lu are as follows.



**Output of sudo fdisk -lu**

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      192779       96358+   6  FAT16
/dev/sda2          194560    21166079    10485760    7  HPFS/NTFS
/dev/sda3        21166080   175042536    76938228+   7  HPFS/NTFS
/dev/sda4       175044240   312592769    68774265    f  W95 Ext'd (LBA)
/dev/sda5       175044303   179927982     2441840   82  Linux swap / Solaris
/dev/sda6       179928063   307323446    63697692   83  Linux
/dev/sda7       307337216   312578047     2620416    c  W95 FAT32 (LBA)

**Output of TestDisk Deep search**

	Partition	Start	End	Size in Sectors			Message on being highlighted
*	FAT16 > 32M	0 1 1 '	11 254 63'	192717	[DellUtility]		FAT16 98MB / 94 MiB
D	FAT32 LBA	12 0 1'	4189 254 63'	67119570	[NO NAME]		FAT32, 34 GB / 32 GiB
P	HPFS - NTFS	12 28 17'	1317 134 33'	20971520	[RECOVERY]		NTFS, 10 GB / 10 GiB
P	HPFS - NTFS	1317 134 34'	10895 277 61'	153876457	[OS]		NTFS, 78 GB / 73 GiB
L	Linux Swap	10896 1 1'	11199 254 46'	4883680			SWAP2 version 1, 2500 MB / 2384 MiB
L	Linux	11200 1 1'	19129 254 60'	127395384			EXT3 Large file Sparse superblock, 65 GB / 60 GB
L	FAT32 LBA	19130 218 33'	19457 21 20'	5240832	[MEDIADIRECT]		FAT 32, 2683 MB / 2559 MiB

---

### Post by quixote on 2010-09-09
Am I reading your info correctly: sda4 is an extended primary partition, sda6 is a logical partition where you want to install ubuntu.  Is that right?

What have you tried?  An upgrade from the install already on sda6?  A clean install?  When you say "does not recognize partitions" do you mean when you're trying to install?  I.e. the install fails.  Or do you mean after the install you can't see any of the other partitions?

I don't see anything in the output which suggests problems with partitions, so I think the problem is elsewhere, either grub or gparted.

---

### Post by Ambij on 2010-09-10
>Am I reading your info correctly: sda4 is an extended primary partition, sda6 is a logical partition where you want to install ubuntu. Is that right?

I think yes. Sda6 is sure the one where ubuntu 8 was installed, I want to install ubuntu 9 on it, not upgrade but fresh install (because I think fresh install performs better than upgrade).

>What have you tried? An upgrade from the install already on sda6? A clean install? When you say "does not recognize partitions" do you mean when you're trying to install? I.e. the install fails. Or do you mean after the install you can't see any of the other partitions?

I tried fresh install. And it does not recognise any of the existing partitions. Since I don't want to delete the exsting windows os, so I want the new Ubuntu 9 install to recognise all the exisitng partitions and then install on the partition on which ubuntu 8 is already installed.

>I don't see anything in the output which suggests problems with partitions, so I think the problem is elsewhere, either grub or gparted.

Is the partition table correct? The computer does not at all boot now, boot 22 error.

Thanks.

---

### Post by srs5694 on 2010-09-10
> **Ambij said:**
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      192779       96358+   6  FAT16
/dev/sda2          194560    21166079    10485760    7  HPFS/NTFS
/dev/sda3        21166080   175042536    76938228+   7  HPFS/NTFS
/dev/sda4       175044240   312592769    68774265    f  W95 Ext'd (LBA)
/dev/sda5       175044303   179927982     2441840   82  Linux swap / Solaris
/dev/sda6       179928063   307323446    63697692   83  Linux
/dev/sda7       307337216   312578047     2620416    c  W95 FAT32 (LBA)

Your /dev/sda4 ends at sector 312592769, which is beyond the end of the disk, at sector 312581808. This is causing the problem. See [here](http://www.rodsbooks.com/missing-parts/index.html) for details and a several possible solutions.

---

### Post by Ambij on 2010-09-13
Thanks. I followed your link and fixed the oversized extended partition. Many thanks for the link, it was wonderfully well explained.

The gparted shows the partition correctly now but my computer does not boot up. On startup It shows the grub terminal instead of different os to boot from.

Here is the output from fdisk -lu

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      192779       96358+   6  FAT16
/dev/sda2          194560    21166079    10485760    7  HPFS/NTFS
/dev/sda3   *    21166080   175042536    76938228+   7  HPFS/NTFS
/dev/sda4       175044240   312581807    68768784    f  W95 Ext'd (LBA)
/dev/sda5       175044303   179927982     2441840   82  Linux swap / Solaris
/dev/sda6       179928063   307323446    63697692   83  Linux


Many thanks again.

---

### Post by Iowan on 2010-09-13
Moved to Maverick Meerkat Testing and Discussion

---

### Post by VMC on 2010-09-13
> **Ambij said:**
> Thanks. I followed your link and fixed the oversized extended partition. Many thanks for the link, it was wonderfully well explained.

The gparted shows the partition correctly now but my computer does not boot up. On startup It shows the grub terminal instead of different os to boot from.
...
Maybe just a re-install of grub will fix your issue now. If you boot up using the livecd, and look inside sda6 partition, do you see the data structure? 
you could issue a file system check on that partition from the livecd:

From a terminal type the following:
(forcing a check and giving you the output in verbose mode)
```
sudo fsck -fv /dev/sda6
```

Also when you installed Maverick on partition 6 , was that from the advance manual or automatic install.

---

### Post by ronparent on 2010-09-13
To reinstall grub see: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by kansasnoob on 2010-09-13
If you're still having problems please post the output of the Boot Info Script as described here using a Live CD:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can use any Live CD, it needn't be a Maverick CD.

---

### Post by Ambij on 2010-09-14
Hi All,

Thanks for all your replies. Much appreciated. I have attached at the end of this message the output of Boot info script and file system check.

>kansasnoob
>If you're still having problems please post the output of the Boot Info Script 

Yes, still having problems. The out of boot info script is at end of this message.

>ronparent
>To reinstall grub see

Already done that but issue remains.

>VMC
>If you boot up using the livecd, and look inside sda6 partition, >do you see the data structure? you could issue a file system check on that partition from the livecd:

If I boot from a live cd I can see the sda6 partition and all the data inside it. Is that what you meant? The output of file system check is at end of this message.


**[SIZE="7"]OUTPUT OF BOOT INFO SCRIPT downloaded from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)[/SIZE]**

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda6 already mounted or sda6 busy

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       192,779       192,717   6 FAT16
/dev/sda2             194,560    21,166,079    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,166,080   175,042,536   153,876,457   7 HPFS/NTFS
/dev/sda4         175,044,240   312,581,807   137,537,568   f W95 Ext d (LBA)
/dev/sda5         175,044,303   179,927,982     4,883,680  82 Linux swap / Solaris
/dev/sda6         179,928,063   307,323,446   127,395,384  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-0403                              vfat       DellUtility                   
/dev/sda2        7ADCA871DCA828F9                       ntfs       RECOVERY                      
/dev/sda3        50DCACD1DCACB2A0                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        30753b69-f68c-4bb2-9151-e0eccd5ff3f4   swap                                     
/dev/sda6        4cca8fff-68fb-4296-8207-ca26fd65b25d   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  15 cd a6 34 32 b1 ea 56  69 74 d2 5e 50 0f 8b 18  |...42..Vit.^P...|
00000010  b0 1d fb 24 fe 64 4a a8  4d 4a e4 e8 35 6a 98 2d  |...$.dJ.MJ..5j.-|
00000020  29 92 19 00 9c fd 40 e1  c0 a8 55 a0 88 18 57 9f  |).....@...U...W.|
00000030  06 24 cd 71 81 36 a2 b3  cb 0c f7 76 69 b5 3f 0e  |.$.q.6.....vi.?.|
00000040  19 27 bf 7b 48 fa 12 76  f5 33 e1 d4 b2 88 28 1d  |.'.{H..v.3....(.|
00000050  9c 6b 13 fa 7c 3a 0f 60  92 82 d4 23 4d b3 8c 4b  |.k..|:.`...#M..K|
00000060  94 7e da e0 b7 33 8e 98  c7 68 f1 f6 10 b7 19 1b  |.~...3...h......|
00000070  5f 44 5b 6a ab 6b 7e ea  5f 28 f2 0b c0 1f d7 6b  |_D[j.k~._(.....k|
00000080  75 df e1 99 16 9b ff 0b  ff bd 6c 9e 9c 05 32 63  |u.........l...2c|
00000090  56 7f 06 54 ef 70 0c 7e  1f 44 b3 81 e9 c5 e5 e6  |V..T.p.~.D......|
000000a0  ac 11 cd ab 7a b0 10 f4  9c cd 33 b0 01 dc 40 63  |....z.....3...@c|
000000b0  a4 2e 56 3d b0 e8 9d 80  d2 69 f1 8b fc 58 87 02  |..V=.....i...X..|
000000c0  48 53 09 79 99 5b 94 5b  a1 46 9b 99 92 1a 99 f2  |HS.y.[.[.F......|
000000d0  ff 10 eb 67 3c 62 ba fc  0d b2 4f 98 49 f4 24 ac  |...g<b....O.I.$.|
000000e0  43 23 e0 7d 7f b3 d7 00  88 ef 3e c1 9a 36 bc 63  |C#.}......>..6.c|
000000f0  ba 04 ef d8 d2 08 fd 37  1a ee 94 3c b8 10 f8 0c  |.......7...<....|
00000100  60 90 a3 24 16 75 49 73  5e 43 a8 fb 5d 67 ed a5  |`..$.uIs^C..]g..|
00000110  8b 43 53 f5 e0 81 f2 ab  d8 93 a9 86 b1 af e9 a0  |.CS.............|
00000120  10 93 46 e2 3b 3d ee c1  be 9e 28 90 ed ea 2d 3b  |..F.;=....(...-;|
00000130  92 76 dd ae 14 6b 3b 7e  ae e9 73 11 88 39 55 5b  |.v...k;~..s..9U[|
00000140  87 9d d2 11 78 32 ff 72  5a ab 54 63 31 95 69 52  |....x2.rZ.Tc1.iR|
00000150  ad a1 f2 40 39 a7 18 ab  5d 17 a7 5d 1b 67 3d 39  |...@9...]..].g=9|
00000160  ae f2 6d 0f 7c 18 83 46  f1 a6 77 24 cd 38 c4 d0  |..m.|..F..w$.8..|
00000170  97 6d f9 9b 3a ad f7 af  04 6e d9 87 fe e9 78 06  |.m..:....n....x.|
00000180  0f 01 e4 af 3c 57 a3 21  a7 2a ea 06 fb ee f9 25  |....<W.!.*.....%|
00000190  ec f2 1c f1 a9 f1 dd 8c  f2 17 0a 57 df 5b 62 84  |...........W.[b.|
000001a0  8f ac d1 39 32 6e d9 3d  22 6a 94 34 4c 97 e0 fe  |...92n.="j.4L...|
000001b0  18 21 80 cd af 2e bb ed  2f 3f 92 4a d1 a0 00 fe  |.!....../?.J....|
000001c0  ff ff 82 fe ff ff 3f 00  00 00 e0 84 4a 00 00 fe  |......?.....J...|
000001d0  ff ff 05 fe ff ff 1f 85  4a 00 01 23 e8 07 00 00  |........J..#....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


**[SIZE="7"]OUTPUT OF file system check[/SIZE]**

ubuntu@ubuntu:~$ sudo fsck -fv /dev/sda6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sda6 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda6: recovering journal
Superblock last mount time is in the future.
	(by less than a day, probably due to the hardware clock being incorrectly set)  Fix<y>? yes

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda6: ***** FILE SYSTEM WAS MODIFIED *****

  758013 inodes used (9.52%)
   26542 non-contiguous files (3.5%)
     616 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 44098/965/0
 9135194 blocks used (57.37%)
       0 bad blocks
       1 large file

  585805 regular files
  145800 directories
     114 character device files
      26 block device files
       2 fifos
     924 links
   26239 symbolic links (22982 fast symbolic links)
      18 sockets
--------
  758928 files
ubuntu@ubuntu:~$

---

### Post by tssaravananone on 2010-09-14
In BIOS, change SATA mode from "*AHCI*" to "*ATA*" and then try.

Hope will solve this issue.

Have a nice day

---

### Post by ratcheer on 2010-09-14
If none of the above suggestions help, you might also try deleting the existing partition and recreating it with a Lucid or Maverick version of gparted. Sometime during the Lucid development process, a change was made to to requirements of the alignment boundary of the beginning of a valid partition. If your existing partition does not meet this requirement, Maverick will not use it.

Tim

---

### Post by Ambij on 2010-09-14
Hi,


>tssaravananone
>In BIOS, change SATA mode from "AHCI" to "ATA" and then try.

Thanks. But I am wondering the rationale of this approach.

>ratcheer
>If none of the above suggestions help, you might also try deleting the existing partition and recreating it with a Lucid or Maverick version of gparted.

Thanks again. But I want to fix the partition, not delete and completely create new. Secondly while creating new, will Maverick  version of gparted recognise the existing partitions? Third does Maverick  version comes in the live or rescue CD?

Thanks again.

---

### Post by VMC on 2010-09-14
> WARNING!!! The filesystem is mounted. If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.


You should obey the warning here. I said to boot with a livecd and then issue the command. It appears you booted from sda6 and then did a file system check on that partition.

Also next time put your outputs inside code tags. It makes reading it easier.

---

### Post by Ambij on 2010-09-14
Hi,

I had not booted from the sda6 but from the live CD. However after booting from the live CD I had opened the sda6 folder (from Places--> menu) and hence sda6 got mounted. I thought ignoring the warning in this case will not do any harm.

Thanks.

---

### Post by ratcheer on 2010-09-14
> **Ambij said:**
> Hi,


>ratcheer
>If none of the above suggestions help, you might also try deleting the existing partition and recreating it with a Lucid or Maverick version of gparted.

Thanks again. But I want to fix the partition, not delete and completely create new. Secondly while creating new, will Maverick  version of gparted recognise the existing partitions? Third does Maverick  version comes in the live or rescue CD?

Thanks again.

If you don't want to delete and recreate, that is your choice.

Yes, the Maverick gparted should recognize the existing partitions. If it doesn't, just exit without doing anything and nothing will be harmed.

And, yes, gparted should be on the Maverick LiveCD image.

Tim

---

### Post by Ambij on 2010-09-14
Hi,

Not sure if I understand you correctly. Do you mean to delete the whole partition? If yes then will I not lose my data? Or you just mean to rewrite the partition table?

I ran the GParted from the ubuntu 10.10 beta live cd and it shows all my partitions. I then changed the flag of the /dev/sda6 (where ubuntu was installed). The reason for this was to allow GParted to rewrite the partition table. But the issue remains.

When I boot, I just get the GRUB command prompt. I type linux and it says no kernel found.

Any idea why GRUB is not able to find any operating system?

Thanks.

---

### Post by VMC on 2010-09-14
Your Boot Info Script output is incomplete. It didn't find a *grub.cfg* file.

I would guess you didn't install it correctly.

Your MBR is pointing to partition#6 of sda, but most likely missing "/grub/boot" files.

You could try chrooting into sda6 an try updating grub.

---

### Post by Ambij on 2010-09-15
Hi,


>Your Boot Info Script output is incomplete. It didn't find a *grub.cfg* file. I would guess you didn't install it correctly. Your MBR is pointing to partition#6 of sda, but most likely missing "/grub/boot" files. You could try chrooting into sda6 an try updating grub. 	

Thanks. Sorry but can you also tell me or point to a link explaining how to update grub? I have followed the following link in past but issue remains.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Thanks again.

---

### Post by mechanic on 2010-09-15
> **ratcheer said:**
> 

And, yes, gparted should be on the Maverick LiveCD image.

It is, but crashes every time on my system. GParted on the parted-magic disk is fine.

---

### Post by VMC on 2010-09-15
> **Ambij said:**
> Hi,


>Your Boot Info Script output is incomplete. It didn't find a *grub.cfg* file. I would guess you didn't install it correctly. Your MBR is pointing to partition#6 of sda, but most likely missing "/grub/boot" files. You could try chrooting into sda6 an try updating grub. 	

Thanks. Sorry but can you also tell me or point to a link explaining how to update grub? I have followed the following link in past but issue remains.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Thanks again.

Not seeing your sda6 file structure, I would be making a wild guess. Try chrooting and then update grub from sda6. Like so:

Boot up using LiveCD, then follow the code below, from a terminal.
```
sudo mount /dev/sda6 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt/ /bin/bash
sudo update-grub
If the above doesn't work try re-installing grub:
sudo grub-install /dev/sda
```

After you complete the above then back out of chroot:
Ctrl+d to exit chroot, then run these commands.
```
sudo umount /mnt/etc/resolv.conf
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```

---

### Post by Ambij on 2010-09-15
Hi,

>VMC
 >Not seeing your sda6 file structure, I would be making a wild guess. Try chrooting and then update grub  >from sda6. Like so:

Done but still on boot I do not see the different OS options. I think boot.cfg still not created. Also when I boot from live CD and run  "sudo grub-install /dev/sda" it gives me an error "sudo: unable to resolve host ubuntu"


Here is the output from the boot script.



```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       192,779       192,717   6 FAT16
/dev/sda2             194,560    21,166,079    20,971,520   7 HPFS/NTFS
/dev/sda3          21,166,080   175,042,536   153,876,457   7 HPFS/NTFS
/dev/sda4         175,044,240   312,581,807   137,537,568   f W95 Ext d (LBA)
/dev/sda5         175,044,303   179,927,982     4,883,680  82 Linux swap / Solaris
/dev/sda6         179,928,063   307,323,446   127,395,384  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-0403                              vfat       DellUtility                   
/dev/sda2        7ADCA871DCA828F9                       ntfs       RECOVERY                      
/dev/sda3        50DCACD1DCACB2A0                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        30753b69-f68c-4bb2-9151-e0eccd5ff3f4   swap                                     
/dev/sda6        4cca8fff-68fb-4296-8207-ca26fd65b25d   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/4cca8fff-68fb-4296-8207-ca26fd65b25d ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /mnt                     ext3       (rw)
/dev             /mnt/dev                 none       (rw,bind)
/dev/pts         /mnt/dev/pts             none       (rw,bind)


=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, kernel 2.6.24-22-generic
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro quiet splash 
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,6)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d ro  single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Chainload into GRUB 2
root        (hd0,6)
kernel        /boot/grub/core.img

title        Ubuntu 9.04, memtest86+
root        (hd0,6)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title        Microsoft Windows XP Embedded
root        (hd0,4)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=4cca8fff-68fb-4296-8207-ca26fd65b25d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
#UUID=07D8-0403  /media/sda1     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=7ADCA871DCA828F9 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=50DCACD1DCACB2A0 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=BAB0-38DA  /media/sda5     vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=30753b69-f68c-4bb2-9151-e0eccd5ff3f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#academic webpage folder
#//danube.brunel.ac.uk/cspgaaj /media/brunelshare3 cifs user=cspgaaj,pass=potatoA1,noperms 0 0
#//danube.brunel.ac.uk/cspgaaj /media/brunelshare3 cifs user=cspgaaj,pass=salaTON'1,noperms 0 0
#disc shared 2GB
#//134.83.83.26/home$/cspgaaj /media/brunelshare1 cifs user=DISC/cspgaaj,pass=potatoA1,noperms 0 0
#//134.83.83.26/home$/cspgaaj /media/brunelshare1 cifs user=academic\cspgaaj,pass=salaTON'1,noperms 0 0
#//134.83.83.26/home$/cspgaaj /media/brunelshare1 cifs credentials=/home/ambi/01MYRES/credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//134.83.83.26/home$/cspgaaj /media/brunelshare1 cifs credentials=/home/ambi/01MYRES/credentials,domain=disc,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
#academic H drive 100MB
#//uxfstru111.academic.windsor/cssf /media/brunelshare2 cifs user=cspgaaj,pass=salaTON'1,noperms 0 0
#//uxfstru111.academic.windsor/cssf /media/brunelshare2 cifs user=academic\cspgaaj,pass=salaTON'1,noperms 0 0
#//uxfstru111.academic.windsor/cssf /media/brunelshare2 cifs user=sdsadasdaacademic\cspgaaj,pass=aaaasalaTON'1,noperms 0 0
#//uxfstru111.academic.windsor/cssf/cspgaaj /media/brunelshare2 cifs user=academic/cspgaaj,pass=salaTON'1,noperms 0 0
#academic webpage folder
#//danube.brunel.ac.uk/cspgaaj /media/brunelshare3 cifs credentials=/home/ambi/01MYRES/credentials,domain=mydomain 0 0
#disc shared 2GB
#//134.83.83.26/home$/cspgaaj /media/brunelshare1 cifs credentials=/home/ambi/01MYRES/credentials,domain=mydomain 0 0
#academic H drive 100MB
#//uxfstru111.academic.windsor/cssf /media/brunelshare2 cifs credentials=/home/ambi/01MYRES/credentials,domain=mydomain 0 0
#//uxfstru111.academic.windsor/cssf /media/brunelshare2 cifs credentials=/home/ambi/01MYRES/credentials,domain=academic 0 0
#//uxfstru111.academic.windsor/cssf/cspgaaj /media/brunelshare2 cifs credentials=/home/ambi/01MYRES/credentials,domain=academic 0 0
#//uxfstru111.academic.windsor/cssf/cspgaaj /media/brunelshare2 cifs credentials=/home/ambi/01MYRES/credentials,nounix,noperms 0 0
#//uxfstru111.academic.windsor/cssf/cspgaaj /media/brunelshare2 cifs credentials=/home/ambi/01MYRES/credentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

=================== sda6: Location of files loaded by Grub: ===================


 123.2GB: boot/grub/core.img
 123.2GB: boot/grub/menu.lst
 123.1GB: boot/grub/stage2
 153.3GB: boot/initrd.img-2.6.24-22-generic
 153.2GB: boot/initrd.img-2.6.24-22-generic.bak
 153.1GB: boot/initrd.img-2.6.27-11-generic
 126.2GB: boot/initrd.img-2.6.28-13-generic
 153.2GB: boot/initrd.img-2.6.28-14-generic
 153.3GB: boot/initrd.img-2.6.28-16-generic
 126.2GB: boot/vmlinuz-2.6.24-22-generic
 123.6GB: boot/vmlinuz-2.6.27-11-generic
 125.9GB: boot/vmlinuz-2.6.28-13-generic
 153.2GB: boot/vmlinuz-2.6.28-14-generic
 126.2GB: boot/vmlinuz-2.6.28-16-generic
 153.3GB: initrd.img
 153.2GB: initrd.img.old
 126.2GB: vmlinuz
 153.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  15 cd a6 34 32 b1 ea 56  69 74 d2 5e 50 0f 8b 18  |...42..Vit.^P...|
00000010  b0 1d fb 24 fe 64 4a a8  4d 4a e4 e8 35 6a 98 2d  |...$.dJ.MJ..5j.-|
00000020  29 92 19 00 9c fd 40 e1  c0 a8 55 a0 88 18 57 9f  |).....@...U...W.|
00000030  06 24 cd 71 81 36 a2 b3  cb 0c f7 76 69 b5 3f 0e  |.$.q.6.....vi.?.|
00000040  19 27 bf 7b 48 fa 12 76  f5 33 e1 d4 b2 88 28 1d  |.'.{H..v.3....(.|
00000050  9c 6b 13 fa 7c 3a 0f 60  92 82 d4 23 4d b3 8c 4b  |.k..|:.`...#M..K|
00000060  94 7e da e0 b7 33 8e 98  c7 68 f1 f6 10 b7 19 1b  |.~...3...h......|
00000070  5f 44 5b 6a ab 6b 7e ea  5f 28 f2 0b c0 1f d7 6b  |_D[j.k~._(.....k|
00000080  75 df e1 99 16 9b ff 0b  ff bd 6c 9e 9c 05 32 63  |u.........l...2c|
00000090  56 7f 06 54 ef 70 0c 7e  1f 44 b3 81 e9 c5 e5 e6  |V..T.p.~.D......|
000000a0  ac 11 cd ab 7a b0 10 f4  9c cd 33 b0 01 dc 40 63  |....z.....3...@c|
000000b0  a4 2e 56 3d b0 e8 9d 80  d2 69 f1 8b fc 58 87 02  |..V=.....i...X..|
000000c0  48 53 09 79 99 5b 94 5b  a1 46 9b 99 92 1a 99 f2  |HS.y.[.[.F......|
000000d0  ff 10 eb 67 3c 62 ba fc  0d b2 4f 98 49 f4 24 ac  |...g<b....O.I.$.|
000000e0  43 23 e0 7d 7f b3 d7 00  88 ef 3e c1 9a 36 bc 63  |C#.}......>..6.c|
000000f0  ba 04 ef d8 d2 08 fd 37  1a ee 94 3c b8 10 f8 0c  |.......7...<....|
00000100  60 90 a3 24 16 75 49 73  5e 43 a8 fb 5d 67 ed a5  |`..$.uIs^C..]g..|
00000110  8b 43 53 f5 e0 81 f2 ab  d8 93 a9 86 b1 af e9 a0  |.CS.............|
00000120  10 93 46 e2 3b 3d ee c1  be 9e 28 90 ed ea 2d 3b  |..F.;=....(...-;|
00000130  92 76 dd ae 14 6b 3b 7e  ae e9 73 11 88 39 55 5b  |.v...k;~..s..9U[|
00000140  87 9d d2 11 78 32 ff 72  5a ab 54 63 31 95 69 52  |....x2.rZ.Tc1.iR|
00000150  ad a1 f2 40 39 a7 18 ab  5d 17 a7 5d 1b 67 3d 39  |...@9...]..].g=9|
00000160  ae f2 6d 0f 7c 18 83 46  f1 a6 77 24 cd 38 c4 d0  |..m.|..F..w$.8..|
00000170  97 6d f9 9b 3a ad f7 af  04 6e d9 87 fe e9 78 06  |.m..:....n....x.|
00000180  0f 01 e4 af 3c 57 a3 21  a7 2a ea 06 fb ee f9 25  |....<W.!.*.....%|
00000190  ec f2 1c f1 a9 f1 dd 8c  f2 17 0a 57 df 5b 62 84  |...........W.[b.|
000001a0  8f ac d1 39 32 6e d9 3d  22 6a 94 34 4c 97 e0 fe  |...92n.="j.4L...|
000001b0  18 21 80 cd af 2e bb ed  2f 3f 92 4a d1 a0 00 fe  |.!....../?.J....|
000001c0  ff ff 82 fe ff ff 3f 00  00 00 e0 84 4a 00 00 fe  |......?.....J...|
000001d0  ff ff 05 fe ff ff 30 85  4a 00 77 e6 97 07 00 00  |......0.J.w.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by ranch hand on 2010-09-15
What is your output for;
```

grub-install -v

```
?

Looks like grub0.97 to me.

---

### Post by Ambij on 2010-09-16
Hi,

It is GRUB 1.98 version. Should I have done something differently?

```
grub-install -v
grub-install (GRUB) 1.98+20100804-4ubuntu4

```


Thanks.

---

### Post by VMC on 2010-09-16
> **Ambij said:**
> Hi,

It is GRUB 1.98 version. Should I have done something differently?

```
grub-install -v
grub-install (GRUB) 1.98+20100804-4ubuntu4

```


Thanks.

Is that output from the livecd or sda6? Also output this from sda6:


```
cat /etc/hosts
```

---

### Post by ranch hand on 2010-09-16
> **Ambij said:**
> Hi,

It is GRUB 1.98 version. Should I have done something differently?

```
grub-install -v
grub-install (GRUB) 1.98+20100804-4ubuntu4

```
Thanks.
You have updated from a 10.04 that is updated from 9.10 which was updated from 9.04 haven't you?

You have no /boot/grub/grub.cfg file, which is what grub1.98 generates, you do have a /boot/grub/menu.lst which is generated by grub0.97.  This is the result of upgrading fro ma grub-legacy using OS to a grub2 using OS and it has finally bitten you in the butt.

Get ye to a console and with a good connection,
```

sudo apt-get purge grub grub-pc grub-common

```
Then delete /boot/grub (not /boot, just the sub directory /boot/grub)

Then;
```

sudo apt-get install grub-pc grub-common

```

---

### Post by Ambij on 2010-09-17
Done, but it say GRUB installation failed.

---

### Post by ranch hand on 2010-09-17
This does not sound good.

Rerun the boot info script and post the results.

---

### Post by Ambij on 2010-09-17
Hi,

I booted from a live Ubuntu 10.10 CD, the ran the following.

sudo apt-get purge grub grub-pc grub-common

I suspect I may be updating/purge grub of the live cd instead of the grub on my /dev/sda6.

Later I deleted /boot/grub from my /dev/sda6.

Then ran "sudo apt-get install grub-pc grub-common" which shows me menu to update, I select my hard disk, and then it shows error message "GRUB installation failed.".

---

### Post by quixote on 2010-09-17
I know it sounds kind of useless to suggest "try it again" since you already have.  Several times. :(  However, that *ought* to work, dammit!  So, try it again, but maybe a bit differently, following the instructions at [Grub2 Recovery, Command Line and Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode"), which is a different section of the same link ronparent gave earlier.

You're an old hand at this, so you probably don't need any clarification of the instructions, but if anything's not clear, you know where to find us :D.

---

