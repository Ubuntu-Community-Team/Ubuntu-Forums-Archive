---
title: "HELP! I could not boot my Linux from the start of the PC"
date: 2024-11-15
forum: MINT
---

### Post by paddy-rice on 2024-11-15
I am using Mint OS on a Thinkpad. Everything went well until I messed up the Lenovo boot. Now I only can boot up  the windows boot. The 1 TB disk was partitioned for five partitions. 

Info from boot repair can be viewed here: [https://paste.ubuntu.com/p/hHJSmW82QQ/](https://paste.ubuntu.com/p/hHJSmW82QQ/)

Thank you so much!

Update: 

[SOLVED] 

Use the command in Live session: 

root@ubuntu:~# efibootmgr -c -w -L "BootOptionName" -d /dev/nvme0n1p5 -p 1 -l /efi/ubuntu/grubx64.efi  # change to grub.efi  shim.efi MokManager.efi for your own distro. 


See below: ```

----------------------------------

boot-repair-4ppa2081                                              [20241115_1307]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/SecureBootRecovery.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p5: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 22
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1 (linux):   Linux Mint 22 Wilma (22) on nvme0n1p5
OS#2 (windows):   Windows 8 or 10 on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Advanced Micro Devices, Inc. [AMD/ATI] EFI VGA from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: R2LET28W (1.09 )(1.9) from LENOVO
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0020
Timeout: 0 seconds
BootOrder: 0000,001D,001E,001F,0020,0021,0022,0023,0024,0025
Boot0000* Windows Boot Manager    HD(1,GPT,0a76b877-edd5-4310-b13c-ed593e82545e,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0010  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Asset Information    FvFile(da465b87-a26f-4c12-b78a-0361428fa026)
Boot0015  Regulatory Information    FvFile(478c92a0-2622-42b7-a65d-5894169e4d24)
Boot0016  ThinkShield secure wipe    FvFile(3593a0d5-bd52-43a0-808e-cbff5ece2477)
Boot0017  ThinkShield Passwordless Power-On Device Manager    FvFile(08448b41-7f83-49be-82a7-0e84790ab133)
Boot0018  Wi-Fi Configuration    FvFile(d3aaff0f-cb22-4792-896c-802c2e9383ba)-.A.p.p...
Boot0019  Reinstall Windows from Cloud    FvFile(3edbaac4-5017-4870-8cc4-721f9ef1974f)-.A.p.p...
Boot001A  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot001B  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot001C  Lenovo OneKey Recovery    FvFile(04970e59-fccc-47cc-b945-7976ee7dbb7a)
Boot001D* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot001E* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot001F* NVMe0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot0020* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot0021* PXE BOOT    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0022* LENOVO CLOUD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri([https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi](https://download.lenovo.com/pccbbs/cdeploy/efi/boot.efi))
Boot0023* ON-PREMISE    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ad38ccbbf7edf04d959cf42aa74d3650)/Uri()
Boot0024  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35400)
Boot0025  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,ca88c2349e7ae947beeb43038a5aeae700)
Boot0026* Boot Next Boot Option    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)

07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/Boot/bootx64.efi
39bc76ff6662f4fbe9aa116e4c997b41   nvme0n1p1/Boot/fbx64.efi
4ba5a5aad43c197e9fb58b76b404d287   nvme0n1p1/Boot/mmx64.efi
66f69798ad23240e43b7ba0044a914c4   nvme0n1p1/ubuntu/grubx64.efi
4ba5a5aad43c197e9fb58b76b404d287   nvme0n1p1/ubuntu/mmx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/ubuntu/shimx64.efi
0dddc55d593fc13c3ab3cb750e1a188a   nvme0n1p1/Microsoft/Boot/SecureBootRecovery.efi
f20e035d67c783cbe1d7b6e624d662d8   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
99bb951188f84db9cbbb6b2e0a25e3f9   nvme0n1p1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    hashidESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p5    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : hidenESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, vfat
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs
nvme0n1p5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: D344A2AD-D4A7-49CA-9E30-C711C5BD6746
              Start        End    Sectors   Size Type
nvme0n1p1       2048     534527     532480   260M EFI System
nvme0n1p2     534528     567295      32768    16M Microsoft reserved
nvme0n1p3     567296 1507610847 1507043552 718.6G Microsoft basic data
nvme0n1p4 1996312576 2000408575    4096000     2G Windows recovery environment
nvme0n1p5 1507612672 1996312575  488699904   233G Linux filesystem
Partition table entries are not in disk order.
Disk sda: 14.32 GiB, 15376318464 bytes, 30031872 sectors
Disk identifier: 0x14eb2669
     Boot   Start      End  Sectors  Size Id Type
sda1  *          0  5138431  5138432  2.5G  0 Empty
sda2           572     9067     8496  4.1M ef EFI (FAT-12/16/32)
sda3       5140480 30031871 24891392 11.9G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:15.4GB:scsi:512:512:msdos:SanDisk Cruzer Blade:;
2:293kB:4643kB:4350kB:::esp;
3:2632MB:15.4GB:12.7GB:ext4::;
nvme0n1:1024GB:nvme:512:512:gpt:UMIS RPETJ1T24MHP2QDQ:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, hidden, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:772GB:772GB:ntfs:Basic data partition:msftdata;
5:772GB:1022GB:250GB:ext4::;
4:1022GB:1024GB:2097MB:ntfs::hidden, diag;

Free space >10MiB: ______________________________________________________________

sda: 4.43MiB:2510MiB:2506MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda         iso9660  2023-12-23-05-05-55-00                                                    Boot-Repair-Disk 64bit 
&#9500;&#9472;sda1      iso9660  2023-12-23-05-05-55-00               14eb2669-01                          Boot-Repair-Disk 64bit 
&#9500;&#9472;sda2      vfat     8D6C-A9F8                            14eb2669-02                          ESP                    
&#9492;&#9472;sda3      ext4     858f82ea-aa83-4098-82d0-feb0d0742e09 14eb2669-03                          writable               
nvme0n1                                                                                                               
&#9500;&#9472;nvme0n1p1 vfat     9A4F-3D16                            0a76b877-edd5-4310-b13c-ed593e82545e SYSTEM                 EFI system partition
&#9500;&#9472;nvme0n1p2                                               8e26e02b-067a-480c-9813-13e87593118f                        Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     800E51B20E51A1C8                     d1d590ce-2669-4259-8f30-f12edc319268 Windows                Basic data partition
&#9500;&#9472;nvme0n1p4 ntfs     481651ED1651DD0E                     56248b84-6504-4ba5-9850-913ae3c530ba WinRE_DRV              Basic data partition
&#9492;&#9472;nvme0n1p5 ext4     ef26dd8d-8314-4e73-8241-a3f3b589eefd 46465c62-d9fb-4c9b-9982-423855d8e780                        

Mount points (filtered): _______________________________________________________

                                                             Avail Use% Mounted on
/dev/nvme0n1p1                                              215.9M  16% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3                                              629.8G  12% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4                                                1.3G  34% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5                                              195.8G   9% /media/mint/ef26dd8d-8314-4e73-8241-a3f3b589eefd
/dev/sda1                                                        0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1                                              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p3                                              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p4                                              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p5                                              ext4            rw,nosuid,nodev,relatime,errors=remount-ro
/dev/sda1                                                   iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid ef26dd8d-8314-4e73-8241-a3f3b589eefd root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p5/boot/grub/grub.cfg (filtered) ====================

Ubuntu   ef26dd8d-8314-4e73-8241-a3f3b589eefd
Windows Boot Manager (on nvme0n1p1)   osprober-efi-9A4F-3D16
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p5/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p5 during installation
UUID=ef26dd8d-8314-4e73-8241-a3f3b589eefd /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=9A4F-3D16  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

==================== nvme0n1p5/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
GRUB_GFXMODE=640x480

================= nvme0n1p5: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 763.092784882 = 819.364638720  boot/grub/grub.cfg                             1
 726.376228333 = 779.940536320  boot/vmlinuz                                   1
 729.657470703 = 783.463743488  boot/vmlinuz-6.8.0-38-generic                  1
 861.352794647 = 924.870520832  boot/vmlinuz-6.8.0-47-generic                  1
 726.376228333 = 779.940536320  boot/vmlinuz-6.8.0-48-generic                  1
 861.352794647 = 924.870520832  boot/vmlinuz.old                               1
 733.188167572 = 787.254800384  boot/initrd.img                                5
 733.862300873 = 787.978645504  boot/initrd.img-6.8.0-38-generic               5
 728.227249146 = 781.928054784  boot/initrd.img-6.8.0-47-generic               1
 733.188167572 = 787.254800384  boot/initrd.img-6.8.0-48-generic               5
 728.227249146 = 781.928054784  boot/initrd.img.old                            1

=================== nvme0n1p5: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5  2024 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4  2024 40_custom
-rwxr-xr-x 1 root root   215 Apr  4  2024 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p5,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Linux Mint 22 Wilma (22) entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)

*******.us ko ()
```

---

### Post by grahammechanical on 2024-11-15
First of all, what did you do to mess up the Lenovo boot? Why can't you reverse it?

Boot Repair will only re-install the Grub boot files. It will not fix a messed up Lenovo boot. Unless of course, you deleted the Linux boot files.

Regards

---

### Post by jeremy31 on 2024-11-15
Moved to Mint

---

### Post by yancek on 2024-11-15
You do not have an entry for Mint in your efibootmgr output and it skips from Boot000 to Boot 0010.  Did you have an entry and delete in.  You need to create a new entry and that is explained at the link below.

[https://wiki.gentoo.org/wiki/Efibootmgr](https://wiki.gentoo.org/wiki/Efibootmgr)

---

### Post by oldfred on 2024-11-15
Mint is not Ubuntu, but usually is identified as Ubuntu in UEFI boot menu.

I like to change names of entries, but in past it needed the /EFI/ubuntu entry as something was hardcoded to only use grub.cfg in /EFI/ubuntu.
In /etc/default/grub I change this liine:
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
to this, by commenting out above line with # and adding new line, but you may want to use mint:
[FONT=monospace][COLOR=#000000]GRUB_DISTRIBUTOR=noble

Then run Boot-Repair to do total reinstall of grub from advanced mode. I think that is what its default suggest is, also.[/COLOR]
[/FONT]

---

### Post by paddy-rice on 2024-11-16
Thanks for your response. Can you explain more specifically as I don’t want to break the system further? Do you refer the file on the live session or the mint os on my PC, which I can’t access right now?

---

### Post by paddy-rice on 2024-11-16
It seems that’s the issue is. Not sure the syntax I should input.

---

### Post by oldfred on 2024-11-16
You can just run Boot-Repair, and see if you can boot.

Then on your working system you can change the name. Add # to convert to comment & add new line.

sudoedit /etc/default/grub
#GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
[FONT=monospace][COLOR=#000000]GRUB_DISTRIBUTOR=mint

Then do 
sudo grub-install
[/COLOR][/FONT]

---

### Post by yancek on 2024-11-16
If you have not resolved this issue by using boot repair as suggested above in post 8, you could try the command below:

```
 efibootmgr -c -d /dev/nvme0n1 -p 1 -L "Mint" -l '\efi\boot\bootx64.efi'
```

Since Mint has required 'ubuntu' in the past, I don't know this will work and you may neet to replace Mint in the command above with ubuntu as mentioned in post 5 above.

I see in your boot repair output that you have under partitions info (2/3):  hidenESP  where it usually just shows is ESP so that may be something you need to change in the BIOS.

---

