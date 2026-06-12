---
title: "grub-pc doesn't find good Array in raid device"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by reyman on 2010-09-12
Binary package hint: grub2
Bug report here for last update : [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/635706]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/635706")

With the last upgrade on maverick, i have problem to upgrade my grub2, it seem grub-prob not recognize my raid, and the device on the raid :/

I have raid on two disk /sda and /sdb , my computer is dell m6500 Q820

My habitual choice is _ARRAY , /dm0 which point on the abstract raid device (see the screenshoot of upgrade box of grub2 [here on bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/635706")) ... grub-prob doesn't find ...

So i'm trying to choice an another option in menu, like /dm6 on RAID ARRAY6, but same problem ...

After each choice terminal says :
/usr/sbin/grub-probe error: cannot find a GRUB drive for /dev/mapper/blablabla_ARRAY6: check your device.map

I'm retrying with a total purge on grub2 + grub-pc, then reinstall, but same problem

My grub2 boot is broken since this update, i'm booting on maverick with super grub on usb disk :/

_***Update on 12/09 :** *_

device.map don't exist, so i create device.map with sudo grub-mkdevicemap --no-floppy

Result is here, generic Array is present, but grub-probe don't find him  : 

(hd0)   /dev/disk/by-id/ata-ST9500420ASG_5VJ4LQ5W
(hd1)   /dev/disk/by-id/ata-ST9500420ASG_5VJ4M2E5
(hd2)   /dev/mapper/isw_cjffbfddic_ARRAY/boot/grub/device.map

**same error : **
Paramétrage de grub-pc (1.98+20100804-4ubuntu6) ...
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.

**Thx a lot for your help !**
S.R

**grub-pc:**
  Installé*: 1.98+20100804-4ubuntu6
  Candidat*: 1.98+20100804-4ubuntu6
 Table de version*:
 *** 1.98+20100804-4ubuntu6 0
        500 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main amd64 Packages
        100 /var/lib/dpkg/status

**sudo blkid**

/dev/mapper/isw_cjffbfddic_ARRAY1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07DA-040A" TYPE="vfat" 
/dev/mapper/isw_cjffbfddic_ARRAY2: LABEL="RM-CM-)servM-CM-) au systM-CM-(me" UUID="5EDCF511DCF4E465" TYPE="ntfs" 
/dev/mapper/isw_cjffbfddic_ARRAY3: UUID="98EEFF19EEFEEE7E" TYPE="ntfs" 
/dev/mapper/isw_cjffbfddic_ARRAY5: UUID="38109D261F16B878" TYPE="ntfs" 
/dev/mapper/isw_cjffbfddic_ARRAY6: UUID="96402ebb-f5ac-4a63-8574-4adc8002d24c" TYPE="ext4" 
/dev/mapper/isw_cjffbfddic_ARRAY7: UUID="bfb07099-79e0-4fa5-8d42-e486906157f4" TYPE="ext4" 
/dev/mapper/isw_cjffbfddic_ARRAY8: UUID="6b0d7554-1799-422c-b425-77bfbb389888" TYPE="swap" 
/dev/sda: TYPE="isw_raid_member" 
/dev/sdb: TYPE="isw_raid_member" 


**Result for BootInfo Script :**

```


   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97-os.1 is installed in the MBR of /dev/sda and looks on boot drive 
    #2 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97-os.1 is installed in the MBR of /dev/mapper/isw_cjffbfddic_ARRAY 
    and looks on boot drive #2 in partition #1 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''
mount: type inconnu de système de fichiers ''

isw_cjffbfddic_ARRAY1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

isw_cjffbfddic_ARRAY2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

isw_cjffbfddic_ARRAY3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

isw_cjffbfddic_ARRAY4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_cjffbfddic_ARRAY5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, 
                       isw_cjffbfddic_ARRAY5 starts at sector 0. But 
                       according to the info from fdisk, 
                       isw_cjffbfddic_ARRAY5 starts at sector 84405573.
    Operating System:  
    Boot files/dirs:   

isw_cjffbfddic_ARRAY6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /etc/fstab

isw_cjffbfddic_ARRAY7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

isw_cjffbfddic_ARRAY8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       514,079       514,017  de Dell Utility
/dev/sda2    *        516,096       720,895       204,800   7 HPFS/NTFS
/dev/sda3             720,896    84,402,175    83,681,280   7 HPFS/NTFS
/dev/sda4          84,405,571   976,751,999   892,346,429   5 Extended
/dev/sda5          84,405,573   475,025,984   390,620,412   7 HPFS/NTFS
/dev/sda6         475,026,048   592,220,159   117,194,112  83 Linux
/dev/sda7         592,220,223   952,750,889   360,530,667  83 Linux
/dev/sda8         952,750,953   976,751,999    24,001,047  82 Linux swap / Solaris


Drive: isw_cjffbfddic_ARRAY ___________________ _____________________________________________________

Disque /dev/mapper/isw_cjffbfddic_ARRAY: 500.1 Go, 500104826880 octets
255 têtes, 63 secteurs/piste, 60800 cylindres, total 976767240 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_cjffbfddic_ARRAY1                 63       514,079       514,017  de Dell Utility
/dev/mapper/isw_cjffbfddic_ARRAY2   *        516,096       720,895       204,800   7 HPFS/NTFS
/dev/mapper/isw_cjffbfddic_ARRAY3            720,896    84,402,175    83,681,280   7 HPFS/NTFS
/dev/mapper/isw_cjffbfddic_ARRAY4         84,405,571   976,751,999   892,346,429   5 Extended
/dev/mapper/isw_cjffbfddic_ARRAY5         84,405,573   475,025,984   390,620,412   7 HPFS/NTFS
/dev/mapper/isw_cjffbfddic_ARRAY6        475,026,048   592,220,159   117,194,112  83 Linux
/dev/mapper/isw_cjffbfddic_ARRAY7        592,220,223   952,750,889   360,530,667  83 Linux
/dev/mapper/isw_cjffbfddic_ARRAY8        952,750,953   976,751,999    24,001,047  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_cjffbfddic_ARRAY1 07DA-040A                              vfat       DellUtility                   
/dev/mapper/isw_cjffbfddic_ARRAY2 5EDCF511DCF4E465                       ntfs       Réservé au système         
/dev/mapper/isw_cjffbfddic_ARRAY3 98EEFF19EEFEEE7E                       ntfs                                     
/dev/mapper/isw_cjffbfddic_ARRAY5 38109D261F16B878                       ntfs                                     
/dev/mapper/isw_cjffbfddic_ARRAY6 96402ebb-f5ac-4a63-8574-4adc8002d24c   ext4                                     
/dev/mapper/isw_cjffbfddic_ARRAY7 bfb07099-79e0-4fa5-8d42-e486906157f4   ext4                                     
/dev/mapper/isw_cjffbfddic_ARRAY8 6b0d7554-1799-422c-b425-77bfbb389888   swap                                     
/dev/mapper/isw_cjffbfddic_ARRAY: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
error: /dev/mapper/isw_cjffbfddic_ARRAY4: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory
error: /dev/sda7: No such file or directory
error: /dev/sda8: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_cjffbfddic_ARRAY
isw_cjffbfddic_ARRAY1
isw_cjffbfddic_ARRAY2
isw_cjffbfddic_ARRAY3
isw_cjffbfddic_ARRAY5
isw_cjffbfddic_ARRAY6
isw_cjffbfddic_ARRAY7
isw_cjffbfddic_ARRAY8

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/isw_cjffbfddic_ARRAY6 /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/mapper/isw_cjffbfddic_ARRAY7 /home                    ext4       (rw,commit=0)
/dev/mapper/isw_cjffbfddic_ARRAY5 /media/38109D261F16B878  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


======================= isw_cjffbfddic_ARRAY6/etc/fstab: =======================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/mapper/isw_cjffbfddic_ARRAY6	/	ext4	errors=remount-ro	0	1
/dev/mapper/isw_cjffbfddic_ARRAY7	/home	ext4	defaults	0	2
/dev/mapper/isw_cjffbfddic_ARRAY5	/media/38109D261F16B878	ntfs-3g	defaults,nosuid,nodev,locale=fr_FR.utf8	0	0
/dev/mapper/isw_cjffbfddic_ARRAY8	none	swap	sw	0	0



=========== isw_cjffbfddic_ARRAY6: Location of files loaded by Grub: ===========


 243.8GB: boot/initrd.img-2.6.31-14-generic
 255.5GB: boot/initrd.img-2.6.35-19-generic
 255.5GB: boot/initrd.img-2.6.35-20-generic
 243.7GB: boot/vmlinuz-2.6.31-14-generic
 256.9GB: boot/vmlinuz-2.6.35-19-generic
 245.2GB: boot/vmlinuz-2.6.35-20-generic
 255.5GB: initrd.img
 255.5GB: initrd.img.old
 245.2GB: vmlinuz
 256.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sda7


Unknown BootLoader  on sda8


Unknown BootLoader  on isw_cjffbfddic_ARRAY4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: Aucun fichier ou dossier de ce type
hexdump: /dev/sda1: Aucun fichier ou dossier de ce type
hexdump: /dev/sda2: Aucun fichier ou dossier de ce type
hexdump: /dev/sda2: Aucun fichier ou dossier de ce type
hexdump: /dev/sda3: Aucun fichier ou dossier de ce type
hexdump: /dev/sda3: Aucun fichier ou dossier de ce type
hexdump: /dev/sda4: Aucun fichier ou dossier de ce type
hexdump: /dev/sda4: Aucun fichier ou dossier de ce type
hexdump: /dev/sda5: Aucun fichier ou dossier de ce type
hexdump: /dev/sda5: Aucun fichier ou dossier de ce type
hexdump: /dev/sda6: Aucun fichier ou dossier de ce type
hexdump: /dev/sda6: Aucun fichier ou dossier de ce type
hexdump: /dev/sda7: Aucun fichier ou dossier de ce type
hexdump: /dev/sda7: Aucun fichier ou dossier de ce type
hexdump: /dev/sda8: Aucun fichier ou dossier de ce type
hexdump: /dev/sda8: Aucun fichier ou dossier de ce type
hexdump: /dev/mapper/isw_cjffbfddic_ARRAY4: Aucun fichier ou dossier de ce type
hexdump: /dev/mapper/isw_cjffbfddic_ARRAY4: Aucun fichier ou dossier de ce type
```

---

### Post by ronparent on 2010-09-12
I'm totally confused by your results script. It show the original grub boot loader on both sda and /dev/mapper/isw_cjffbfddic_ARRAY (the latter is where it should be located). Maybe a reinstall grub 2 is in order.

Open a terminal in a live cd and enter:

> sudo mount /dev/mapper/isw_cjffbfddic_ARRAY6 /mnt

sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_cjffbfddic_ARRAY

I would cut and paste these commands.

For your reference, the following contains most of what you may need to know about grub 2: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Let us know how you make out!):P

---

### Post by reyman on 2010-09-12
Tks for your help about this "grrrrrrub" problem
And i already try to apt-get remove --purge grub* then reinstall; but same problem.
 
Result is same with your cmd : 

```
sudo mount /dev/mapper/isw_cjffbfddic_ARRAY6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_cjffbfddic_ARRAY 
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

---

### Post by ranch hand on 2010-09-12
I actually think that installing grub-pc and grub common would be a good idea.

Your boot info script is indicating that you are  using grub-legacy (grub0.97).

I would purge what ever grub you have and delete /boot/grub and start over with a clean grub installation.

---

### Post by ronparent on 2010-09-12
What are the contents of your /boot, /boot/grub and /dev/dm*?

---

### Post by reyman on 2010-09-12
> **ranch hand said:**
> I actually think that installing grub-pc and grub common would be a good idea.

Your boot info script is indicating that you are  using grub-legacy (grub0.97).

I would purge what ever grub you have and delete /boot/grub and start over with a clean grub installation.

I remove /boot/grub, but
How i can remove **totally** grub on MBR ? Because removing grub2 not remove old grub mbr install : 

```
=> Grub 0.97-os.1 is installed in the MBR of /dev/mapper/isw_cjffbfddic_ARRAY 
    and looks on boot drive #2 in partition #1 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.
```

```

ls /boot/
abi-2.6.31-14-generic  config-2.6.31-14-generic  initrd.img-2.6.31-14-generic  memtest86+.bin                System.map-2.6.35-19-generic  vmcoreinfo-2.6.35-19-generic  vmlinuz-2.6.35-19-generic
abi-2.6.35-19-generic  config-2.6.35-19-generic  initrd.img-2.6.35-19-generic  memtest86+_multiboot.bin      System.map-2.6.35-20-generic  vmcoreinfo-2.6.35-20-generic  vmlinuz-2.6.35-20-generic
abi-2.6.35-20-generic  config-2.6.35-20-generic  initrd.img-2.6.35-20-generic  System.map-2.6.31-14-generic  vmcoreinfo-2.6.31-14-generic  vmlinuz-2.6.31-14-generic

ls /dev/dm*
/dev/dm-0  /dev/dm-1  /dev/dm-3  /dev/dm-4  /dev/dm-5  /dev/dm-6  /dev/dm-7  /dev/dm-8
```

---

### Post by ranch hand on 2010-09-12
After you;
```

sudo apt-get purge grub grub-pc grub-common

```
and delete /boot/grub
Then you need to;
```

sudo apt-get install grub-pc grub-common

```
This should install it on the MBR as part of installation.

To be sure that it has you can do it again manually;
```

sudo grub-install /dev/sda

```
Do make sure that you have a /boot/grub/device.map that is correct, as you did before.

---

### Post by v1ad on 2010-09-12
the grub boot directory will always be /boot. if you are currently booting off usb or live cd then:

```

mkdir /target
sudo mount /dev/mapper/isw_beeaakeeaa_five5 /target/  <-- your are info, you can use mnt instead of target your call
sudo mount --bind /dev /target/dev/
sudo mount -t proc proc /target/proc/
sudo mount -t sysfs sys /target/sys/
sudo cp /etc/resolv.conf /target/etc/resolv.conf 
sudo chroot /target/
apt-get update
apt-get --purge remove grub-pc
apt-get install grub-pc
update-grub
grub --no-curses
 grub> device (hd0) /dev/mapper/isw_beeaakeeaa_five <!--Put you info-->
 grub> find /boot/grub/stage1

```

---

### Post by ronparent on 2010-09-12
Grub on MBR is no problem if we can get grub 2 to overwrite it (should happen normally with grub reinstall).

The only other abnormally I notice is an earlier kernel (karmic) in boot. 

There are  other methods in the reference I gave you that we can employ. Which live cd are you using?

This is a bit confusing since a grub reinstall for the version we are trying to reinstall to should overwrite and replace anything else there?

Ranch hand - the grub install for a raid system has to be to the root array not one of the drives in the array.
Vlad: there is no stage1 for grub 2 (grub-pc)

---

### Post by reyman on 2010-09-12
> **ronparent said:**
> Grub on MBR is no problem if we can get grub 2 to overwrite it (should happen normally with grub reinstall).

The only other abnormally I notice is an earlier kernel (karmic) in boot. 

There are  other methods in the reference I gave you that we can employ. Which live cd are you using?

This is a bit confusing since a grub reinstall for the version we are trying to reinstall to should overwrite and replace anything else there?

Ranch hand - the grub install for a raid system has to be to the root array not one of the drives in the array.
Vlad: there is no stage1 for grub 2 (grub-pc)

Yes, normally grub 2 overwrite grub isn't it ?
I'm using latest maverick dev, i'm not on a live cd,  i boot with supergrub :/

---

### Post by ronparent on 2010-09-12
Ah ha. You are in maverick thru a grub disk! Great, follow ranch hand's instructions except at grub-install write:

> sudo grub-install /dev/mapper/isw_cjffbfddic_ARRAY

I think that will do it.

Note: in the prior post where I gave you the grub install from the live cd, I had inadvertently left a space at the end of '/dev/mapper/isw_cjffbfddic_ARRAY ' - that could have messed us up.:lolflag:

---

### Post by reyman on 2010-09-12
> **ranch hand said:**
> After you;
```

sudo apt-get purge grub grub-pc grub-common

```
and delete /boot/grub
Then you need to;
```

sudo apt-get install grub-pc grub-common

```
This should install it on the MBR as part of installation.

To be sure that it has you can do it again manually;
```

sudo grub-install /dev/sda

```
Do make sure that you have a /boot/grub/device.map that is correct, as you did before.

Problem is during configuration of grub-pc, i have the choice between : 
/dev/sda ( 500go)
/dev/sdb (500 go)
/dev/dm-1 (ARRAY -> front end of raid 1 500go *2 )
/dev/dm-6 ( ARRAY6 -> my / )

but if _i choose one , or all_ of this option, i have the same error : 

```
 Creating config file /etc/default/grub with new version
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

So i'm trying to create device.map with grub-mkdevicemap --no-floppy
My device map is : 
```

(hd0)   /dev/disk/by-id/ata-ST9500420ASG_5VJ4LQ5W
(hd1)   /dev/disk/by-id/ata-ST9500420ASG_5VJ4M2E5
(hd2)   /dev/mapper/isw_cjffbfddic_ARRAY
```

I reconfigure grub with aptitude reinstall grub-pc then, SAME error :(
Failed on installation on /dev/dm1 etc ... but this time device.map exist, so i don't understand where is this problem ?!

```
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

I'm trying to install manualy ... and tadam ! 

```
 sudo grub-install /dev/mapper/isw_cjffbfddic_ARRAY
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

---

### Post by ktp on 2010-09-12
ignore

---

### Post by ronparent on 2010-09-12
Some thing we are not seeing here. Again, what are the contents of your /boot, /boot/grub and /dev/dm*?

10.10 is using an evolved set of symbolic links for designating the raid devices. I don't know where they are going, but, they are listed as dm0, dm1, etc.

Also, I am not grasping the meaning of '/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6'. It seem to imply that grub is installed elsewhere - but where? and why is the install grub not fixing?

---

### Post by reyman on 2010-09-12
> **ronparent said:**
> Some thing we are not seeing here. Again, what are the contents of your /boot, /boot/grub and /dev/dm*?

10.10 is using an evolved set of symbolic links for designating the raid devices. I don't know where they are going, but, they are listed as dm0, dm1, etc.

Also, I am not grasping the meaning of '/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6'. It seem to imply that grub is installed elsewhere - but where? and why is the install grub not fixing?

```

 ll /boot

total 51892
-rw-r--r-- 1 root root   623709 2009-10-16 18:12 abi-2.6.31-14-generic
-rw-r--r-- 1 root root   700686 2010-08-29 09:25 abi-2.6.35-19-generic
-rw-r--r-- 1 root root   700720 2010-09-03 21:25 abi-2.6.35-20-generic
-rw-r--r-- 1 root root   105768 2009-10-16 18:12 config-2.6.31-14-generic
-rw-r--r-- 1 root root   122536 2010-08-29 09:25 config-2.6.35-19-generic
-rw-r--r-- 1 root root   122593 2010-09-03 21:25 config-2.6.35-20-generic
drwxr-xr-x 3 root root     4096 2010-09-12 19:44 grub
-rw-r--r-- 1 root root  8459115 2010-04-21 23:21 initrd.img-2.6.31-14-generic
-rw-r--r-- 1 root root 11247367 2010-09-08 09:28 initrd.img-2.6.35-19-generic
-rw-r--r-- 1 root root 11246138 2010-09-09 10:13 initrd.img-2.6.35-20-generic
-rw-r--r-- 1 root root   165084 2010-07-05 10:41 memtest86+.bin
-rw-r--r-- 1 root root   167264 2010-07-05 10:41 memtest86+_multiboot.bin
-rw-r--r-- 1 root root  2130808 2009-10-16 18:12 System.map-2.6.31-14-generic
-rw-r--r-- 1 root root  2340443 2010-08-29 09:25 System.map-2.6.35-19-generic
-rw-r--r-- 1 root root  2341508 2010-09-03 21:25 System.map-2.6.35-20-generic
-rw-r--r-- 1 root root     1336 2009-10-16 18:18 vmcoreinfo-2.6.31-14-generic
-rw-r--r-- 1 root root     1335 2010-08-29 09:26 vmcoreinfo-2.6.35-19-generic
-rw-r--r-- 1 root root     1335 2010-09-03 21:32 vmcoreinfo-2.6.35-20-generic
-rw-r--r-- 1 root root  3941696 2009-10-16 18:12 vmlinuz-2.6.31-14-generic
-rw-r--r-- 1 root root  4333968 2010-08-29 09:25 vmlinuz-2.6.35-19-generic
-rw-r--r-- 1 root root  4334672 2010-09-03 21:25 vmlinuz-2.6.35-20-generic

ll /boot/grub/
total 1576
-rw-r--r-- 1 root root  8208 2010-09-12 19:44 915resolution.mod
-rw-r--r-- 1 root root 10488 2010-09-12 19:44 acpi.mod
-rw-r--r-- 1 root root  4536 2010-09-12 19:44 affs.mod
-rw-r--r-- 1 root root  4896 2010-09-12 19:44 afs_be.mod
-rw-r--r-- 1 root root  4872 2010-09-12 19:44 afs.mod
-rw-r--r-- 1 root root  1048 2010-09-12 19:44 aout.mod
-rw-r--r-- 1 root root  8036 2010-09-12 19:44 ata.mod
-rw-r--r-- 1 root root  2228 2010-09-12 19:44 ata_pthru.mod
-rw-r--r-- 1 root root  2672 2010-09-12 19:44 at_keyboard.mod
-rw-r--r-- 1 root root  4792 2010-09-12 19:44 befs_be.mod
-rw-r--r-- 1 root root  4776 2010-09-12 19:44 befs.mod
-rw-r--r-- 1 root root  4288 2010-09-12 19:44 biosdisk.mod
-rw-r--r-- 1 root root  2400 2010-09-12 19:44 bitmap.mod
-rw-r--r-- 1 root root  2904 2010-09-12 19:44 bitmap_scale.mod
-rw-r--r-- 1 root root  2020 2010-09-12 19:44 blocklist.mod
-rw-r--r-- 1 root root   512 2010-09-12 19:44 boot.img
-rw-r--r-- 1 root root  2568 2010-09-12 19:44 boot.mod
-rw-r--r-- 1 root root 19612 2010-09-12 19:44 bsd.mod
-rw-r--r-- 1 root root  1964 2010-09-12 19:44 bufio.mod
-rw-r--r-- 1 root root  2388 2010-09-12 19:44 cat.mod
-rw-r--r-- 1 root root   512 2010-09-12 19:44 cdboot.img
-rw-r--r-- 1 root root  2476 2010-09-12 19:44 chain.mod
-rw-r--r-- 1 root root  1340 2010-09-12 19:44 cmostest.mod
-rw-r--r-- 1 root root  2144 2010-09-12 19:44 cmp.mod
-rw-r--r-- 1 root root  2033 2010-09-12 19:44 command.lst
-rw-r--r-- 1 root root  1784 2010-09-12 19:44 configfile.mod
-rw-r--r-- 1 root root  2864 2010-09-12 19:44 cpio.mod
-rw-r--r-- 1 root root  1608 2010-09-12 19:44 cpuid.mod
-rw-r--r-- 1 root root  1784 2010-09-12 19:44 crc.mod
-rw-r--r-- 1 root root   825 2010-09-12 19:44 crypto.lst
-rw-r--r-- 1 root root  4428 2010-09-12 19:44 crypto.mod
-rw-r--r-- 1 root root  4052 2010-09-12 19:44 cs5536.mod
-rw-r--r-- 1 root root  1824 2010-09-12 19:44 datehook.mod
-rw-r--r-- 1 root root  2316 2010-09-12 19:44 date.mod
-rw-r--r-- 1 root root  1241 2010-09-12 19:44 datetime.mod
-rw-r--r-- 1 root root   135 2010-09-12 19:42 device.map
-rw-r--r-- 1 root root   512 2010-09-12 19:44 diskboot.img
-rw-r--r-- 1 root root  1896 2010-09-12 19:44 dm_nv.mod
-rw-r--r-- 1 root root  5488 2010-09-12 19:44 drivemap.mod
-rw-r--r-- 1 root root  1920 2010-09-12 19:44 echo.mod
-rw-r--r-- 1 root root  6472 2010-09-12 19:44 efiemu32.o
-rw-r--r-- 1 root root 11034 2010-09-12 19:44 efiemu64.o
-rw-r--r-- 1 root root 24168 2010-09-12 19:44 efiemu.mod
-rw-r--r-- 1 root root  4404 2010-09-12 19:44 elf.mod
-rw-r--r-- 1 root root  1636 2010-09-12 19:44 example_functional_test.mod
-rw-r--r-- 1 root root  5500 2010-09-12 19:44 ext2.mod
-rw-r--r-- 1 root root  3976 2010-09-12 19:44 extcmd.mod
-rw-r--r-- 1 root root  5932 2010-09-12 19:44 fat.mod
-rw-r--r-- 1 root root 11992 2010-09-12 19:44 font.mod
-rw-r--r-- 1 root root  2800 2010-09-12 19:44 fshelp.mod
-rw-r--r-- 1 root root   128 2010-09-12 19:44 fs.lst
-rw-r--r-- 1 root root  2508 2010-09-12 19:44 functional_test.mod
-rw-r--r-- 1 root root  1768 2010-09-12 19:44 gcry_arcfour.mod
-rw-r--r-- 1 root root  8144 2010-09-12 19:44 gcry_blowfish.mod
-rw-r--r-- 1 root root 35040 2010-09-12 19:44 gcry_camellia.mod
-rw-r--r-- 1 root root 17568 2010-09-12 19:44 gcry_cast5.mod
-rw-r--r-- 1 root root  2996 2010-09-12 19:44 gcry_crc.mod
-rw-r--r-- 1 root root 19280 2010-09-12 19:44 gcry_des.mod
-rw-r--r-- 1 root root  3268 2010-09-12 19:44 gcry_md4.mod
-rw-r--r-- 1 root root  4008 2010-09-12 19:44 gcry_md5.mod
-rw-r--r-- 1 root root  2636 2010-09-12 19:44 gcry_rfc2268.mod
-rw-r--r-- 1 root root 19204 2010-09-12 19:44 gcry_rijndael.mod
-rw-r--r-- 1 root root  9116 2010-09-12 19:44 gcry_rmd160.mod
-rw-r--r-- 1 root root 16652 2010-09-12 19:44 gcry_seed.mod
-rw-r--r-- 1 root root 18016 2010-09-12 19:44 gcry_serpent.mod
-rw-r--r-- 1 root root  8848 2010-09-12 19:44 gcry_sha1.mod
-rw-r--r-- 1 root root  3484 2010-09-12 19:44 gcry_sha256.mod
-rw-r--r-- 1 root root  5620 2010-09-12 19:44 gcry_sha512.mod
-rw-r--r-- 1 root root 11980 2010-09-12 19:44 gcry_tiger.mod
-rw-r--r-- 1 root root 39736 2010-09-12 19:44 gcry_twofish.mod
-rw-r--r-- 1 root root 24792 2010-09-12 19:44 gcry_whirlpool.mod
-rw-r--r-- 1 root root  3984 2010-09-12 19:44 gettext.mod
-rw-r--r-- 1 root root 38628 2010-09-12 19:44 gfxmenu.mod
-rw-r--r-- 1 root root 11280 2010-09-12 19:44 gfxterm.mod
-rw-r--r-- 1 root root  3720 2010-09-12 19:44 gptsync.mod
-rw-r--r-- 1 root root 10240 2010-09-12 19:44 grldr.img
-rw-r--r-- 1 root root  1024 2010-09-12 19:34 grubenv
-rw-r--r-- 1 root root  7828 2010-09-12 19:44 gzio.mod
-rw-r--r-- 1 root root  1460 2010-09-12 19:44 halt.mod
-rw-r--r-- 1 root root     0 2010-09-12 19:44 handler.lst
-rw-r--r-- 1 root root  4632 2010-09-12 19:44 hashsum.mod
-rw-r--r-- 1 root root  7440 2010-09-12 19:44 hdparm.mod
-rw-r--r-- 1 root root  1216 2010-09-12 19:44 hello.mod
-rw-r--r-- 1 root root  2488 2010-09-12 19:44 help.mod
-rw-r--r-- 1 root root  3244 2010-09-12 19:44 hexdump.mod
-rw-r--r-- 1 root root  6028 2010-09-12 19:44 hfs.mod
-rw-r--r-- 1 root root  5896 2010-09-12 19:44 hfsplus.mod
-rw-r--r-- 1 root root  2856 2010-09-12 19:44 iorw.mod
-rw-r--r-- 1 root root  6248 2010-09-12 19:44 iso9660.mod
-rw-r--r-- 1 root root  5844 2010-09-12 19:44 jfs.mod
-rw-r--r-- 1 root root  5944 2010-09-12 19:44 jpeg.mod
-rw-r--r-- 1 root root 29028 2010-09-12 19:44 kernel.img
-rw-r--r-- 1 root root  1980 2010-09-12 19:44 keystatus.mod
-rw-r--r-- 1 root root  5012 2010-09-12 19:44 linux16.mod
-rw-r--r-- 1 root root  8732 2010-09-12 19:44 linux.mod
-rw-r--r-- 1 root root  1024 2010-09-12 19:44 lnxboot.img
-rw-r--r-- 1 root root  5560 2010-09-12 19:44 loadenv.mod
drwxr-xr-x 2 root root  4096 2010-09-12 19:37 locale
-rw-r--r-- 1 root root  3032 2010-09-12 19:44 loopback.mod
-rw-r--r-- 1 root root  1300 2010-09-12 19:44 lsmmap.mod
-rw-r--r-- 1 root root  4168 2010-09-12 19:44 ls.mod
-rw-r--r-- 1 root root  4932 2010-09-12 19:44 lspci.mod
-rw-r--r-- 1 root root  6060 2010-09-12 19:44 lvm.mod
-rw-r--r-- 1 root root  2652 2010-09-12 19:44 mdraid.mod
-rw-r--r-- 1 root root  2080 2010-09-12 19:44 memdisk.mod
-rw-r--r-- 1 root root  2876 2010-09-12 19:44 memrw.mod
-rw-r--r-- 1 root root  4132 2010-09-12 19:44 minicmd.mod
-rw-r--r-- 1 root root  4336 2010-09-12 19:44 minix.mod
-rw-r--r-- 1 root root  8508 2010-09-12 19:44 mmap.mod
-rw-r--r-- 1 root root  2773 2010-09-12 19:44 moddep.lst
-rw-r--r-- 1 root root  2372 2010-09-12 19:44 msdospart.mod
-rw-r--r-- 1 root root 11436 2010-09-12 19:44 multiboot2.mod
-rw-r--r-- 1 root root 10488 2010-09-12 19:44 multiboot.mod
-rw-r--r-- 1 root root  6648 2010-09-12 19:44 nilfs2.mod
-rw-r--r-- 1 root root 98312 2010-09-12 19:44 normal.mod
-rw-r--r-- 1 root root  3536 2010-09-12 19:44 ntfscomp.mod
-rw-r--r-- 1 root root  9992 2010-09-12 19:44 ntfs.mod
-rw-r--r-- 1 root root 10556 2010-09-12 19:44 ohci.mod
-rw-r--r-- 1 root root  1688 2010-09-12 19:44 part_acorn.mod
-rw-r--r-- 1 root root  1672 2010-09-12 19:44 part_amiga.mod
-rw-r--r-- 1 root root  2112 2010-09-12 19:44 part_apple.mod
-rw-r--r-- 1 root root  2004 2010-09-12 19:44 part_bsd.mod
-rw-r--r-- 1 root root  2284 2010-09-12 19:44 part_gpt.mod
-rw-r--r-- 1 root root    82 2010-09-12 19:44 partmap.lst
-rw-r--r-- 1 root root  2096 2010-09-12 19:44 part_msdos.mod
-rw-r--r-- 1 root root  1792 2010-09-12 19:44 part_sun.mod
-rw-r--r-- 1 root root  1704 2010-09-12 19:44 part_sunpc.mod
-rw-r--r-- 1 root root    17 2010-09-12 19:44 parttool.lst
-rw-r--r-- 1 root root  4488 2010-09-12 19:44 parttool.mod
-rw-r--r-- 1 root root  1904 2010-09-12 19:44 password.mod
-rw-r--r-- 1 root root  2976 2010-09-12 19:44 password_pbkdf2.mod
-rw-r--r-- 1 root root  1328 2010-09-12 19:44 pbkdf2.mod
-rw-r--r-- 1 root root  1184 2010-09-12 19:44 pci.mod
-rw-r--r-- 1 root root  2472 2010-09-12 19:44 play.mod
-rw-r--r-- 1 root root  6620 2010-09-12 19:44 png.mod
-rw-r--r-- 1 root root  2664 2010-09-12 19:44 probe.mod
-rw-r--r-- 1 root root  1024 2010-09-12 19:44 pxeboot.img
-rw-r--r-- 1 root root  1332 2010-09-12 19:44 pxecmd.mod
-rw-r--r-- 1 root root  5588 2010-09-12 19:44 pxe.mod
-rw-r--r-- 1 root root  1400 2010-09-12 19:44 raid5rec.mod
-rw-r--r-- 1 root root  2812 2010-09-12 19:44 raid6rec.mod
-rw-r--r-- 1 root root  6216 2010-09-12 19:44 raid.mod
-rw-r--r-- 1 root root  1564 2010-09-12 19:44 read.mod
-rw-r--r-- 1 root root  1120 2010-09-12 19:44 reboot.mod
-rw-r--r-- 1 root root 38636 2010-09-12 19:44 regexp.mod
-rw-r--r-- 1 root root  9796 2010-09-12 19:44 reiserfs.mod
-rw-r--r-- 1 root root  4104 2010-09-12 19:44 relocator.mod
-rw-r--r-- 1 root root  4128 2010-09-12 19:44 scsi.mod
-rw-r--r-- 1 root root  2168 2010-09-12 19:44 search_fs_file.mod
-rw-r--r-- 1 root root  2336 2010-09-12 19:44 search_fs_uuid.mod
-rw-r--r-- 1 root root  2256 2010-09-12 19:44 search_label.mod
-rw-r--r-- 1 root root  2356 2010-09-12 19:44 search.mod
-rw-r--r-- 1 root root  4920 2010-09-12 19:44 serial.mod
-rw-r--r-- 1 root root   690 2010-09-12 19:44 setjmp.mod
-rw-r--r-- 1 root root  5524 2010-09-12 19:44 setpci.mod
-rw-r--r-- 1 root root  4104 2010-09-12 19:44 sfs.mod
-rw-r--r-- 1 root root  2220 2010-09-12 19:44 sleep.mod
-rw-r--r-- 1 root root  2888 2010-09-12 19:44 tar.mod
-rw-r--r-- 1 root root   124 2010-09-12 19:44 terminal.lst
-rw-r--r-- 1 root root  3476 2010-09-12 19:44 terminal.mod
-rw-r--r-- 1 root root 12740 2010-09-12 19:44 terminfo.mod
-rw-r--r-- 1 root root  5188 2010-09-12 19:44 test.mod
-rw-r--r-- 1 root root  2884 2010-09-12 19:44 tga.mod
-rw-r--r-- 1 root root  1675 2010-09-12 19:44 trig.mod
-rw-r--r-- 1 root root  1276 2010-09-12 19:44 true.mod
-rw-r--r-- 1 root root  5484 2010-09-12 19:44 udf.mod
-rw-r--r-- 1 root root  4672 2010-09-12 19:44 ufs1.mod
-rw-r--r-- 1 root root  4988 2010-09-12 19:44 ufs2.mod
-rw-r--r-- 1 root root  5800 2010-09-12 19:44 uhci.mod
-rw-r--r-- 1 root root  3428 2010-09-12 19:44 usb_keyboard.mod
-rw-r--r-- 1 root root  7876 2010-09-12 19:44 usb.mod
-rw-r--r-- 1 root root  5440 2010-09-12 19:44 usbms.mod
-rw-r--r-- 1 root root  3624 2010-09-12 19:44 usbtest.mod
-rw-r--r-- 1 root root  2736 2010-09-12 19:44 vbeinfo.mod
-rw-r--r-- 1 root root  6676 2010-09-12 19:44 vbe.mod
-rw-r--r-- 1 root root  3048 2010-09-12 19:44 vbetest.mod
-rw-r--r-- 1 root root  4788 2010-09-12 19:44 vga.mod
-rw-r--r-- 1 root root  2288 2010-09-12 19:44 vga_text.mod
-rw-r--r-- 1 root root  5500 2010-09-12 19:44 video_bochs.mod
-rw-r--r-- 1 root root  5744 2010-09-12 19:44 video_cirrus.mod
-rw-r--r-- 1 root root 18716 2010-09-12 19:44 video_fb.mod
-rw-r--r-- 1 root root    33 2010-09-12 19:44 video.lst
-rw-r--r-- 1 root root  5388 2010-09-12 19:44 video.mod
-rw-r--r-- 1 root root  3876 2010-09-12 19:44 videotest.mod
-rw-r--r-- 1 root root  5856 2010-09-12 19:44 xfs.mod
-rw-r--r-- 1 root root 31396 2010-09-12 19:44 xnu.mod
-rw-r--r-- 1 root root  1936 2010-09-12 19:44 xnu_uuid.mod
-rw-r--r-- 1 root root  6208 2010-09-12 19:44 zfsinfo.mod
-rw-r--r-- 1 root root 24384 2010-09-12 19:44 zfs.mod

 ll /dev/dm*

brw-rw---- 1 root disk 252, 0 2010-09-12 16:47 /dev/dm-0
brw-rw---- 1 root disk 252, 1 2010-09-12 16:47 /dev/dm-1
brw-rw---- 1 root disk 252, 3 2010-09-12 17:07 /dev/dm-3
brw-rw---- 1 root disk 252, 4 2010-09-12 16:47 /dev/dm-4
brw-rw---- 1 root disk 252, 5 2010-09-12 20:00 /dev/dm-5
brw-rw---- 1 root disk 252, 6 2010-09-12 16:47 /dev/dm-6
brw-rw---- 1 root disk 252, 7 2010-09-12 16:47 /dev/dm-7
brw-rw---- 1 root disk 252, 8 2010-09-12 16:47 /dev/dm-8

```

Don't understand too, why grub-probe ask me about ARRAY6 absolutely ?...

---

### Post by ronparent on 2010-09-12
For some reason the grub.cfg is missing? It should be there after a update-grub. what do you get if you run 'sudo update-grub'?

---

### Post by reyman on 2010-09-12
> **ronparent said:**
> For some reason the grub.cfg is missing? It should be there after a update-grub. what do you get if you run 'sudo update-grub'?

```
sudo update-grub

Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
```

Same error again :(
Hum, i'm taking advice of my pillow, perhaps tomorow i get an answer.

---

### Post by ranch hand on 2010-09-12
I do not use raid so don't know much about it.

That said, I would be trying to install grub on the MBR of sda and then putting the raid info into the menu entry.

This could be done with custom menus  or editing the /etc/default/grub files instruction string (I think).

---

### Post by ranch hand on 2010-09-12
This problem interests me to no end.

Ran a search and came up with this;
[http://www.linuxquestions.org/questions/linux-general-1/raid-and-grub-2-on-ubuntu-karmic-koala-788540/](http://www.linuxquestions.org/questions/linux-general-1/raid-and-grub-2-on-ubuntu-karmic-koala-788540/)

It might help particularly;
> 
Solved it. Grub gets its RAID information from /etc/mdadm/mdadm.conf. I  just needed to add the ARRAY definitions to it rather than having them  auto-detected.

Also found these, haven't looked at them but they looked like they may have some info;
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/525425](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/525425)
[https://answers.launchpad.net/ubuntu/lucid/+source/grub2](https://answers.launchpad.net/ubuntu/lucid/+source/grub2)

If they don't, you can blame my ignorance.

---

### Post by reyman on 2010-09-13
> **ranch hand said:**
> This problem interests me to no end.

Ran a search and came up with this;
[http://www.linuxquestions.org/questions/linux-general-1/raid-and-grub-2-on-ubuntu-karmic-koala-788540/](http://www.linuxquestions.org/questions/linux-general-1/raid-and-grub-2-on-ubuntu-karmic-koala-788540/)

It might help particularly;

Also found these, haven't looked at them but they looked like they may have some info;
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/525425](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/525425)
[https://answers.launchpad.net/ubuntu/lucid/+source/grub2](https://answers.launchpad.net/ubuntu/lucid/+source/grub2)

If they don't, you can blame my ignorance.

Thks for your help;

I have not /etc/mdadm/mdadm.conf and my raid run ok with older grub 2.
I'm retrying to add a line about ARRAY6 in my /boot/grub/device.map

```
(hd0)	/dev/disk/by-id/ata-ST9500420ASG_5VJ4LQ5W
(hd1)	/dev/disk/by-id/ata-ST9500420ASG_5VJ4M2E5
(hd2)	/dev/mapper/isw_cjffbfddic_ARRAY
(hd3)	/dev/mapper/isw_cjffbfddic_ARRAY6
(hd4)    /dev/mapper/isw_cjffbfddic_ARRAY7
```

And testing device.map with grub-probe : 

```
grub-probe --device-map=/boot/grub/device.map --target=drive /
grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.

grub-probe --device-map=/boot/grub/device.map --target=drive /home
grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY7.  Check your device.map.
```

Perhaps a bug in grube-probe ? :(

---

### Post by ronparent on 2010-09-13
You are correct, you do not have /etc/mdadm/mdadm because you are using a 'fakeraid'. You have /dev/mapper/ with your array and raid partitions listed. In 10.10 you should not be able to install boot loader to /dev/sda as it should be because that is not where it belongs.

It is becoming apparent to me that grub is not installed to the expected location. The results script finds a grub.cfg. But it isn't in ARRAY6? Since ARRAY6 is where youu have installed Maverick and it seems to be behaving properly I don't know how to account for it?????

Something I noticed on reexam. Boot info doesn't include grub.cfg? I'm not blaming it on a grub bug (say that fast) yet. I am installed on a raid 0 and have seen no such problem. Grub-probe is evidently, for some unknown reason not finding the grub installation? And that appears, as you have identified, to be the root cause of the problem. I will have to study the Grub references a again and get back to you. Maybe we have to sos herman?

edit: have you checked grub-probe options - ie grub-probe --help Especially -p -t

---

### Post by ronparent on 2010-09-13
> Please specify the module with the option `--modules' explicitly.

This message makes no sense. There is no '--modules' option for grub-probe?

---

### Post by reyman on 2010-09-13
> **ronparent said:**
> This message makes no sense. There is no '--modules' option for grub-probe?

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg795121.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg795121.html)

I'm trying some of this cmd : 

```
grub-probe -t drive /boot/grub
grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
```

```

sudo grub-probe -vvv -t drive /boot/grub

disk/raid.c:658: Scanning for RAID devices on disk hd0
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd0'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos8
kern/disk.c:245: Opening `hd0,msdos8'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos7
kern/disk.c:245: Opening `hd0,msdos7'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos6
kern/disk.c:245: Opening `hd0,msdos6'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos5
kern/disk.c:245: Opening `hd0,msdos5'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos3
kern/disk.c:245: Opening `hd0,msdos3'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos2
kern/disk.c:245: Opening `hd0,msdos2'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos1
kern/disk.c:245: Opening `hd0,msdos1'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos1'.
disk/raid.c:658: Scanning for RAID devices on disk hd1
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd1'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos8
kern/disk.c:245: Opening `hd1,msdos8'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos7
kern/disk.c:245: Opening `hd1,msdos7'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos6
kern/disk.c:245: Opening `hd1,msdos6'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos5
kern/disk.c:245: Opening `hd1,msdos5'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos3
kern/disk.c:245: Opening `hd1,msdos3'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos2
kern/disk.c:245: Opening `hd1,msdos2'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos1
kern/disk.c:245: Opening `hd1,msdos1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos1'.
disk/raid.c:658: Scanning for RAID devices on disk hd2
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd2'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos8
kern/disk.c:245: Opening `hd2,msdos8'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos7
kern/disk.c:245: Opening `hd2,msdos7'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos6
kern/disk.c:245: Opening `hd2,msdos6'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos5
kern/disk.c:245: Opening `hd2,msdos5'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos3
kern/disk.c:245: Opening `hd2,msdos3'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos2
kern/disk.c:245: Opening `hd2,msdos2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos1
kern/disk.c:245: Opening `hd2,msdos1'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos1'.
disk/raid.c:658: Scanning for RAID devices on disk hd3
kern/disk.c:245: Opening `hd3'...
grub-probe: info: the size of hd3 is 117194112.
kern/emu/hostdisk.c:594: opening the device `/dev/dm-5' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-5'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-5'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-5'
kern/disk.c:334: Closing `hd3'.
kern/disk.c:245: Opening `hd3'...
grub-probe: info: the size of hd3 is 117194112.
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
kern/disk.c:334: Closing `hd3'.
disk/raid.c:658: Scanning for RAID devices on disk hd4
kern/disk.c:245: Opening `hd4'...
grub-probe: info: the size of hd4 is 360530667.
kern/emu/hostdisk.c:594: opening the device `/dev/dm-6' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-6'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-6'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-6'
kern/disk.c:334: Closing `hd4'.
kern/disk.c:245: Opening `hd4'...
grub-probe: info: the size of hd4 is 360530667.
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
kern/disk.c:334: Closing `hd4'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0,msdos8'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd0,msdos8'.
kern/disk.c:245: Opening `hd0,msdos7'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd0,msdos7'.
kern/disk.c:245: Opening `hd0,msdos6'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd0,msdos6'.
kern/disk.c:245: Opening `hd0,msdos5'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd0,msdos5'.
kern/disk.c:245: Opening `hd0,msdos3'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd0,msdos3'.
kern/disk.c:245: Opening `hd0,msdos2'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd0,msdos2'.
kern/disk.c:245: Opening `hd0,msdos1'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd0,msdos1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1,msdos8'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd1,msdos8'.
kern/disk.c:245: Opening `hd1,msdos7'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd1,msdos7'.
kern/disk.c:245: Opening `hd1,msdos6'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd1,msdos6'.
kern/disk.c:245: Opening `hd1,msdos5'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd1,msdos5'.
kern/disk.c:245: Opening `hd1,msdos3'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd1,msdos3'.
kern/disk.c:245: Opening `hd1,msdos2'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd1,msdos2'.
kern/disk.c:245: Opening `hd1,msdos1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd1,msdos1'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2,msdos8'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd2,msdos8'.
kern/disk.c:245: Opening `hd2,msdos7'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd2,msdos7'.
kern/disk.c:245: Opening `hd2,msdos6'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd2,msdos6'.
kern/disk.c:245: Opening `hd2,msdos5'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd2,msdos5'.
kern/disk.c:245: Opening `hd2,msdos3'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd2,msdos3'.
kern/disk.c:245: Opening `hd2,msdos2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd2,msdos2'.
kern/disk.c:245: Opening `hd2,msdos1'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd2,msdos1'.
kern/disk.c:245: Opening `hd3'...
grub-probe: info: the size of hd3 is 117194112.
kern/disk.c:334: Closing `hd3'.
kern/disk.c:245: Opening `hd3'...
grub-probe: info: the size of hd3 is 117194112.
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
kern/disk.c:334: Closing `hd3'.
kern/disk.c:245: Opening `hd4'...
grub-probe: info: the size of hd4 is 360530667.
kern/disk.c:334: Closing `hd4'.
kern/disk.c:245: Opening `hd4'...
grub-probe: info: the size of hd4 is 360530667.
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
kern/disk.c:334: Closing `hd4'.
grub-probe: info: changing current directory to /dev.
grub-probe: info: changing current directory to snd.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to v4l.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to by-id.
grub-probe: info: changing current directory to cpu.
grub-probe: info: changing current directory to 15.
grub-probe: info: changing current directory to 14.
grub-probe: info: changing current directory to 13.
grub-probe: info: changing current directory to 12.
grub-probe: info: changing current directory to 11.
grub-probe: info: changing current directory to 10.
grub-probe: info: changing current directory to 9.
grub-probe: info: changing current directory to 8.
grub-probe: info: changing current directory to 7.
grub-probe: info: changing current directory to 6.
grub-probe: info: changing current directory to 5.
grub-probe: info: changing current directory to 4.
grub-probe: info: changing current directory to 3.
grub-probe: info: changing current directory to 2.
grub-probe: info: changing current directory to 1.
grub-probe: info: changing current directory to 0.
grub-probe: info: changing current directory to shm.
grub-probe: info: changing current directory to disk.
grub-probe: info: changing current directory to by-label.
grub-probe: info: changing current directory to by-uuid.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to by-id.
grub-probe: info: changing current directory to bsg.
grub-probe: info: changing current directory to char.
grub-probe: info: changing current directory to block.
grub-probe: info: changing current directory to pts.
grub-probe: info: changing current directory to mapper.
kern/emu/hostdisk.c:403: dm /dev/mapper/isw_cjffbfddic_ARRAY6 starts at 475026048
grub-probe: info: /dev/mapper/isw_cjffbfddic_ARRAY6 starts from 475026048.
grub-probe: info: opening the device hd3.
kern/disk.c:245: Opening `hd3'...
grub-probe: info: the size of hd3 is 117194112.
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
kern/disk.c:334: Closing `hd3'.
grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.

```


```

 sudo sh -x /usr/sbin/grub-install --no-floppy --grub-setup=/bin/true "$(grub-probe -t drive /boot/grub)"

grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
+ transform=s,x,x,
+ prefix=/usr
+ exec_prefix=/usr
+ sbindir=/usr/sbin
+ bindir=/usr/bin
+ libdir=/usr/lib
+ PACKAGE_NAME=GRUB
+ PACKAGE_TARNAME=grub
+ PACKAGE_VERSION=1.98+20100804-4ubuntu6
+ target_cpu=i386
+ platform=pc
+ host_os=linux-gnu
+ font=/usr/share/grub/ascii.pf2
+ echo grub/i386-pc
+ sed s,x,x,
+ pkglibdir=/usr/lib/grub/i386-pc
+ localedir=/usr/share/locale
+ basename /usr/sbin/grub-install
+ self=grub-install
+ echo grub-setup
+ sed s,x,x,
+ grub_setup=/usr/sbin/grub-setup
+ echo grub-mkimage
+ sed s,x,x,
+ grub_mkimage=/usr/bin/grub-mkimage
+ echo grub-probe
+ sed s,x,x,
+ grub_probe=/usr/sbin/grub-probe
+ echo grub-editenv
+ sed s,x,x,
+ grub_editenv=/usr/bin/grub-editenv
+ rootdir=
+ echo /boot/grub
+ sed s,x,x,
+ grub_prefix=/boot/grub
+ modules=
+ install_device=
+ no_floppy=
+ force_lba=
+ recheck=no
+ debug=no
+ debug_image=
+ [ i386-pc = i386-pc ]
+ disk_module=biosdisk
+ test 3 -gt 0
+ option=--no-floppy
+ shift
+ no_floppy=--no-floppy
+ test 2 -gt 0
+ option=--grub-setup=/bin/true
+ shift
+ echo --grub-setup=/bin/true
+ sed s/--grub-setup=//
+ grub_setup=/bin/true
+ test 1 -gt 0
+ option=
+ shift
+ test x != x
+ install_device=
+ test 0 -gt 0
+ . /usr/lib/grub/grub-mkconfig_lib
+ transform=s,x,x,
+ prefix=/usr
+ exec_prefix=/usr
+ datarootdir=/usr/share
+ datadir=/usr/share
+ bindir=/usr/bin
+ sbindir=/usr/sbin
+ echo grub
+ sed s,x,x,
+ pkgdatadir=/usr/share/grub
+ test x/usr/sbin/grub-probe = x
+ test x = x
+ echo grub-mkrelpath
+ sed s,x,x,
+ grub_mkrelpath=/usr/bin/grub-mkrelpath
+ which gettext
+ 
+ gettext=gettext
+ test x = x
+ test i386-pc != mips-yeeloong
+ echo install_device not specified.
install_device not specified.
+ usage
+ cat
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
+ [ i386-pc = i386-pc ]
+ cat
  --disk-module=MODULE    disk module to use
+ [ i386-pc = mips-yeeloong ]
+ cat

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.
+ exit 1

```

---

### Post by ronparent on 2010-09-13
I get an error whenever I do a grub-probe with a /dev/mapper/ device at the -d option. I get  a return if I use a /dev/dm-# -d option. You will find the same symbolic links in your system and your grub-install should be to /dev/dm-6 if that is your root.

---

### Post by ronparent on 2010-09-13
> grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.

This seem to say that grub is not installed on ARRAY6.

---

### Post by reyman on 2010-09-13
> **ronparent said:**
> This seem to say that grub is not installed on ARRAY6.

Yes :/
```

grub-probe --device-map=/boot/grub/device.map --target=drive /
grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.

grub-probe --device-map=/boot/grub/device.map --target=drive /dev/dm-6
grub-probe: error: cannot find a device for /dev/dm-6 (is /dev mounted?).


```

/dev/dm-6 is not a drive, not a device , but what ?

About the last command for grub-probe i try, at the end of listing ,grub-probe try to read the (hd3) for ARRAY6 in device.map ( i add manually this line in device.map) and grube-probe say : 
```

kern/emu/hostdisk.c:403: dm /dev/mapper/isw_cjffbfddic_ARRAY6 starts at 475026048
grub-probe: info: /dev/mapper/isw_cjffbfddic_ARRAY6 starts from 475026048.
grub-probe: info: opening the device hd3.
kern/disk.c:245: Opening `hd3'...
grub-probe: info: the size of hd3 is 117194112.
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
kern/disk.c:334: Closing `hd3'.
```

Perhaps there are information here ?

---

### Post by ronparent on 2010-09-13
I don't know if it is worth another try at installing - but this shoud be quick. 

Try (from a Maverick session):

> sudo grub-install /dev/dm-0

This should be the same as the array location I gave you before.

---

### Post by reyman on 2010-09-13
> **ronparent said:**
> I don't know if it is worth another try at installing - but this shoud be quick. 

Try (from a Maverick session):



This should be the same as the array location I gave you before.

The same ..

```

sudo grub-install /dev/dm-0
[sudo] password for srey: 
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

---

### Post by reyman on 2010-09-13
i remove (hd3) in my device.map, to try only with this device.map : 
```

(hd0)	/dev/disk/by-id/ata-ST9500420ASG_5VJ4LQ5W
(hd1)	/dev/disk/by-id/ata-ST9500420ASG_5VJ4M2E5
(hd2)	/dev/mapper/isw_cjffbfddic_ARRAY
```

ANd with this cmd : 
grub-probe -vvv -t fs /boot/grub

i have : 

```
disk/raid.c:658: Scanning for RAID devices on disk hd0
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd0'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos8
kern/disk.c:245: Opening `hd0,msdos8'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos7
kern/disk.c:245: Opening `hd0,msdos7'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos6
kern/disk.c:245: Opening `hd0,msdos6'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos5
kern/disk.c:245: Opening `hd0,msdos5'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos3
kern/disk.c:245: Opening `hd0,msdos3'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos2
kern/disk.c:245: Opening `hd0,msdos2'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos1
kern/disk.c:245: Opening `hd0,msdos1'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos1'.
disk/raid.c:658: Scanning for RAID devices on disk hd1
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd1'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos8
kern/disk.c:245: Opening `hd1,msdos8'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos7
kern/disk.c:245: Opening `hd1,msdos7'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos6
kern/disk.c:245: Opening `hd1,msdos6'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos5
kern/disk.c:245: Opening `hd1,msdos5'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos3
kern/disk.c:245: Opening `hd1,msdos3'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos2
kern/disk.c:245: Opening `hd1,msdos2'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos1
kern/disk.c:245: Opening `hd1,msdos1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos1'.
disk/raid.c:658: Scanning for RAID devices on disk hd2
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd2'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos8
kern/disk.c:245: Opening `hd2,msdos8'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos7
kern/disk.c:245: Opening `hd2,msdos7'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos6
kern/disk.c:245: Opening `hd2,msdos6'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos5
kern/disk.c:245: Opening `hd2,msdos5'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos3
kern/disk.c:245: Opening `hd2,msdos3'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos2
kern/disk.c:245: Opening `hd2,msdos2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos1
kern/disk.c:245: Opening `hd2,msdos1'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos1'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0,msdos8'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd0,msdos8'.
kern/disk.c:245: Opening `hd0,msdos7'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd0,msdos7'.
kern/disk.c:245: Opening `hd0,msdos6'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd0,msdos6'.
kern/disk.c:245: Opening `hd0,msdos5'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd0,msdos5'.
kern/disk.c:245: Opening `hd0,msdos3'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd0,msdos3'.
kern/disk.c:245: Opening `hd0,msdos2'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd0,msdos2'.
kern/disk.c:245: Opening `hd0,msdos1'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd0,msdos1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1,msdos8'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd1,msdos8'.
kern/disk.c:245: Opening `hd1,msdos7'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd1,msdos7'.
kern/disk.c:245: Opening `hd1,msdos6'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd1,msdos6'.
kern/disk.c:245: Opening `hd1,msdos5'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd1,msdos5'.
kern/disk.c:245: Opening `hd1,msdos3'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd1,msdos3'.
kern/disk.c:245: Opening `hd1,msdos2'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd1,msdos2'.
kern/disk.c:245: Opening `hd1,msdos1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd1,msdos1'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2,msdos8'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd2,msdos8'.
kern/disk.c:245: Opening `hd2,msdos7'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd2,msdos7'.
kern/disk.c:245: Opening `hd2,msdos6'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd2,msdos6'.
kern/disk.c:245: Opening `hd2,msdos5'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd2,msdos5'.
kern/disk.c:245: Opening `hd2,msdos3'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd2,msdos3'.
kern/disk.c:245: Opening `hd2,msdos2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd2,msdos2'.
kern/disk.c:245: Opening `hd2,msdos1'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd2,msdos1'.
grub-probe: info: changing current directory to /dev.
grub-probe: info: changing current directory to snd.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to v4l.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to by-id.
grub-probe: info: changing current directory to cpu.
grub-probe: info: changing current directory to 15.
grub-probe: info: changing current directory to 14.
grub-probe: info: changing current directory to 13.
grub-probe: info: changing current directory to 12.
grub-probe: info: changing current directory to 11.
grub-probe: info: changing current directory to 10.
grub-probe: info: changing current directory to 9.
grub-probe: info: changing current directory to 8.
grub-probe: info: changing current directory to 7.
grub-probe: info: changing current directory to 6.
grub-probe: info: changing current directory to 5.
grub-probe: info: changing current directory to 4.
grub-probe: info: changing current directory to 3.
grub-probe: info: changing current directory to 2.
grub-probe: info: changing current directory to 1.
grub-probe: info: changing current directory to 0.
grub-probe: info: changing current directory to shm.
grub-probe: info: changing current directory to disk.
grub-probe: info: changing current directory to by-label.
grub-probe: info: changing current directory to by-uuid.
grub-probe: info: changing current directory to by-path.
grub-probe: info: changing current directory to by-id.
grub-probe: info: changing current directory to bsg.
grub-probe: info: changing current directory to char.
grub-probe: info: changing current directory to block.
grub-probe: info: changing current directory to pts.
grub-probe: info: changing current directory to mapper.
kern/emu/hostdisk.c:403: dm /dev/mapper/isw_cjffbfddic_ARRAY6 starts at 475026048
grub-probe: info: /dev/mapper/isw_cjffbfddic_ARRAY6 starts from 475026048.
grub-probe: info: opening the device /dev/dm-5.
kern/disk.c:245: Opening `/dev/dm-5'...
grub-probe: info: the size of /dev/dm-5 is 117194112.
kern/emu/hostdisk.c:594: opening the device `/dev/dm-5' in open_device()
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
kern/disk.c:334: Closing `/dev/dm-5'.
grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
```

Don't understand this part, it's crazy ...

```

kern/emu/hostdisk.c:403: dm /dev/mapper/isw_cjffbfddic_ARRAY6 starts at 475026048
grub-probe: info: /dev/mapper/isw_cjffbfddic_ARRAY6 starts from 475026048.
grub-probe: info: opening the device /dev/dm-5.
kern/disk.c:245: Opening `/dev/dm-5'...
grub-probe: info: the size of /dev/dm-5 is 117194112.
kern/emu/hostdisk.c:594: opening the device `/dev/dm-5' in open_device()
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
kern/disk.c:334: Closing `/dev/dm-5'.
grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cjffbfddic_ARRAY6.  Check your device.map.
```

---

### Post by ronparent on 2010-09-13
?????????????????

But at least we know ARRAY6=dm-5

Would you consider a clean maverick reinstall - just be sure not to reformat /home?

---

### Post by reyman on 2010-09-13
> **ronparent said:**
> ?????????????????

But at least we know ARRAY6=dm-5

Would you consider a clean maverick reinstall - just be sure not to reformat /home?

Colin Watson says about --modules : 
> 

(Regarding your next message, please forget about --modules.  That
advice in grub-install's error message is actually kind of unhelpful and
I should get it reworded.  Generally, if grub-install fails like this,
no amount of fiddling about with --modules is going to help much; it
would help if it were actually the filesystem autodetection that failed,
but it's more usually grub-probe failing to handle the device at all.)



ANother try with this help : 

[http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg223442.html](http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg223442.html)

sudo grub-probe -vvv --device-map=/boot/grub/device.map --target=fs  --device /dev/mapper/isw_cjffbfddic_ARRAY

```

sudo grub-probe -vvv --device-map=/boot/grub/device.map --target=fs  --device /dev/mapper/isw_cjffbfddic_ARRAY

disk/raid.c:658: Scanning for RAID devices on disk hd0
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd0'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos8
kern/disk.c:245: Opening `hd0,msdos8'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos7
kern/disk.c:245: Opening `hd0,msdos7'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos6
kern/disk.c:245: Opening `hd0,msdos6'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos5
kern/disk.c:245: Opening `hd0,msdos5'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos3
kern/disk.c:245: Opening `hd0,msdos3'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos2
kern/disk.c:245: Opening `hd0,msdos2'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd0,msdos1
kern/disk.c:245: Opening `hd0,msdos1'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/emu/hostdisk.c:584: reusing open device `/dev/sda'
kern/disk.c:334: Closing `hd0,msdos1'.
disk/raid.c:658: Scanning for RAID devices on disk hd1
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd1'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos8
kern/disk.c:245: Opening `hd1,msdos8'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos7
kern/disk.c:245: Opening `hd1,msdos7'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos6
kern/disk.c:245: Opening `hd1,msdos6'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos5
kern/disk.c:245: Opening `hd1,msdos5'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos3
kern/disk.c:245: Opening `hd1,msdos3'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos2
kern/disk.c:245: Opening `hd1,msdos2'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd1,msdos1
kern/disk.c:245: Opening `hd1,msdos1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/sdb' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/emu/hostdisk.c:584: reusing open device `/dev/sdb'
kern/disk.c:334: Closing `hd1,msdos1'.
disk/raid.c:658: Scanning for RAID devices on disk hd2
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd2'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos8
kern/disk.c:245: Opening `hd2,msdos8'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos8'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos7
kern/disk.c:245: Opening `hd2,msdos7'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos7'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos6
kern/disk.c:245: Opening `hd2,msdos6'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos6'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos5
kern/disk.c:245: Opening `hd2,msdos5'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos5'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos3
kern/disk.c:245: Opening `hd2,msdos3'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos3'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos2
kern/disk.c:245: Opening `hd2,msdos2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos2'.
disk/raid.c:658: Scanning for RAID devices on disk hd2,msdos1
kern/disk.c:245: Opening `hd2,msdos1'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/disk.c:334: Closing `hd2,msdos1'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
kern/emu/hostdisk.c:594: opening the device `/dev/sda' in open_device()
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0'...
grub-probe: info: the size of hd0 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd0'.
kern/disk.c:245: Opening `hd0,msdos8'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd0,msdos8'.
kern/disk.c:245: Opening `hd0,msdos7'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd0,msdos7'.
kern/disk.c:245: Opening `hd0,msdos6'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd0,msdos6'.
kern/disk.c:245: Opening `hd0,msdos5'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd0,msdos5'.
kern/disk.c:245: Opening `hd0,msdos3'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd0,msdos3'.
kern/disk.c:245: Opening `hd0,msdos2'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd0,msdos2'.
kern/disk.c:245: Opening `hd0,msdos1'...
grub-probe: info: the size of hd0 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd0,msdos1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd1'.
kern/disk.c:245: Opening `hd1,msdos8'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd1,msdos8'.
kern/disk.c:245: Opening `hd1,msdos7'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd1,msdos7'.
kern/disk.c:245: Opening `hd1,msdos6'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd1,msdos6'.
kern/disk.c:245: Opening `hd1,msdos5'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd1,msdos5'.
kern/disk.c:245: Opening `hd1,msdos3'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd1,msdos3'.
kern/disk.c:245: Opening `hd1,msdos2'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd1,msdos2'.
kern/disk.c:245: Opening `hd1,msdos1'...
grub-probe: info: the size of hd1 is 976773168.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd1,msdos1'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/apple.c:121: bad magic (found 0xeb48; wanted 0x4552
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/apple.c:121: bad magic (found 0xeb54; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/apple.c:121: bad magic (found 0xeb52; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
partmap/apple.c:121: bad magic (found 0x0; wanted 0x4552
partmap/msdos.c:91: partition 1: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x38c9d32a, len 0x0
kern/disk.c:334: Closing `hd2'.
kern/disk.c:245: Opening `hd2,msdos8'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x570e75e7, len 0x16e3a56
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x234c9000, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x82, start 0x38c9d369, len 0x16e3a17
kern/disk.c:334: Closing `hd2,msdos8'.
kern/disk.c:245: Opening `hd2,msdos7'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x3a94f4fe, len 0x157d432a
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x1c505241, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x234c903f, len 0x157d42eb
kern/disk.c:334: Closing `hd2,msdos7'.
kern/disk.c:245: Opening `hd2,msdos6'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
partmap/msdos.c:91: partition 1: flag 0x0, type 0x5, start 0x1c505241, len 0x6fc3dbf
partmap/msdos.c:91: partition 2: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 3: flag 0x0, type 0x0, start 0x507ed43, len 0x0
partmap/msdos.c:91: partition 0: flag 0x0, type 0x83, start 0x1c505280, len 0x6fc3d80
kern/disk.c:334: Closing `hd2,msdos6'.
kern/disk.c:245: Opening `hd2,msdos5'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
partmap/msdos.c:91: partition 3: flag 0x0, type 0x5, start 0x507ed43, len 0x3530203d
partmap/msdos.c:91: partition 0: flag 0x0, type 0x7, start 0x507ed45, len 0x174864fc
kern/disk.c:334: Closing `hd2,msdos5'.
kern/disk.c:245: Opening `hd2,msdos3'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
partmap/msdos.c:91: partition 2: flag 0x0, type 0x7, start 0xb0000, len 0x4fce000
kern/disk.c:334: Closing `hd2,msdos3'.
kern/disk.c:245: Opening `hd2,msdos2'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
partmap/msdos.c:91: partition 1: flag 0x80, type 0x7, start 0x7e000, len 0x32000
kern/disk.c:334: Closing `hd2,msdos2'.
kern/disk.c:245: Opening `hd2,msdos1'...
grub-probe: info: the size of hd2 is 976767240.
partmap/msdos.c:91: partition 0: flag 0x0, type 0x6, start 0x3f, len 0x7d7e1
kern/disk.c:334: Closing `hd2,msdos1'.
kern/emu/hostdisk.c:383: ignoring dm target mirror (not linear)
grub-probe: info: /dev/mapper/isw_cjffbfddic_ARRAY starts from 0.
grub-probe: info: opening hd2.
kern/disk.c:245: Opening `hd2'...
grub-probe: info: the size of hd2 is 976767240.
kern/fs.c:54: Detecting zfs...
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:1984: label 0
kern/emu/hostdisk.c:594: opening the device `/dev/dm-0' in open_device()
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:2001: label ok 0
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:2006: No uberblock found
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:1984: label 1
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:2001: label ok 1
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:2006: No uberblock found
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:1984: label 2
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:2001: label ok 2
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:2006: No uberblock found
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:1984: label 3
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:2001: label ok 3
/build/buildd/grub2-1.98+20100804/debian/grub-extras/zfs/zfs.c:2006: No uberblock found
kern/fs.c:60: zfs detection failed.
kern/fs.c:54: Detecting afs...
kern/fs.c:60: afs detection failed.
kern/fs.c:54: Detecting afs_be...
kern/fs.c:60: afs_be detection failed.
kern/fs.c:54: Detecting befs...
kern/fs.c:60: befs detection failed.
kern/fs.c:54: Detecting befs_be...
kern/fs.c:60: befs_be detection failed.
kern/fs.c:54: Detecting xfs...
kern/fs.c:60: xfs detection failed.
kern/fs.c:54: Detecting ufs1...
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/emu/hostdisk.c:584: reusing open device `/dev/dm-0'
kern/fs.c:60: ufs1 detection failed.
kern/fs.c:54: Detecting ufs2...
kern/fs.c:60: ufs2 detection failed.
kern/fs.c:54: Detecting sfs...
kern/fs.c:60: sfs detection failed.
kern/fs.c:54: Detecting reiserfs...
kern/fs.c:60: reiserfs detection failed.
kern/fs.c:54: Detecting ntfs...
kern/fs.c:60: ntfs detection failed.
kern/fs.c:54: Detecting nilfs2...
kern/fs.c:60: nilfs2 detection failed.
kern/fs.c:54: Detecting minix...
kern/fs.c:60: minix detection failed.
kern/fs.c:54: Detecting jfs...
kern/fs.c:60: jfs detection failed.
kern/fs.c:54: Detecting udf...
kern/fs.c:60: udf detection failed.
kern/fs.c:54: Detecting iso9660...
kern/fs.c:60: iso9660 detection failed.
kern/fs.c:54: Detecting hfsplus...
kern/fs.c:60: hfsplus detection failed.
kern/fs.c:54: Detecting hfs...
kern/fs.c:60: hfs detection failed.
kern/fs.c:54: Detecting ext2...
kern/fs.c:60: ext2 detection failed.
kern/fs.c:54: Detecting fat...
kern/fs.c:60: fat detection failed.
kern/fs.c:54: Detecting cpiofs...
kern/fs.c:60: cpiofs detection failed.
kern/fs.c:54: Detecting tarfs...
kern/fs.c:60: tarfs detection failed.
kern/fs.c:54: Detecting affs...
kern/fs.c:60: affs detection failed.
grub-probe: error: unknown filesystem.


```

The end of listing is interesting ...

---

### Post by psusi on 2010-09-13
I think the problem is that grub is getting confused by the name.  It thinks that /dev/mapper/isw_cjffbfddic_ARRAY6 is a whole disk, rather than a partition on a disk.  This is because the name is supposed to be /dev/mapper/isw_cjffbfddic_ARRAYp6 to indicate the 6th partition on the underlying actual disk device named /dev/mapper/isw_cjffbfddic_ARRAY.  Ubuntu has a patch to dmraid to drop the p from the name.  This patch was supposed to be removed during the Maverick development cycle but it seems it has not been yet.  I will try to remove it tonight and upload it to my PPA for you to test.

---

### Post by reyman on 2010-09-13
> **psusi said:**
> I think the problem is that grub is getting confused by the name.  It thinks that /dev/mapper/isw_cjffbfddic_ARRAY6 is a whole disk, rather than a partition on a disk.  This is because the name is supposed to be /dev/mapper/isw_cjffbfddic_ARRAYp6 to indicate the 6th partition on the underlying actual disk device named /dev/mapper/isw_cjffbfddic_ARRAY.  Ubuntu has a patch to dmraid to drop the p from the name.  This patch was supposed to be removed during the Maverick development cycle but it seems it has not been yet.  I will try to remove it tonight and upload it to my PPA for you to test.

Tks a lot :) I hope your patch solve this problem !

---

### Post by ronparent on 2010-09-13
Chasing down your problem is interesting and informative. Your install looks and feels like an update with residual garbage left over from a previous install. I think time would be better spent with a clean install of the 10.10 beta. On my system, with a separate home, the install was clean and the grub boot loader was actually automatically and properly placed on the raid root (a first!). More importantly, it was bootable with grub as installed!

I haven't run afoul of the bug with the dmraid naming conventions myself. It doesn't seem to have hit if a raid partition and its name was established prior to that particular bug in dmraid showing up. Maybe because I select the manual partitioning option when installing to a raid. Will keep watching your posts with interest.

---

### Post by psusi on 2010-09-14
After dropping the patches from dmraid and (lib)parted to get the 'p' back, grub-probe still fails with the same error, so it seems my guess was wrong.  Will have to look elsewhere for the cause tonight.

---

### Post by reyman on 2010-09-14
> **psusi said:**
> After dropping the patches from dmraid and (lib)parted to get the 'p' back, grub-probe still fails with the same error, so it seems my guess was wrong.  Will have to look elsewhere for the cause tonight.

OK, you have similar problem with Raid on your computer ?

---

### Post by psusi on 2010-09-14
> **reyman said:**
> OK, you have similar problem with Raid on your computer ?

Yes.  It seems to be a regression in grub.  You should be able to work around it by using grub-mkimage and grub-setup yourself.  It's just the automagic detection that grub-install does is broken.

---

### Post by reyman on 2010-09-14
Ok i try with grub-setup tomorow, if i find an answer, i post here.

---

### Post by ronparent on 2010-09-14
The grub-install command combines a number of commands that could be executed separately. That is explained here: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html)

I also am currently getting grub-probe errors probing on my /dev/mapper/ links. I get correct results probing on my /dev/dm-* links. I don't know what the implications are except that the dm-* links are a recent implementation and to my knowledge are not yet documented! If it is a change that affects grub installation, then we are on our own fingering it out.

---

### Post by psusi on 2010-09-14
> **ronparent said:**
> The grub-install command combines a number of commands that could be executed separately. That is explained here: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html)

I also am currently getting grub-probe errors probing on my /dev/mapper/ links. I get correct results probing on my /dev/dm-* links. I don't know what the implications are except that the dm-* links are a recent implementation and to my knowledge are not yet documented! If it is a change that affects grub installation, then we are on our own fingering it out.

After doing some debugging and walking the code tonight, I came to the same conclusion.  I found one bug where the code expects /dev/mapper/* but actually gets /dev/dm-*, but it seems there is still another problem.  Work continues.

---

### Post by ronparent on 2010-09-15
My system is definitely broke as of an update run last night. The error that pertains to this thread is:

> Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/nvidia_aebhdfib12.  Check your device.map.

Am trying to figure out what include in bug report.

---

### Post by Javache on 2010-09-15
I've had the same issue on my system. The patch in this issue fixed it for me: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=594221](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=594221)

---

### Post by psusi on 2010-09-15
Awesome, that's exactly the problem I found last night; I just didn't quite fix it right.  I'll poke people to try and get this applied despite the freeze.  The patch seems to work for me.

---

### Post by ronparent on 2010-09-15
Looks like issue except both my maverick installs lack /boot/grub/device.map ????

---

### Post by psusi on 2010-09-15
FYI, here is the bug tracking the issue:

[https://bugs.launchpad.net/debian/+source/grub2/+bug/634840](https://bugs.launchpad.net/debian/+source/grub2/+bug/634840)

---

### Post by psusi on 2010-09-15
> **ronparent said:**
> Looks like issue except both my maverick installs lack /boot/grub/device.map ????

That's right, it isn't actually necessary and Ubuntu prefers to run without one.  Its contents are automatically generated as needed.

---

### Post by reyman on 2010-09-16
Thanks psusi for helping us !! :)
I'm trying to apply this patch ...

---

### Post by neillmitchell on 2010-09-16
Hi.

I've just built and installed grub2 from the source with the fix_dmraid patch applied ( [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=594221](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=594221)).

Hasn't fixed it for me :(

When I run sudo update-grub I still get:
Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cbiajacjhg_Watercooler5.  Check your device.map.

I upgraded Lucid to Maverick a couple of weeks ago and all was fine until I updated over the weekend.

---

### Post by psusi on 2010-09-16
I will upload the working version I have to my PPA tonight.

---

### Post by neillmitchell on 2010-09-16
> **psusi said:**
> I will upload the working version I have to my PPA tonight.

That would be very helpful. Thanks! I forgot to mention. I'm running a 64 bit install.

It's vital that a fixed version makes it into Maverick otherwise thousands of upgraders are going to be left with stuffed systems.

---

### Post by neillmitchell on 2010-09-16
I've just got it to work as well. I did not have libdevmapper-dev and libfreetype6-dev installed. Put them on and rebuilt and it worked.

One thing to remember if building grub2 from source is to set the directory prefix using:
./configure --prefix=/usr 
otherwise it all gets installed to /usr/local.

So my full steps to build:

Get [grub2_1.98+20100804.orig.tar.gz]("https://launchpad.net/ubuntu/+archive/primary/+files/grub2_1.98%2B20100804.orig.tar.gz") and [grub2_1.98+20100804-4ubuntu6.diff.gz]("https://launchpad.net/ubuntu/+archive/primary/+files/grub2_1.98%2B20100804-4ubuntu6.diff.gz") from
_[https://launchpad.net/ubuntu/+source/grub2/1.98+20100804-4ubuntu6](https://launchpad.net/ubuntu/+source/grub2/1.98+20100804-4ubuntu6)_

Get the fix_dmraid.patch from [https://bugs.launchpad.net/debian/+source/grub2/+bug/634840](https://bugs.launchpad.net/debian/+source/grub2/+bug/634840)

Unpack the tgz to a temp directory. Copy the diff and patch to that directory. 
gzip -d the [grub2_1.98+20100804-4ubuntu6.diff]("https://launchpad.net/ubuntu/+archive/primary/+files/grub2_1.98%2B20100804-4ubuntu6.diff.gz").gz patch in the directory
patch -p0 < [grub2_1.98+20100804-4ubuntu6.diff]("https://launchpad.net/ubuntu/+archive/primary/+files/grub2_1.98%2B20100804-4ubuntu6.diff.gz")
edit fix_dmraid.patch and change
--- a/kern/emu/hostdisk.c to --- kern/emu/hostdisk.c
and
+++ b/kern/emu/hostdisk.c to +++ kern/emu/hostdisk.c
Then
patch -p0 < fix_dmraid.patch

Make sure you have ruby, bison, automake, autoconf,  flex, libdevmapper-dev and libfreetype6-dev installed.

./configure --prefix=/usr
make
sudo make install

update-grub should now work. :)

---

### Post by psusi on 2010-09-16
Actually, building it like that does not include all of the other Ubuntu patches to grub.  You should either use pbuilder or debuild to build the package then install it rather than make and make install.

---

### Post by neillmitchell on 2010-09-16
> **psusi said:**
> Actually, building it like that does not include all of the other Ubuntu patches to grub.  You should either use pbuilder or debuild to build the package then install it rather than make and make install.

Ah, I've never used those tools. I've come from old school Redhat ;) Are they easy to get going or should I wait for an official grub2 package? However, my built grub2 tools seem to work okay. My computer boots okay to the latest kernel now. Seem to have lost plymouth integration, but that's no big deal for me ;) I'll get it back when he official package is released.

---

### Post by befire on 2010-09-18
Hi, I had this problem too. There is little HOWTO to solve this problem in right (debian) way.

[LIST][*]first get grub sources from ubuntu repo
```

mkdir src && cd src
apt-get source grub2  #it downloads grub sources with ubuntu patches to current directory

```
[*]next - download grub patch to this directory (I've used debian patch) [http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=fix_dmraid.patch;att=1;bug=594221](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=fix_dmraid.patch;att=1;bug=594221)
[*]next - modify patch
change in original patch lines (line numbers only for info, don't add'em to patch)
```

16 --- a/kern/emu/hostdisk.c
17 +++ b/kern/emu/hostdisk.c

```
to this view
```

16 --- kern/emu/hostdisk.c
17 +++ kern/emu/hostdisk.c

```
[*]next - patch grub
```

cd grub2-1.98+20100804
patch -p0 < ../fix_dmraid.patch

```
[*]next - install grub2 dependences and needed tools
```

sudo aptitude install build-essential fakeroot
sudo apt-get build-dep grub2

```
[*]next - compile sources and make debs
```

dpkg-buildpackage -rfakeroot

```
[*]after we get several debs in src directory, install needed
```

cd ..
sudo dpkg -i grub-common_1.98+20100804-4ubuntu6_amd64.deb grub-pc_1.98+20100804-4ubuntu6_amd64.deb #I have 64 bit platform, so got packages for it

```
[*]now need lock custom packages to prevent upgrade them by aptitude
```

echo grub-common hold| sudo dpkg --set-selections
echo grub-pc hold| sudo dpkg --set-selections

```
if you want unlock them need execute 2 last commands again, but replace **hold** with **install**
[/LIST]

---

### Post by ronparent on 2010-09-18
Gentlemen: I submitted a bug report entitled 'Failure of grub-update with raid devices'. If you could submit your comments it could help clear the problem hopefully before final release. See: [https://bugs.launchpad.net/bugs/641372](https://bugs.launchpad.net/bugs/641372)

---

### Post by psusi on 2010-09-18
> **ronparent said:**
> Gentlemen: I submitted a bug report entitled 'Failure of grub-update with raid devices'. If you could submit your comments it could help clear the problem hopefully before final release. See: [https://bugs.launchpad.net/bugs/641372](https://bugs.launchpad.net/bugs/641372)

I already mentioned the existing bug tracking this issue.  Marking this one as a duplicate.

---

### Post by reyman on 2010-09-20
> **befire said:**
> Hi, I had this problem too. There is little HOWTO to solve this problem in right (debian) way.

[LIST][*]first get grub sources from ubuntu repo
```

mkdir src && cd src
apt-get source grub2  #it downloads grub sources with ubuntu patches to current directory

```
[*]next - download grub patch to this directory (I've used debian patch) [http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=fix_dmraid.patch;att=1;bug=594221](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=fix_dmraid.patch;att=1;bug=594221)
[*]next - patch grub
```

cd grub2-1.98+20100804
patch -p0 < ../fix_dmraid.patch

```
[*]next - install grub2 dependences and needed tools
```

sudo aptitude install build-essential fakeroot
sudo apt-get build-dep grub2

```
[*]next - compile sources and make debs
```

dpkg-buildpackage -rfakeroot

```
[*]after we get several debs in src directory, install needed
```

cd ..
sudo dpkg -i grub-common_1.98+20100804-4ubuntu6_amd64.deb grub-pc_1.98+20100804-4ubuntu6_amd64.deb #I have 64 bit platform, so got packages for it

```
[*]now need lock custom packages to prevent upgrade them by aptitude
```

echo grub-common hold| sudo dpkg --set-selections
echo grub-pc hold| sudo dpkg --set-selections

```
if you want unlock them need execute 2 last commands again, but replace **hold** with **install**
[/LIST]

I'm using your instruction to patch grub, but patch failed here 

```
FONDATION-II:~/src/grub2-1.98+20100804$ patch -p0 < ../fix_dmraid.patch
patching file b/kern/emu/hostdisk.c
Hunk #1 FAILED at 1157.
Hunk #2 FAILED at 1171.
Hunk #3 FAILED at 1179.
Hunk #4 FAILED at 1222.
Hunk #5 FAILED at 1354.
5 out of 5 hunks FAILED -- saving rejects to file b/kern/emu/hostdisk.c.rej
```

---

### Post by neillmitchell on 2010-09-20
> **reyman said:**
> I'm using your instruction to patch grub, but patch failed here 

```
FONDATION-II:~/src/grub2-1.98+20100804$ patch -p0 < ../fix_dmraid.patch
patching file b/kern/emu/hostdisk.c
Hunk #1 FAILED at 1157.
Hunk #2 FAILED at 1171.
Hunk #3 FAILED at 1179.
Hunk #4 FAILED at 1222.
Hunk #5 FAILED at 1354.
5 out of 5 hunks FAILED -- saving rejects to file b/kern/emu/hostdisk.c.rej
```

Hi.

You need to edit fix_dmraid.patch and remove the a/ and b/ path in front of the two kern/emu/hostdisk.c entries at the top. The patch then works.

---

### Post by neillmitchell on 2010-09-20
> **befire said:**
> Hi, I had this problem too. There is little HOWTO to solve this problem in right (debian) way.

[LIST]
[*]first get grub sources from ubuntu repo
```

mkdir src && cd src
apt-get source grub2  #it downloads grub sources with ubuntu patches to current directory

```
[/LIST]


Thanks very much for this information! Got it all to build "properly" :) 
I needed extra packages installed to build it on my system. They were debhelper, quilt, xorriso, texinfo,  help2man and libusb-dev. Although I believe some are only needed to run the tests so executing dpkg-buildpackage -rfakeroot with -d ran okay for me without the qemu-kvm package installed.

---

### Post by psusi on 2010-09-20
> **befire said:**
> Hi, I had this problem too. There is little HOWTO to solve this problem in right (debian) way.

Incidentally the debian way is to not apply the patch yourself, but to put it in debian/patches and add it to debian/patches/series.  That way you never use modified upstream sources, except when you actually go to build, the patches are applied.  This lets you drop in a new upstream release when it comes out.

> **neillmitchell said:**
> Hi.

You need to edit fix_dmraid.patch and remove the a/ and b/ path in front of the two kern/emu/hostdisk.c entries at the top. The patch then works.

Or you just use patch -p1 instead of -p0.

---

### Post by neillmitchell on 2010-09-20
> **psusi said:**
> Incidentally the debian way is to not apply the patch yourself, but to put it in debian/patches and add it to debian/patches/series.  That way you never use modified upstream sources, except when you actually go to build, the patches are applied.  This lets you drop in a new upstream release when it comes out..

Very neat and easy once you know how :) 

So will this fix make it into Maverick do you think? A number of users have now verified the patch works. Installing with dmraid was busted in Lucid for other reasons, so it would be a great shame it Maverick went out with fakeraid broken as well. It will also stuff thousands of people who are upgrading.

---

### Post by reyman on 2010-09-20
> **neillmitchell said:**
> Hi.

You need to edit fix_dmraid.patch and remove the a/ and b/ path in front of the two kern/emu/hostdisk.c entries at the top. The patch then works.

It's ok, good, no problem with grube-probe *OUF*
Thanks a lot @all , and i hope for ubuntu user there is a maverick patch in the future...

---

### Post by psusi on 2010-09-20
Yes, it will be fixed before Maverick is released.  If you want to test in the meantime, I have uploaded it to my PPA.

---

### Post by neillmitchell on 2010-09-21
> **psusi said:**
> Yes, it will be fixed before Maverick is released.  If you want to test in the meantime, I have uploaded it to my PPA.
Great news. Thanks!

---

### Post by befire on 2010-09-21
> **neillmitchell said:**
> Hi.

You need to edit fix_dmraid.patch and remove the a/ and b/ path in front of the two kern/emu/hostdisk.c entries at the top. The patch then works.

Yes, it's right, forgot add this step to HOWTO. Now fixed.

---

