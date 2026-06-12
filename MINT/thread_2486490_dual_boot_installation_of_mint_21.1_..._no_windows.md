---
title: "dual boot installation of mint 21.1 ... no windows 10 boot - even after boot-repair"
date: 2023-05-02
forum: MINT
---

### Post by mpav989 on 2023-05-02
Hi - I had a win10 laptop, which I wanted to dual boot with linux mint...21 

under win10 I shrank the partion to leave 50GB free...
with the mint installer I chose to Install Linux Mint alongside Windows.... everything seemed fine...

on reboot I didn't get the grub screen as expected .... only error msg saying not bootable...

I booted LM again from the live iso... and used boot-repair....

Now I get the grub screen.... the ubuntu option boot the installed LMint fine....
the win10 option does not boot .... it just returns to the grub screen after a second or 2.

I booted the mint live cd again and ran boot-repair again ... the grub config now has 2 win10 entries ... one for /dev/sda1 (as before) ... and one for sda3 which says - no bootable image if I try to boot to it.

so I can boot into mint OK .... from mint I can seen the files in the  win10  partition (sda2) and they look fine .... but I cannot book into  windows...

I would be grateful for any help!

thanks
```


here's the output of boot repair is it helps
[http://*******.us/HLBZ4v](http://*******.us/HLBZ4v)

boot-repair-4ppa200                                              [20230502_0913]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,2)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    offsetio extcmd macho elf file gettext boot bufio verifiers crypto 
    terminal normal datetime date mmap drivemap blocklist archelp newc 
    vga_text relocator video chain ntldr search_label search_fs_file 
    search_fs_uuid search keylayouts at_keyboard pci usb usb_keyboard gcry_md5 
    hashsum gcry_crc gzio xzio lzopio lspci fshelp ext2 xfs acpi reboot 
    iso9660 gcry_sha1 div udf exfat font diskfilter raid6rec zstd btrfs ventoy 
    read halt video_fb vbe linux linux16 test true sleep echo bitmap gfxterm 
    bitmap_scale trig video_colors gfxmenu videotest videoinfo functional_test 
    videotest_checksum video_cirrus video_bochs vga minicmd help configfile tr 
    biosdisk disk ls tar zfs squash4 pbkdf2 gcry_sha512 password_pbkdf2 
    all_video png jpeg part_gpt part_msdos fat ntfs loopback 
    gfxterm_background procfs gfxterm_menu smbios
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1 
                       and looks at sector 938734272 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub. It also embeds following 
                       components:
                       
                       modules
                       -------------------------------------------------------
                       fshelp ext2 part_msdos biosdisk
                       -------------------------------------------------------
                       -------------------------. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg /bootmgr 
                       /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 21.1
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdb1: __________________________________________________________________________

    File system:       exfat
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sdb1: /dev/sdb1 already mounted or mount point busy.

sdb2: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb2 and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg


================================ 4 OS detected =================================

OS#1:   Windows 10 (boot) on sda1
OS#2:   Windows 10 (boot) on sda3
OS#3:   Linux Mint 21.1 Vera (21.1) on sda5
OS#4:   Windows 8 or 10 on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: HD Graphics 5500 from Intel Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.1, vera, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: JBET73WW (1.37 )(1.37) from LENOVO
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


a9c517741ac31962d7feb152948ad1ee   sda3/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda3/BOOT/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   sda3/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda3/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda3/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   sda3/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda3    : is-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda5    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda5    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x2bd2c32a
      Boot     Start       End   Sectors   Size Id Type
sda1            2048   4272127   4270080     2G  7 HPFS/NTFS/exFAT
sda2         4272128 874372168 870100041 414.9G  7 HPFS/NTFS/exFAT
sda3  *    874373120 875423743   1050624   513M ef EFI (FAT-12/16/32)
sda4       875425790 976771071 101345282  48.3G  5 Extended
sda5       875425792 976771071 101345280  48.3G 83 Linux
Disk sdb: 14.92 GiB, 16023289856 bytes, 31295488 sectors
Disk identifier: 0x4b801049
      Boot    Start      End  Sectors  Size Id Type
sdb1  *        2048 31229951 31227904 14.9G  7 HPFS/NTFS/exFAT
sdb2       31229952 31295487    65536   32M ef EFI (FAT-12/16/32)
Disk mapper/ventoy: 2.47 GiB, 2647666688 bytes, 5171224 sectors
Disk identifier: 4F11B734-C1FB-49E2-85D8-BF2ED72EDBB3
                      Start     End Sectors  Size Type
mapper/ventoy-part1      64 5162663 5162600  2.5G Microsoft basic data
mapper/ventoy-part2 5162664 5171159    8496  4.1M EFI System

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:4096:msdos:ATA HGST HTS725050A7:;
1:1049kB:2187MB:2186MB:ntfs::;
2:2187MB:448GB:445GB:ntfs::;
3:448GB:448GB:538MB:fat32::boot, esp;
4:448GB:500GB:51.9GB:::;
5:448GB:500GB:51.9GB:ext4::;
sdb:16.0GB:scsi:512:512:msdos:CENTON DS Pro:;
1:1049kB:16.0GB:16.0GB:::boot;
2:16.0GB:16.0GB:33.6MB:fat16::esp;
mapper/ventoy:2648MB:dm:512:512:gpt:Linux device-mapper (linear):;
1:32.8kB:2643MB:2643MB::ISO9660:hidden, msftdata;
2:2643MB:2648MB:4350kB::Appended2:boot, esp;

blkid (filtered): ______________________________________________________________

NAME       FSTYPE   UUID                                 PARTUUID                             LABEL                       PARTLABEL
sda                                                                                                                       
&#9500;&#9472;sda1     ntfs     8C72842A72841B5A                     2bd2c32a-01                          System Reserved             
&#9500;&#9472;sda2     ntfs     DE5C84F65C84CAAB                     2bd2c32a-02                                                      
&#9500;&#9472;sda3     vfat     CE8E-AA38                            2bd2c32a-03                                                      
&#9500;&#9472;sda4                                                   2bd2c32a-04                                                      
&#9492;&#9472;sda5     ext4     348cbb04-67c1-49e7-bbd3-96180ac77b07 2bd2c32a-05                                                      
sdb                                                                                                                       
&#9500;&#9472;sdb1     exfat    4E21-0000                            4b801049-01                          Ventoy                      
&#9474; &#9492;&#9472;ventoy                                                                                                                
&#9492;&#9472;sdb2     iso9660  2022-12-17-22-50-00-00                                                    Linux Mint 21.1 Xfce 64-bit 

Mount points (filtered): _______________________________________________________

                    Avail Use% Mounted on
/dev/mapper/ventoy      0 100% /cdrom
/dev/sda1              1G  51% /mnt/boot-sav/sda1
/dev/sda2          238.3G  43% /mnt/boot-sav/sda2
/dev/sda3          487.1M   5% /mnt/boot-sav/sda3
/dev/sda5           34.3G  22% /mnt/boot-sav/sda5

Mount options (filtered): ______________________________________________________

/dev/mapper/ventoy iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8
/dev/sda1          fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda2          fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda3          vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda5          ext4            rw,relatime

============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
ventoy

===================== sda3/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 348cbb04-67c1-49e7-bbd3-96180ac77b07 root hd0,msdos5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   348cbb04-67c1-49e7-bbd3-96180ac77b07
Ubuntu, with Linux 5.15.0-56-generic   348cbb04-67c1-49e7-bbd3-96180ac77b07
Windows 10 (on sda1)   8C72842A72841B5A
Windows 10 (on sda3)   CE8E-AA38
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=348cbb04-67c1-49e7-bbd3-96180ac77b07 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
/swapfile                                 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 447.584865570 = 480.590589952  boot/grub/grub.cfg                             1
 447.937652588 = 480.969392128  boot/grub/i386-pc/core.img                     1
 422.797866821 = 453.975752704  boot/vmlinuz                                   1
 422.797866821 = 453.975752704  boot/vmlinuz-5.15.0-56-generic                 1
 462.515327454 = 496.622051328  boot/initrd.img                                1
 462.515327454 = 496.622051328  boot/initrd.img-5.15.0-56-generic              1
 462.515327454 = 496.622051328  boot/initrd.img.old                            1

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec  2 15:18 10_linux
-rwxr-xr-x 1 root root 43031 Dec  2 15:18 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Dec  2 15:18 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec  2 15:18 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec  2 15:18 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec  2 15:18 40_custom
-rwxr-xr-x 1 root root   215 Dec  2 15:18 41_custom

====================== sdb2/boot/grub/grub.cfg (filtered) ======================

Start Linux Mint 21.1 Xfce 64-bit
Start Linux Mint 21.1 Xfce 64-bit (compatibility mode)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdb2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================================= User choice ==================================

Is there RAID on this computer? no



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
sda5 into the MBR of sda.
Grub-efi would not be selected by default because legacy Windows detected.
Additional repair would be performed: unhide-bootmenu-10s win-legacy-basic-fix

```

