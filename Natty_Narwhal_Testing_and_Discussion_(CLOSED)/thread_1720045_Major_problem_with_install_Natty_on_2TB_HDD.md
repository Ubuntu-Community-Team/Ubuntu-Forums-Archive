---
title: "Major problem with install Natty on 2TB HDD"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by 8jwong14 on 2011-04-02
Hi.  I've tried installing Natty on a 2TB HDD that I have previously used with Ubuntu 11.04 Alpha 3.  I used gparted to delete the partitions on that HDD and another one of my 2TB HDDs.  I installed Windows 7 on the second one with both.  Afterwards, I tried installing Natty on the first 2TB HDD but I get the following warning:

/dev/sda contains GPT signatures, indicating that is has a GPT table, as it should. Perhaps it was corrupted - possbily by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?  

Pressing Yes and then No doesn't do a thing.  The message stays.

Now Windows won't boot and gives me an error message while Ubuntu won't install.  Please help.

---

### Post by oldfred on 2011-04-02
Windows will not boot from gpt unless you are using UEFI not BIOS. Ubuntu is fine with gpt. So do you want gpt or MBR(msdos) on the Ubuntu drive? Except for my one windows drive, all new drives will be gpt, just because it is a bit better and no logical partitions.

To see where everything is at:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by 8jwong14 on 2011-04-02
> **oldfred said:**
> Windows will not boot from gpt unless you are using UEFI not BIOS. Ubuntu is fine with gpt. So do you want gpt or MBR(msdos) on the Ubuntu drive? Except for my one windows drive, all new drives will be gpt, just because it is a bit better and no logical partitions.

To see where everything is at:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

I got rid of windows since it was having issues.  I just want Ubuntu on the 1st drive.  I want to isntall it normally as if nothing had happened.

---

### Post by 8jwong14 on 2011-04-03
> **oldfred said:**
> Windows will not boot from gpt unless you are using UEFI not BIOS. Ubuntu is fine with gpt. So do you want gpt or MBR(msdos) on the Ubuntu drive? Except for my one windows drive, all new drives will be gpt, just because it is a bit better and no logical partitions.

To see where everything is at:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Ok.  Here is the code:



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 34 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048     7,815,167     7,813,120 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34         1,987         1,954 Bios Boot Partition
/dev/sdb2           1,988 3,881,880,894 3,881,878,907 Linux or Data
/dev/sdb3   3,881,880,895 3,907,029,118    25,148,224 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a7582673-45ab-450f-8fb9-37895e555d5c   ext2                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb2        b131d9f7-74a1-4c79-97c4-50144e3adc1c   ext4                                     
/dev/sdb3        c5de6079-74ca-4ac1-9339-41a3b9ff4449   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=b131d9f7-74a1-4c79-97c4-50144e3adc1c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=c5de6079-74ca-4ac1-9339-41a3b9ff4449 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


1048.1GB: boot/grub/core.img
 713.3GB: boot/initrd.img-2.6.38-7-generic
1048.1GB: boot/vmlinuz-2.6.38-7-generic
 713.3GB: initrd.img
1048.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 23 00 00 00  00 00 00 00 63 00 20 08  |....#.......c. .|
00000200

```I'm going to remove the Windows and the second hardrivee with ti eventually.  I'll just keep Ubuntu on the first one if I can fix the problem.

Thanks for helping.

Also, how do I unmark this thread as solved?  Because isn't.

---

### Post by oldfred on 2011-04-03
That core image cannot be found may not be a problem as the old version of boot script did not parse the bios_grub partition.

But you do not have a grub.cfg file? 

Does your system start to boot and give a grub> command? You may be able to manually boot if so.

I prefer small system partitions of 20-25 GB (even with 2TB you do not need more) and large data partitions. You can install with the rest of the drive as /home or create data partition(s) to hold all your data. Then system partition is small and all operating system files are close to each other on drive.

One or two others with very large drives and system files scattered all over had issues booting, so small system avoids that issue. But I think that issue is related to some BIOS settings, not Ubuntu.

If you have no data to save I would reinstall with a 25GB /, 50GB /home and the rest as data. You do not even have to partition yet until you decide what data will go where. If also running windows you will want share NTFS data partition so you do not write into the windows system partition. You can read from windows but should not write into it (unless doing repairs).

I do not know how to turn off solved. But will check if you have posted several times a day. Others may not.

---

