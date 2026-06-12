---
title: "Boot Repair Tool Not Working"
date: 2024-08-07
forum: MINT
---

### Post by namiwiki on 2024-08-07
I'm running Linux Mint 21.3, attempted to update to Linux Mint 22. Took a  snapshot with timeshift prior to initiating the install for Mint 22.  The installation process stopped on Foreign Packages, I was asked to  downgrade the foreign packages. So I tried reverting to the snapshot  prior to starting the update process, and my plan was to go through and  delete/downgrade the offending foreign packages. Reverted to the old  snapshot, and my system would not boot.

Got the boot repair tool  on a USB drive. Got the boot disk running, but it won't give me a recommended repair. I'm getting an error that  states, "Please enable a repository containing the [grub-efi] packages in the  software sources of Linux Mint 21.3 Virginia (21.3) (/dev/sda2). Then  try again."

Thoughts on what I can do here?

A summary of the issue from the boot repair tool is here:



[https://pastebin.ubuntu.com/p/NPP6qnHDSn/](https://pastebin.ubuntu.com/p/NPP6qnHDSn/)

```
boot-info-4ppa2079                                              [20240807_2339]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 21.3
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       vfat
     Boot sector type:  SYSLINUX 4.03 2010-10-22  ........>..sr>.......sP  9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 5456288 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /efi/boot/grubx64.efi 
                       /efi/boot/mmx64.efi /ldlinux.sys


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller from Intel Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: A29(4.6) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 000D
Timeout: 0 seconds
BootOrder: 0007,0002,0003,0005,000A,000B,000C,000D,0001,0006,0004
Boot0000   Windows Boot Manager     HD(1,GPT,ebf42a7d-b685-4953-9c69-c55e90376caa,0x800,0x64000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}................. ...
Boot0001  Diskette Drive    BBS(Floppy,Diskette Drive,0x0)AMBO
Boot0002  ubuntu    HD(1,GPT,e1d89f89-31c9-466c-b076-11ef2fbadf52,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* USB Storage Device    BBS(USB,Memorex USB Flash Drive PMAP,0x0)AMBO
Boot0004  CD/DVD/CD-RW Drive    BBS(CDROM,P1: TSSTcorp DVD-ROM SN-108DN ,0x0)AMBO
Boot0005  Onboard NIC    BBS(Network,IBA GE Slot 00C8 v1550,0x0)AMBO
Boot0006* Hitachi HUA723030ALA641    BBS(HD,P0: Hitachi HUA723030ALA641   ,0x0)AMBO
Boot0007  ubuntu    HD(1,GPT,e1d89f89-31c9-466c-b076-11ef2fbadf52,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot000A   UEFI: Hitachi HUA723030ALA641     PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,65535,0)/HD(1,GPT,e1d89f89-31c9-466c-b076-11ef2fbadf52,0x800,0x100000)AMBO
Boot000B  Onboard NIC(IPV4)    PciRoot(0x0)/Pci(0x19,0x0)/MAC(f8b156aa46a2,0)/IPv4(0.0.0.00.0.0.0,0,0)AMBO
Boot000C  Onboard NIC(IPV6)    PciRoot(0x0)/Pci(0x19,0x0)/MAC(f8b156aa46a2,0)/IPv6([::]:<->[::]:,0,0)AMBO
Boot000D* UEFI: Memorex USB Flash Drive PMAP    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x892bfea5,0x1f80,0x39d0080)AMBO

a9c517741ac31962d7feb152948ad1ee   sda1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda1/BOOT/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1     : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,     no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    :  maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,     no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 2.73 TiB, 3000592982016 bytes, 5860533168 sectors
Disk identifier: BBF6C1A9-E69D-494D-B64B-FFF941880A0C
       Start        End    Sectors  Size Type
sda1     2048    1050623    1048576  512M EFI System
sda2  1050624 5860532223 5859481600  2.7T Linux filesystem
Disk sdb: 28.91 GiB, 31042043904 bytes, 60628992 sectors
Disk identifier: 0x892bfea5
     Boot Start      End  Sectors  Size Id Type
sdb1  *     8064 60628991 60620928 28.9G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:3001GB:scsi:512:512:gpt:ATA Hitachi HUA72303:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:3001GB:3000GB:ext4::;
sdb:31.0GB:scsi:512:512:msdos:Memorex USB Flash Drive:;
1:4129kB:31.0GB:31.0GB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1 vfat     8ABD-3CB0                            e1d89f89-31c9-466c-b076-11ef2fbadf52             EFI System Partition
&#9492;&#9472;sda2 ext4     097beafd-a19b-4832-b13a-160aaf611027 e5fe41fd-06c7-459d-803d-248afd0877db             
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     897F-8A62                            892bfea5-01                          Memorex USB 

Mount points (filtered): _______________________________________________________

             Avail Use% Mounted on
/dev/sda1   504.9M   1% /mnt/boot-sav/sda1
/dev/sda2     1.7T  33% /mnt
/dev/sda2     1.7T  33% /mnt/boot-sav/sda2
/dev/sdb1    26.3G   9% /cdrom
proc          1.7T  33% /mnt/boot-sav/sda2/proc
sysfs         1.7T  33% /mnt/boot-sav/sda2/sys
udev          1.7T  33% /mnt/boot-sav/sda2/dev

Mount options (filtered): ______________________________________________________

/dev/sda1   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2   ext4            rw,relatime
/dev/sda2   ext4            rw,relatime
/dev/sdb1   vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Linux Mint 21.3 Cinnamon   097beafd-a19b-4832-b13a-160aaf611027
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=097beafd-a19b-4832-b13a-160aaf611027 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8ABD-3CB0  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
1849.066379547 = 1985.419907072 boot/grub/grub.cfg                             1
 269.472805023 = 289.344221184  boot/vmlinuz                                   1
 193.793094635 = 208.083750912  boot/vmlinuz-5.15.0-105-generic                1
 319.324359894 = 342.871920640  boot/vmlinuz-5.15.0-106-generic                2
 207.011859894 = 222.277292032  boot/vmlinuz-5.15.0-107-generic                2
 529.144668579 = 568.164761600  boot/vmlinuz-5.15.0-112-generic                1
 467.707168579 = 502.196748288  boot/vmlinuz-5.15.0-113-generic                2
 269.472805023 = 289.344221184  boot/vmlinuz-5.15.0-117-generic                1
 467.707168579 = 502.196748288  boot/vmlinuz.old                               2
 113.960247040 = 122.363883520  boot/initrd.img                                1
 113.413360596 = 121.776668672  boot/initrd.img-5.15.0-105-generic             1
 113.522743225 = 121.894117376  boot/initrd.img-5.15.0-106-generic             1
 113.632122040 = 122.011561984  boot/initrd.img-5.15.0-107-generic             1
 113.741489410 = 122.128994304  boot/initrd.img-5.15.0-112-generic             1
 113.850856781 = 122.246426624  boot/initrd.img-5.15.0-113-generic             1
 113.960247040 = 122.363883520  boot/initrd.img-5.15.0-117-generic             1
 113.850856781 = 122.246426624  boot/initrd.img.old                            1

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5 11:36 35_fwupd
-rwxr-xr-x 1 root root   214 Nov 12  2020 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Start Boot-Repair-Disk 64-bit
Start Boot-Repair-Disk 64-bit (compatibility mode)
UEFI Firmware Settings
Test memory

========================= sdb1/syslinux.cfg (filtered) =========================

default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/linuxmint.seed boot=casper quiet splash --

label ubnentry0
menu label Start Boot-Repair-Disk
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper  quiet splash --

label ubnentry1
menu label Start in compatibility mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper  noapic noacpi nosplash irqpoll nomodeset --

label ubnentry2
menu label Start Boot-Repair-Disk 64-bit --class linuxmint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper iso-scan/filename=${iso_path} quiet splash --

label ubnentry3
menu label Start Boot-Repair-Disk 64-bit (compatibility mode)
kernel /casper/vmlinuz
append  initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper  iso-scan/filename=${iso_path} noapic noacpi nosplash irqpoll nomodeset  --


==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1

=============== sdb1: Version of COM32(R) files used by Syslinux ===============

 menu.c32                           :  COM32R module (v4.xx)



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by TheFu on 2024-08-07
Mint isn't Ubuntu.

Boot-Repair doesn't fix all possible issues.

Please edit your post above and wrap the output in "forum code tags" so the format is correct - i.e. monospaced. Use the advanced editor.

BTW, timeshift doesn't really work that well without using btrfs. Just something you should know.

---

### Post by deadflowr on 2024-08-07
Thread moved to the Mint sub-forum

---

### Post by yancek on 2024-08-08
You have messed up the boot process somehow.  You show an EFI partition and a GPT drive but you do not have any boot files on the EFI partition so you cannot boot EFI.  You do not have any boot code in the MBR of the device so yo can't boot in Legacy mode.  You see to have had an EFI partition and somehow deleted all the files there so reinstall Grub in EFI mode which you should be able to do from boot repair.  THe link below to the Mint forums also explains reinstalling Grub.

  [https://forums.linuxmint.com/viewtopic.php?t=320504](https://forums.linuxmint.com/viewtopic.php?t=320504)

Had you tried posting at the Mint forusm?

---