---

### Post by TheFu on 2023-05-02
Would really make it easier to help if the report were wrapped in forum 'code-tags'.  You'll likely get better help if you do that. My signature below has a link for a how-to guide on code-tags (and some other forum formatting), but really I only use code, bold, and quote tags in these forums.

---

### Post by mpav989 on 2023-05-02
apologies added code tags ....

---

### Post by mpav989 on 2023-05-02
I think I have just about solved it now .... after a lot of hours and heartache...
I adopted the process to  First - fix Windows booting, second - fix GRUB2.

i) first I got windows only to boot  by using a windows install disk and using a combination of bootrec and bootsect to force
see [https://woshub.com/how-to-rebuild-bcd-file-in-windows-10/](https://woshub.com/how-to-rebuild-bcd-file-in-windows-10/)

ii) I then booted the sysem with the standalone boot-repair livecd which seemed better able to successfully reinstall grub2 to allow me to boot to either mint or win10 from the grub menu ...
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I've a sneaky suspicion that booting my mint live-cd iso from ventoy to install and initially fix things may have led to some of the problems.... which seemed to work better from real cd when sorting boot problems.

ps refind livecd was also useful for debugging
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

thanks
and
fingers crossed

---

### Post by oldfred on 2023-05-02
Two major issues.
You cannot mix UEFI boot & BIOS boot.
You cannot install grub to PBR - partition boot sector of NTFS partitions.

It looks like grub was reinstalled (multiple times) to sda, sdb, and the NTFS partition sda1.
And installed to an ESP - efi system partition - sda3.
Since mount of sda3, ESP is commented out in fstab, the reinstall of grub in BIOS mode corrected that.

You need to move boot flag back to sda1 with gparted or Windows tools, the Windows boot partition. Typically Boot-Repair also copies the boot files into the main Windows partition as backup, since so many users delete the boot partition which Windows does not normally show.
Windows has to have boot flag in BIOS mode, but  UEFI also uses it. Grub does not use boot flag, so you must have it on sda1 (or sda2, if boot files copied).

If you only installed grub once to sda1's PBR, you can restore the backup PBR with testdisk or Windows tools. 
Testdisk may say PBR is valid but different. Grub in a PBR can be valid, but never recommended. And can never be installed to PBR of NTFS partitions as Windows has essential information in the PBR.

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since 2012. Not sure why you have UEFI system with very old BIOS/MBR install.
One disadvantage is that grub only boots working Windows. No chkdsk nor hibernation. And new Windows uses fast start up which sets hibernation flag and often turns it back on with updates. Then the only recourse is to temporarily reinstall a Windows boot loader to MBR, fix Windows, and restore grub to MBR. So you must always keep a Windows repair/recovery flash drive, and an Ubuntu live installer to make repairs. 
And of course good backups.

With UEFI/gpt the ESP partition has both boot loaders, so you can always choose which system to boot. 
But conversion to gpt from MBR will totally erase drive, so may not be easily done now.

---

### Post by mpav989 on 2023-05-02
Yes, its been a bit of a mess... A relative, bought it 2nd hand with the BIOS / OS installed that way. Then he installed linux and got me involved when it wouldn&#8217;t boot. Anyway, its booting now .... I&#8217;ll look into your advice and try to do it when I next get my hands on it... (I&#8217;ve already had to hand it back to him as it was needed).

Here is a copy of the log after the final boot-repair  was done.
```

boot-repair-4ppa203                                              [20230502_1415]

============================= Boot Repair Summary ==============================






Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub2 of
sda5 into the MBR of sda.
Grub-efi will not be selected by default because legacy Windows detected.
Additional repair will be performed: unhide-bootmenu-10s win-legacy-basic-fix


Quantity of real Windows: 1

========================= Reinstall the grub2 of sda5 ==========================

chroot /mnt/boot-sav/sda5 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.1

==> Reinstall the GRUB of sda5 into the MBR of sda

chroot /mnt/boot-sav/sda5 grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.

chroot /mnt/boot-sav/sda5 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50_linuxmint.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-56-generic
Found initrd image: /boot/initrd.img-5.15.0-56-generic
The ZFS modules are not loaded.
Try running '/sbin/modprobe zfs' as root to load them.
Some pools couldn't be imported and will be ignored:
The ZFS modules are not loaded.
Try running '/sbin/modprobe zfs' as root to load them.
The ZFS modules are not loaded.
Try running '/sbin/modprobe zfs' as root to load them.
The ZFS modules are not loaded.
Try running '/sbin/modprobe zfs' as root to load them.
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 10 on /dev/sda1
Found Windows 10 on /dev/sda3

Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.


============================ Boot Info After Repair ============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg /bootmgr 
                       /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 21.1
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


================================ 4 OS detected =================================

OS#1:   Windows 10 (boot) on sda1
OS#2:   Windows 10 (boot) on sda3
OS#3:   Linux Mint 21.1 Vera (21.1) on sda5
OS#4:   Windows 10 or 11 on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: HD Graphics 5500 from Intel Corporation
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: JBET73WW (1.37 ) from LENOVO
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


a9c517741ac31962d7feb152948ad1ee   sda3/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda3/BOOT/mmx64.efi
5ddf997e8b025bfbc2009e85b32f60dc   sda3/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda3/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda3/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   sda3/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : notGPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda5    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda5    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x2bd2c32a
      Boot     Start       End   Sectors   Size Id Type
sda1            2048   4272127   4270080     2G  7 HPFS/NTFS/exFAT
sda2         4272128 874372168 870100041 414.9G  7 HPFS/NTFS/exFAT
sda3  *    874373120 875423743   1050624   513M ef EFI (FAT-12/16/32)
sda4       875425790 976771071 101345282  48.3G  5 Extended
sda5       875425792 976771071 101345280  48.3G 83 Linux
Disk zram0: 957.7 MiB, 1004224512 bytes, 245172 sectors
Disk zram1: 957.7 MiB, 1004224512 bytes, 245172 sectors
Disk zram2: 957.7 MiB, 1004224512 bytes, 245172 sectors
Disk zram3: 957.7 MiB, 1004224512 bytes, 245172 sectors

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:4096:msdos:ATA HGST HTS725050A7:;
1:1049kB:2187MB:2186MB:ntfs::;
2:2187MB:448GB:445GB:ntfs::;
3:448GB:448GB:538MB:fat32::boot, esp;
4:448GB:500GB:51.9GB:::;
5:448GB:500GB:51.9GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9500;&#9472;sda1 ntfs     8C72842A72841B5A                     2bd2c32a-01                          System Reserved        
&#9500;&#9472;sda2 ntfs     DE5C84F65C84CAAB                     2bd2c32a-02                                                 
&#9500;&#9472;sda3 vfat     CE8E-AA38                            2bd2c32a-03                                                 
&#9500;&#9472;sda4                                               2bd2c32a-04                                                 
&#9492;&#9472;sda5 ext4     348cbb04-67c1-49e7-bbd3-96180ac77b07 2bd2c32a-05                                                 

Mount points (filtered): _______________________________________________________

             Avail Use% Mounted on
/dev/sda1       1G  51% /mnt/boot-sav/sda1
/dev/sda2   236.1G  43% /mnt/boot-sav/sda2
/dev/sda3   487.1M   5% /mnt/boot-sav/sda3
/dev/sda5    34.3G  22% /mnt/boot-sav/sda5

Mount options (filtered): ______________________________________________________


===================== sda3/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 348cbb04-67c1-49e7-bbd3-96180ac77b07 root hd0,msdos5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   348cbb04-67c1-49e7-bbd3-96180ac77b07
Ubuntu, with Linux 5.15.0-56-generic   348cbb04-67c1-49e7-bbd3-96180ac77b07
Windows 10 (on sda1)   8C72842A72841B5A
Windows 10 (on sda3)   CE8E-AA38
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=348cbb04-67c1-49e7-bbd3-96180ac77b07 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
/swapfile                                 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 417.435550690 = 448.218009600  boot/grub/grub.cfg                             1
 447.760623932 = 480.779309056  boot/grub/i386-pc/core.img                     1
 422.797866821 = 453.975752704  boot/vmlinuz                                   1
 422.797866821 = 453.975752704  boot/vmlinuz-5.15.0-56-generic                 1
 462.515327454 = 496.622051328  boot/initrd.img                                1
 462.515327454 = 496.622051328  boot/initrd.img-5.15.0-56-generic              1
 462.515327454 = 496.622051328  boot/initrd.img.old                            1

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec  2 15:18 10_linux
-rwxr-xr-x 1 root root 43031 Dec  2 15:18 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Dec  2 15:18 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec  2 15:18 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec  2 15:18 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec  2 15:18 40_custom
-rwxr-xr-x 1 root root   215 Dec  2 15:18 41_custom

```

---

