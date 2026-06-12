---
title: "Struggling to install Ubuntu 20.04 LTS to newly built PC"
date: 2020-08-16
forum: MINT
---

### Post by flexbriggs on 2020-08-16
Hey guys, first post here. For the past few days, I have been struggling to install Ubuntu (from a flash drive) to my hard drive of type nvme. I've tried many solutions, but to no avail.

[Warning: I'm a HUGE noob when it comes to linux / tech stuff. If you need some information, I'd really appreciate it if you could explain the steps to get the information, Thank you!]

I build a PC with the following components:
MSI b550-a pro motherboard
Ryzen 5 3600 CPU
Radeon RX 580 Graphics Card
Adapta sxg6000 M.2 hard drive

I have two M.2 hard drives, on one I have downloaded Windows 10 successfully. I removed this hard drive and inserted the other so that I could install Ubuntu, but am not having any luck.

What I've done so far:
Change boot order in BIOS to boot to the flash drive, then a (grub?) menu would come up and I'd choose Ubuntu. From there, it would either freeze on the loading (Pro Series) screen,
or if I pressed enter, I could see a long line of errors. Some of which included iomu ivd0 amd-vi timing out, stdin-invalid argument, etc. 
Instead of choosing Ubuntu in the (grub?) menu, I edited it and inserted "nomodeset acpi=off" inbetween quiet and splash, and I was able to boot to the flash usb! Progress, but that's 
where the progress quickly ended.
Every time I try to install the Ubuntu 20.04, I get the error "Executing 'grub-install /dev/nvme0n1' failed. This is a fatal error'. From here, I've attempted to do some partitioning with GPart,
and I have also tried boot-repair (which always gives me an error). 

At this point, I don't know what to do. If you guys have any ideas, I'd really appreciate it. Like I said, if you want any info, please let me know how I can obtain this info.

Thanks

---

### Post by ubfan1 on 2020-08-16
First ensure your firmware is up-to-date from the vendor for your motherboard and SSD.  The 20.04  kernel is 5.4, so consider trying a later one like 5.7 if all else fails.  Next, search the askubuntu site for IOMMU then your msib550,  then ryzen 3600.  Might be some tips on getting your machine to work.  Lastly, the installer will still fail for UEFI mode when the EFI is not on sda.  See lanuchpad bug 1396379, the workaround suggested is to do the install from the "Try" desktop of the installer, then remount the desired EFI at /boot/eri.

---

### Post by flexbriggs on 2020-08-17
Hey there, I have read the launchpad bug's comments, and am a bit confused. I'm hoping you can help clear this up? I have a USB Flash Drive and a hard drive I'm trying to install to. Would it be correct to use GParted to partition the hard drive into ext4, EFI, and then mount the EFI of the hard drive to /target/boot/efi,or am I mounting the EFI of the flash drive? I'm just getting a bit confused between the two. Also, if a mount point does not exist, should I just manually create the directories? Thank you

---

### Post by TheFu on 2020-08-17
B550 is bleeding edge.  
When searching for that Adapta sxg6000 drive, only your posts show up.  None from any vendor.  Some NVMe SSDs don't have good drivers.

---

### Post by ubfan1 on 2020-08-17
Might be your sda is the install media, in which case not sure if those inst. would work (filesystem might be readonly?). I've always just done the EFI creation manually -- create the three directories (EFI, Boot, ubuntu) and copy in three files (grubx64.efi, shimx64.efi and the stub grub.cfg).  Edit the UUID of your Ubuntu root into the three line stub grub.cfg, and if you set the Boot up with grubx64.efi and shimx64.efi renamed as bootx64.efi, the device should boot (even without an explicit OS nvram entry which would boot the ...ubuntu/ efi files.

---

### Post by oldfred on 2020-08-17
Even if different brand, most issue are by common chipset of motherboard.
Essential to have latest UEFI & NVMe firmware updates.

Asus ROG strix b450-F
[https://askubuntu.com/questions/1267714/error-while-trying-to-install-any-linux-version-ubuntu-ubuntu-budgie-solus-gn?noredirect=1#comment2146118_1267714](https://askubuntu.com/questions/1267714/error-while-trying-to-install-any-linux-version-ubuntu-ubuntu-budgie-solus-gn?noredirect=1#comment2146118_1267714)
 Asus ROG Strix B450 E motherboard UEFI update worked
[https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679](https://askubuntu.com/questions/1174679/cant-dual-boot-ubuntu-with-windows-10-in-ryzen-3600?noredirect=1#comment1960921_1174679)
Asus Rog Strix B550 Disable IOMMU
[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)

If NVMe drive, it will not be /dev/sda, but /dev/nvme0n1. 

I only have ESP, / (root) and data partitions. With my smaller SSS, I had data on HDD. Now with a larger NVMe drive, I have most data on NVMe drive and HDD is backup and other "stuff".

---

### Post by TheFu on 2020-08-17
I have an Asus ROG STRIX B450-F GAMING MB. Don't remember any problems specific to Ubuntu/Linux.

The information from that askUbuntu B450 link is out of date. Ryzen MBs over about 6 months old shouldn't have any RAM compatibility issues anymore. I've been running non-approved RAM since the beginning. Just use the XMP profile - AMD calls that something else.

As for NVMe - can't say. My SSD is SATA m.2 in that machine.

---

### Post by flexbriggs on 2020-08-17
My BIOS is the latest version, and I have attempted the install from both the M.2 and a SATA-connected SSD, and both are giving me the same error.

--- Also --- Attempted a boot-repair and received the following error log (long)

```
boot-repair-4ppa125                                              [20200818_0118]

============================= Boot Repair Summary ==============================



/usr/share/boot-sav/bs-cmd_terminal.sh: line 177: warning: command substitution: ignored null byte in input

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
sda2,
using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file


/boot/efi added in sda2/fstab
Mount sda1 on /mnt/boot-sav/sda2/boot/efi
ls: cannot access '/mnt/boot-sav/sda2/boot/efi/efi': No such file or directory
No sda2/boot/efi/efi/ ubuntu/mint folder

Unhide GRUB boot menu in sda2/etc/default/grub

================= Reinstall the grub-efi-amd64-signed of sda2 ==================

grub-install --version
grub-install (GRUB) 2.04-1ubuntu26.2

efibootmgr -v from chroot before grub install
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001
Boot0001* UEFI: VendorCoProductCode 2.00, Partition 1    PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/USB(7,0)/HD(1,GPT,43d91da7-d9b0-4a91-b077-51d10bc28555,0x800,0xeff7df)..BO

uname -r
5.4.0-42-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Exit code: 1
df /dev/sda1
mv /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Exit code: 1

---- Grub-install recheck

/sbin/grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot --recheck
Installing for x86_64-efi platform.
/sbin/grub-install: warning: Internal error.
/sbin/grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Exit code: 1
---- End of grub-install recheck


efibootmgr -v from chroot after grub install
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001
Boot0001* UEFI: VendorCoProductCode 2.00, Partition 1    PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/USB(7,0)/HD(1,GPT,43d91da7-d9b0-4a91-b077-51d10bc28555,0x800,0xeff7df)..BO
Error: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-42-generic
Found initrd image: /boot/initrd.img-5.4.0-42-generic
Adding boot menu entry for UEFI Firmware Settings

Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

An error occurred during the repair.

Locked-NVram detected.


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/grubx64.efi 
                       /efi/BOOT/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /efi/BOOT/mmx64.efi


================================ 1 OS detected =================================

OS#1:   Ubuntu 20.04.1 LTS on sda2

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.1 LTS, focal, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled.

efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001
Boot0001* UEFI: VendorCoProductCode 2.00, Partition 1    PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/USB(7,0)/HD(1,GPT,43d91da7-d9b0-4a91-b077-51d10bc28555,0x800,0xeff7df)..BO



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    no-grubenv,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda2    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 119.25 GiB, 128035676160 bytes, 250069680 sectors
Disk identifier: C71F4D8F-E050-4A96-83D6-994C194D2B18
       Start       End   Sectors  Size Type
sda1    2048    514047    512000  250M EFI System
sda2  514048 250068991 249554944  119G Linux filesystem
Disk sdb: 7.51 GiB, 8053063680 bytes, 15728640 sectors
Disk identifier: F59CF8D1-634D-47E1-8646-68B1FBCE8B7F
      Start      End  Sectors  Size Type
sdb1   2048 15728606 15726559  7.5G Microsoft basic data

parted -lm (filtered): _________________________________________________________

sda:128GB:scsi:512:512:gpt:ATA M4-CT128M4SSD2:;
1:1049kB:263MB:262MB:fat32::boot, esp;
2:263MB:128GB:128GB:ext4::;
sdb:8053MB:scsi:512:512:gpt:VendorCo ProductCode:;
1:1049kB:8053MB:8052MB:fat32:Main Data Partition:msftdata;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9500;&#9472;sda1 vfat     8841-7B12                            96e098e1-0067-47ec-b745-91354e6ba60e EFI         
&#9492;&#9472;sda2 ext4     79e70783-ee8e-46df-9fbe-c417a3e46f9f 9aa442ef-44f5-4eea-b34c-1863f17229dd             
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     7692-9FCC                            43d91da7-d9b0-4a91-b077-51d10bc28555 UBUNTU 20_0 Main Data Partition

df (filtered): _________________________________________________________________

       Avail Use% Mounted on
sda1   235.5M   4% /mnt/boot-sav/sda1
sda2   103.4G   6% /mnt/boot-sav/sda2
sdb1     4.9G  35% /cdrom

Mount options: __________________________________________________________________

sda1   rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda2   rw,relatime
sdb1   ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 79e70783-ee8e-46df-9fbe-c417a3e46f9f root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Ubuntu   79e70783-ee8e-46df-9fbe-c417a3e46f9f
Ubuntu, with Linux 5.4.0-42-generic   79e70783-ee8e-46df-9fbe-c417a3e46f9f
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=79e70783-ee8e-46df-9fbe-c417a3e46f9f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
/swapfile                                 none            swap    sw              0       0
UUID=8841-7B12  /boot/efi       vfat    defaults      0       1

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   0.245121002 = 0.263196672    boot/grub/grub.cfg                             1
   4.427852631 = 4.754370560    boot/vmlinuz                                   1
   4.427852631 = 4.754370560    boot/vmlinuz-5.4.0-42-generic                  1
  50.825092316 = 54.573027328   boot/initrd.img                                2
  50.825092316 = 54.573027328   boot/initrd.img-5.4.0-42-generic               2
  50.825092316 = 54.573027328   boot/initrd.img.old                            2

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 17123 Jul 31 00:34 10_linux
-rwxr-xr-x 1 root root 42128 Jul 31 00:34 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Jul 31 00:34 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jul 31 00:34 30_os-prober
-rwxr-xr-x 1 root root  1424 Jul 31 00:34 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jul 31 00:34 40_custom
-rwxr-xr-x 1 root root   216 Jul 31 00:34 41_custom

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings

========================= sdb1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1


======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown MBR on /dev/sdb

00000000  41 4b 45 4f fc 31 c0 fa  8e d0 bc 00 7c fb 8e d8  |AKEO.1......|...|
00000010  bb 13 04 8b 07 83 e8 04  89 07 c1 e0 06 8e c0 b7  |................|
00000020  07 b8 7f 00 cd 10 31 db  31 c9 ba 4f 18 b8 00 06  |......1.1..O....|
00000030  cd 10 31 d2 b4 02 cd 10  b4 41 bb aa 55 cd 13 72  |..1......A..U..r|
00000040  27 81 fb 55 aa 75 21 f7  c1 01 00 74 1b 66 31 c0  |'..U.u!....t.f1.|
00000050  66 50 6a 22 06 66 50 6a  08 6a 10 89 e6 b4 42 cd  |fPj".fPj.j....B.|
00000060  13 9f 83 c4 10 9e eb 0d  b8 08 02 b9 23 00 ba 80  |............#...|
00000070  00 31 db cd 13 bb 07 00  72 0b 31 f6 8c c0 8e d8  |.1......r.1.....|
00000080  e8 3f 00 eb 06 be 17 7d  e8 37 00 31 c0 8e d8 be  |.?.....}.7.1....|
00000090  63 7d e8 2d 00 e8 1d 00  b4 01 cd 16 75 08 b4 02  |c}.-........u...|
000000a0  cd 16 24 04 74 f2 31 c0  8e d8 b8 34 12 a3 73 04  |..$.t.1....4..s.|
000000b0  ea 00 00 ff ff b4 01 cd  16 74 06 b4 00 cd 16 e2  |.........t......|
000000c0  f4 c3 ac 3c 00 74 4f 3c  0d 74 f7 3c 0a 75 10 53  |...<.tO<.t.<.u.S|
000000d0  b4 03 cd 10 fe c6 b2 00  b4 02 cd 10 5b eb e3 3c  |............[..<|
000000e0  5c 75 1c b1 02 ac 3c 46  7f d8 2c 30 3c 09 7e 02  |\u....<F..,0<.~.|
000000f0  2c 07 c0 e3 04 24 0f 08  c3 fe c9 75 e8 eb c3 b9  |,....$.....u....|
00000100  01 00 b4 09 cd 10 53 31  db b4 03 cd 10 fe c2 b4  |......S1........|
00000110  02 cd 10 5b eb ac c3 0d  0a 20 20 20 20 20 20 20  |...[.....       |
00000120  20 20 20 20 20 20 5c 30  34 2a 2a 2a 20 45 52 52  |      \04*** ERR|
00000130  4f 52 3a 20 54 48 49 53  20 4d 45 44 49 41 20 43  |OR: THIS MEDIA C|
00000140  41 4e 4e 4f 54 20 42 4f  4f 54 20 49 4e 20 4c 45  |ANNOT BOOT IN LE|
00000150  47 41 43 59 20 4d 4f 44  45 20 2a 2a 2a 5c 30 37  |GACY MODE ***\07|
00000160  0d 0a 00 0d 0a 0d 0a 20  20 20 20 20 20 20 20 20  |.......         |
00000170  20 20 20 20 5c 37 30 50  6c 65 61 73 65 20 72 65  |    \70Please re|
00000180  6d 6f 76 65 20 74 68 69  73 20 6d 65 64 69 61 20  |move this media |
00000190  61 6e 64 20 70 72 65 73  73 20 61 6e 79 20 6b 65  |and press any ke|
000001a0  79 20 74 6f 20 72 65 62  6f 6f 74 5c 30 37 00 00  |y to reboot\07..|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  02 00 ee fe ff d2 01 00  00 00 ff ff ff ff 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages ================================

File descriptor 63 (pipe:[93097]) leaked on lvs invocation. Parent PID 13547: /bin/bash
```

---

### Post by oldfred on 2020-08-17
Please use Code Tags if posting longer terminal or text output. Easy to add with Forum's advanced reply and # icon.

But with Boot-Repair better to just post the link to the Summary Report it gives you.

You must have an UEFI setting somewhere:
> Error: NVram is locked

Report also only shows sda, no NVMe drive.
Either needs firmware update or settings in UEFI to be seen.

---

### Post by flexbriggs on 2020-08-18
Hey @oldfred sorry about that. This is my first post here. I will use Code tags next time. 

In the MSI Bios, the boot mode is "UEFI". And the reason the report only shows SDA is because I took out the NVME's and have been 
testing with SSD's so I wouldn't harm my good hard drives. The errors I've been getting have been the same between the hard drives, so 
I have a hard time imagining it's the hard drive's fault.

What does "NVram is locked" mean? For your information, after building the PC, I inserted one M.2 drive in the computer, installed Windows 10
then removed the M.2 Drive, and inserted my 2nd M.2 Drive and attempted to install Linux on it. After failing I took out that M.2 drive and replaced
it with a SSD for further testing. If there's any more info I can provide, please let me know. Thank you.

---

### Post by oldfred on 2020-08-18
NVRAM is where your UEFI settings are stored. And any other settings you can change in UEFI.
You see boot settings with
sudo efibootmgr -v

For Security reasons, some UEFI prevent various things by default and assume secure boot. User can change most of those settings, even with secure boot on, if required. Most have to turn on allow USB boot or full USB support as booting another system from USB is not secure.

You must also have a setting that prevents write into NVMRAM unless you change it. Check your manual. A few systems also have more settings if you set a UEFI password. But never lose that password or you may have a brick. Or reset password to blank when done configuring system.

Most UEFI motherboards also have settings to "disable" a drive. That way you do not have to physically remove a M.2 drive as that is not always easy and those M.2 parts are not designed for frequent changes.

Update:
Looked at your manual. Not really different than the Gigabyte Intel Z170 and older Asus z97 boards I have.
My Gigabyte is somewhat like your MSI, as UEFI and CSM settings are combined. My motherboard would only boot in UEFI mode with "UEFI only setting". And its UEFI settings were all under CSM item. But systems are really UEFI with CSM as an option not the other way around.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
Check your settings for CSM & UEFI.

---

### Post by flexbriggs on 2020-08-19
@oldfred thank you for your continued attempts to help me fix this. After checking my BIOS, I have learned that my PC has the following settings: SATA Mode: AHCI, XHCI Hand-Off Enabled, Legacy USB Support Enabled, BIOS UEFI/CSM Mode: CSM, Boot mode select LEGACY + UEFI, Not actually seeing anything on Secure Boot (can't find it for some reason). 

Are any of these settings making it impossible to install Ubuntu. If there are any other settings you would like to see, please let me know. Thanks again!

---

### Post by oldfred on 2020-08-19
My Asus motherboard would not boot in UEFI mode even with "UEFI or CSM" mode. Only  the "UEFI only" mode would let me boot my install in UEFI mode.

Many systems do not call it UEFI Secure Boot, but have "Windows" or "Other". And fine print says if installing Windows 7 (now obsolete) use Other. Windows 7 did not support Secure Boot. So Other is the setting to have Secure Boot off. You also do not get CSM/Legacy/BIOS boot mode if Secure Boot is on.

---

### Post by flexbriggs on 2020-08-20
I have tried the install with UEFI mode and UEFI + Legacy Mode and both gave me the same error. Any other ideas?

---

### Post by oldfred on 2020-08-20
Did you update UEFI & SSD firmware?
And threads with similar systems as posted in post #6?

Vendors do not always say an UEFI update applies to Linux.

Now year old, but still applies.
AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
ASUS ROG CROSSHAIR VIII HERO WiFi - update supports Ubuntu 19.04
MSI has also put out BIOS updates in Aug as a "beta" though without explicitly acknowledging the Linux fix.

---

### Post by flexbriggs on 2020-08-20
Sorry, I am a bit confused. Are we simply talking about BIOS updates? Or can you directly update the UEFI and SSD? If that's the case, I am having a hard time finding updates for those components directly. I have noticed that in the past couple days there has been a BIOS update (mine is 7C56vA1, and the latest is 7C56vA2). Do you recommend installing that, would that solve the problem? 
The update says:
- Improved boot time.
- Improved PS/2 KB/Mouse compatibility.
- Improved memory compatibility.
But, it also says not to update if not necessary.

---

### Post by oldfred on 2020-08-20
You never know for sure. But I always update as they do not always mention all the fixes, as shown in Phoronix link.

It has been UEFI since Microsoft required UEFI in 2012 with release of Windows 8. But many vendors still call it BIOS.

And SSD almost always need firmware update. Some vendors have that as part of UEFI/BIOS update. But those are mostly system vendors like laptops.

I have Samsung NVMe drive and they have a bootable ISO with the update for my specific model NMVe drive. It looked like an old BIOS screen and only offered update for latest firmware on my drive. For Windows they seem to have an application for updates.

---

### Post by flexbriggs on 2020-08-20
I'll look for updates and give it a shot and get back to you. Thank you. If these updates do not work, is it possible the motherboard just isn't compatible with Linux?

---

### Post by oldfred on 2020-08-20
Others have posted that that AMD based version works. 
But different vendors, do things differently. 


The link from Phoronix mentions a Linux issue from a year ago, where vendors with AMD did have to update UEFI, but that has been resolved. So I would expect it to work.

---

### Post by flexbriggs on 2020-08-20
I updated everything, turned on the UEFI mode, booted from a UEFI flash drive. I followed the instructions from the youtube video: [https://www.youtube.com/watch?v=xxef7Veeg6A](https://www.youtube.com/watch?v=xxef7Veeg6A)

Failed once again on the grub-install /dev/nvme0n.. can't remember the exact message. 

Here is a tail call to the /var/log/syslog if this helps
```
ubuntu@ubuntu:~$ tail /var/log/syslog
Aug 21 03:01:30 ubuntu /plugininstall.py:     install.run()
Aug 21 03:01:30 ubuntu /plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 62, in wrapper
Aug 21 03:01:30 ubuntu /plugininstall.py:     func(self)
Aug 21 03:01:30 ubuntu /plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 233, in run
Aug 21 03:01:30 ubuntu /plugininstall.py:     self.configure_bootloader()
Aug 21 03:01:30 ubuntu /plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 929, in configure_bootloader
Aug 21 03:01:30 ubuntu /plugininstall.py:     raise install_misc.InstallStepError(
Aug 21 03:01:30 ubuntu /plugininstall.py: ubiquity.install_misc.InstallStepError: GrubInstaller failed with code 1
Aug 21 03:01:30 ubuntu /plugininstall.py: 
Aug 21 03:02:06 ubuntu systemd[1]: zsysd.service: Succeeded.

```

Also the sudo efibootmgr -v from earlier
```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0008
Timeout: 1 seconds
BootOrder: 0008,0000,0005
Boot0000* Windows Boot Manager    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0005* ubuntu    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0008* UEFI: VendorCoProductCode 2.00, Partition 1    PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/USB(7,0)/HD(1,GPT,5eb80d9d-e5b8-4236-93c3-b62ee86fc03d,0x800,0xeff7df)..BO

```

Does this give any insight on what could be throwing off the install of Ubuntu?

---

### Post by oldfred on 2020-08-20
If it has installed everything but grub, lets see what this says.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by flexbriggs on 2020-08-20
When you say live installer, do you mean while I'm still "trying ubuntu"? And sorry, I'm not following the instructions clearly. You want me to use the 2nd option and install boot-repair and use the recommended repair, then copy paste the log link afterwards?

And this is AFTER or BEFORE an attempted install of ubuntu 20.04?

Note: When I run boot-repair after a grub-install failure ubuntu install attempt, I get the following messages: /boot detected. Please check the options. I click OK and I'm brought to the boot-repair menu. I choose recommended repair and I get the errror message: /target detected. Please close the Ubuntu installer, then retry. The ubuntu installer is not open (to my knowledge). If it is, somehow in the background? how would I close that? Or am I supposed to be running boot-repair right when I boot into
a live usb ubuntu (before trying to install ubuntu 20.04 to the nvme)

Edit: I ran boot-repair using the advanced option, and got the following link ---->  [https://paste.ubuntu.com/p/Vqq9shPsz4/](https://paste.ubuntu.com/p/Vqq9shPsz4/)

---

### Post by oldfred on 2020-08-21
I do not think Ubuntu live installer installer mounts /target until you start install.
It is both an installer and a flash drive you want to always have to make repairs. Just like you have a Windows repair flash drive. 
I keep multiple flash drives, but usually have a full install & some or most of my backup data on them also.

You show one ESP - efi system partition nvme0n1p1, but report shows no Windows UEFI boot files and shows an old BIOS boot  loader in MBR????
Windows only boots from gpt partitioned drives with UEFI from ESP. Did you tell Ubuntu installer to reformat the ESP during install & it then erased your Windows boot files?
You can only fix that using a Windows repair disk and a full set of repairs to restore the .efi & support boot files to ESP.

I prefer to have an ESP on each drive. But Ubuntu's Ubiquity installer only installs to first ESP seen, usually the Windows drive.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Some have posted just removing boot/esp flags from Windows ESP and adding an ESP with those flags on the Ubuntu drive also works.
Some also in UEFI change Windows drive to "disabled" so not seen from Ubuntu installer.

Ubuntu does not now require swap partition, but uses a swap file. It will use swap partition if found. Those with servers still suggest a swap partition, but otherwise you should not need it.

Please review link in my signature below. 

Some like to separate / (root) from data with either partition(s) for /home and/or data.

---

### Post by flexbriggs on 2020-08-21
Hey @oldfred thanks for the reply. So you're telling me that the EFI partition on my windows hard drive was changed during an Ubuntu install? And that it was GPT and now it's MBR, and I need to repair that in the windows OS?
I was able to boot to my windows hard drive just fine... And in disk management the efi partition says healthy..
What do I do to repair that?

I'll attempt an install using #23 and #26. By the way, how would you disable the Windows drive? That seems like it could work. And removing/adding flags would be done in GParted right?

---

### Post by oldfred on 2020-08-21
My older motherboard's UEFI have 'disabled' settings for drives. And it is same entry as changing to AHCI. Mine seems to be an all or nothing, but newer systems should have a per drive as NVMe devices are often hard to remove and are not really designed to be installed & removed a lot. 

Gparted is one way to change flags. You can use terminal commands and if Gnome, Disks Utility (which I do not recommend for most things).

---

### Post by flexbriggs on 2020-08-21
Hey @oldfred I removed the boot flag on the Windows EFI partition before entering the install, and I also attempted your #23 solution of umount and mount on the /target/boot/efi (Just to make sure, that would be mounting the EFI partition
of my linux hard drive nvme1, correct?), and I am still getting the grub-error. I feel like I'm running out of solutions here, and may just resort to running a virtual machine of linux instead.

---

### Post by oldfred on 2020-08-21
Did you check what mount the installer had?
And was the partition you mounted flagged as an ESP?

And if install otherwise completed, you often can just use Boot-Repair to install/reinstall grub.

---

### Post by flexbriggs on 2020-08-21
The EFI partion of the nvme needs to be on /target/boot/efi, correct? I did check and it was correct, but I unmounted and mounted it again.

---

### Post by oldfred on 2020-08-21
Sounds about right.

I normally check mounts before I start. Then as password screen as by then it has added the required mounts. And that is where I change it.

From one of my installs:
```
# mount of ESP does not show until about end of username & password entry screen
ubuntu-mate@ubuntu-mate:~$ history
    1  mount
    2  sudo umount /target/boot/efi
    3  sudo mount /dev/sdc1 /target/boot/efi
    4  mount
    5  history

```

---

### Post by flexbriggs on 2020-08-21
Right, I did exactly that... but instead of sdc1 I did nvme1n1p1 or something along those lines. I coped the directory from fdisk -l

---

### Post by flexbriggs on 2020-08-23
Hey @oldfred I have tried again to install Linux, and have run into some errors. I am hoping maybe you can help me decode these error messages? Maybe they hint to the solution? (By the way, I'm attempted Linux Mint 20.04, though it's giving the same errors as Ubuntu)

1. Here is the state of my hard drives (nvme1 is the hard drive I'm trying to install linux to)
```
Disk /dev/nvme1n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: ADATA SX6000PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcdb854d4

Device         Boot    Start        End   Sectors   Size Id Type
/dev/nvme1n1p1 *        2048    1050623   1048576   512M ef EFI (FAT-12/16/32)
/dev/nvme1n1p2       1050624   72730623  71680000  34.2G 83 Linux
/dev/nvme1n1p3      72730624 1000214527 927483904 442.3G 83 Linux


```

I went through the installer, chose "Something else" and partitioned out EFI, Root, and Home partitions (EFI, ext4, ext4 respectively). I then continued on and on the last page of the installer, checked the mounts in the terminal using the "mount" command.
I do not have a copy/paste of this, but do remember it to be ...
/dev/nvme1n1p1 on /target/boot/efi
/dev/nvme1n1p2 on /target
/dev/nvme1n1p3 on /target/home
I thought the mounts looked correct, so I clicked install and ran into the error (again) "Executing grub-install /dev/nvme1n1 failed. This is a fatal error". It seems as if it's failing to register my EFI partition? When I expanded the error message I got 
Internal error ... failed to register the EFI boot entry: Operation not permitted ... error: Running 'grub-install --force "/dev/nvme1n1" failed.

I then shut down the computer and booted back up to the live USB and ran the following, trying to manually re-install grub correctly. But I got some errors 
```
mint@mint:~$ sudo mount /dev/nvme1n1p2 /mnt
mint@mint:~$ sudo mount /dev/nvme1n1p1 /mnt/boot/efi
mint@mint:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
mint@mint:~$ sudo chroot /mnt
root@mint:/# apt-get update
Ign:1 http://packages.linuxmint.com ulyana InRelease
Hit:2 http://packages.linuxmint.com ulyana Release                                                                                                             
Hit:3 http://archive.canonical.com/ubuntu focal InRelease                                                                                                      
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease                                 
Hit:5 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:7 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:8 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done
root@mint:/# apt-get install --reinstall grub-efi grub-efi-amd64 grub-efi-amd64-signed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc
The following NEW packages will be installed:
  grub-efi grub-efi-amd64
0 upgraded, 2 newly installed, 1 reinstalled, 2 to remove and 291 not upgraded.
Need to get 49.3 kB/519 kB of archives.
After this operation, 417 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 grub-efi-amd64 amd64 2.04-1ubuntu26.2 [46.7 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 grub-efi amd64 2.04-1ubuntu26.2 [2596 B]
Fetched 49.3 kB in 1s (62.5 kB/s)
Preconfiguring packages ...
(Reading database ... 290538 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64-signed_1.142.4+2.04-1ubuntu26.2_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.142.4+2.04-1ubuntu26.2) over (1.142.4+2.04-1ubuntu26.2) ...
(Reading database ... 290538 files and directories currently installed.)
Removing grub-gfxpayload-lists (0.7) ...
dpkg: grub-pc: dependency problems, but removing anyway as you requested:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not installed.
  Package grub-pc is to be removed.

Removing grub-pc (2.04-1ubuntu26.2) ...
Selecting previously unselected package grub-efi-amd64.
(Reading database ... 290516 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64_2.04-1ubuntu26.2_amd64.deb ...
Unpacking grub-efi-amd64 (2.04-1ubuntu26.2) ...
Selecting previously unselected package grub-efi.
Preparing to unpack .../grub-efi_2.04-1ubuntu26.2_amd64.deb ...
Unpacking grub-efi (2.04-1ubuntu26.2) ...
Setting up grub-efi-amd64 (2.04-1ubuntu26.2) ...
Trying to migrate /boot/efi into esp config
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Setting up grub-efi (2.04-1ubuntu26.2) ...
Setting up grub-efi-amd64-signed (1.142.4+2.04-1ubuntu26.2) ...
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for shim-signed (1.40.3+15+1533136590.3beb971-0ubuntu1) ...
Secure Boot not enabled on this system.

```

From what I am gathering here, it appears the computer is trying to install grub, but it can't find the EFI partition? But, as you can see in my fdisk code, it is there! It's there in GParted too, with the flags boot,esp

Any ideas?

---

### Post by dragonfly41 on 2020-08-23
> [COLOR=#000000][FONT=&quot]grub-install: error: failed to register the EFI boot entry: Operation not permitted.
I am reading this from the side stage.
Out of curiosity I searched .. and found this [freshly reported bug]("https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1872212"). I don't know if this is relevant.

OP has indicated Linux Mint installation.  Although I do not have Linux Mint I picked up a lot of tips from [this forum post]("https://forums.linuxmint.com/viewtopic.php?f=42&t=256750").

From this I installed refind as my "meta boot loader" (in /boot/efi/EFI/refind alongside others) and have not looked back. In last few days I have just installed Ubuntu 20.04 through mkusb into a second SSD added to a HDD/SSD dual boot configuration. rEFInd picked it up without sweat. So now I have: Windows 10 + Ubuntu 16.04 in main HDD, Ubuntu 18.04 in USB SSD1, Ubuntu 20.04 in USB SSD2 - and all showing in rEFInd menu. 

I am in the minority using rEFInd but there are so many posts on dual boot problems that I feel rEFInd requires more exposure to dig you out of a hole on occasions. When it is working you can always go into boot options and switch to ubuntu (GRUB).[/FONT][/COLOR]

---

### Post by oldfred on 2020-08-23
Moved to Mint sub-forum as not sure what changes to standard Ubuntu they make.

If reinstalling grub from live installer you typically have to mount the ESP & / and other system partitions, if you have them, with a chroot. 

Or manually boot into install, if you get grub> or grub rescue> from a partial grub install.

UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Many find using Boot-Repair to do the grub install, it walks you thru a minimal chroot.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)


I use rEFInd for emergency boot and have multiple flash drives and one USB SSD with rEFInd. My system gets confused sometimes as I have installs on multiple drives and then the UEFI does not want to boot anything. I have to disconnect most drives & use rEFInd. Once I had to totally reinstall UEFI, reset all UEFI boot entrys, remove all but one drive and boot with rEFInd. Most of the time system just boots, ok.

---

### Post by flexbriggs on 2020-08-23
Here is more information. Going through the install again, I thought I could provide the logs of some terminal info to respond to @dragonfly41, who referred me to a bug. The solution to the bug at [https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1872212](https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1872212) was to ensure the EFI partition was 
a primary partition. Below I will prove that it is before clicking the final install button.  

Note: Still installing Mint, but will go back to Ubuntu if needed.

Info on my drive
```
 sudo fdisk -l
Disk /dev/loop0: 1.75 GiB, 1863593984 bytes, 3639832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: ADATA SX6000PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2925A349-CE8D-4F08-B5C6-855FD1DBDE5C

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     206847    204800   100M EFI System
/dev/nvme0n1p2    206848     239615     32768    16M Microsoft reserved
/dev/nvme0n1p3    239616  999176274 998936659 476.3G Microsoft basic data
/dev/nvme0n1p4 999178240 1000212479   1034240   505M Windows recovery environment


Disk /dev/nvme1n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: ADATA SX6000PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcdb854d4

Device         Boot    Start        End   Sectors   Size Id Type
/dev/nvme1n1p1 *        2048     999423    997376   487M ef EFI (FAT-12/16/32)
/dev/nvme1n1p2        999424   69359615  68360192  32.6G 83 Linux
/dev/nvme1n1p3      69359616 1000214527 930854912 443.9G 83 Linux


Disk /dev/sda: 7.51 GiB, 8053063680 bytes, 15728640 sectors
Disk model: ProductCode     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B169E3E6-634E-496A-9EE6-ECE54A1EF8B4

Device     Start      End  Sectors  Size Type
/dev/sda1   2048 15728606 15726559  7.5G Microsoft basic data
```

As for the response to the Primary partition for EFI
```
sudo parted /dev/nvme1n1
GNU Parted 3.3
Using /dev/nvme1n1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ADATA SX6000PNP (nvme)
Disk /dev/nvme1n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  512MB   511MB   primary  fat32        boot, esp
 2      512MB   35.5GB  35.0GB  primary  ext4
 3      35.5GB  512GB   477GB   primary  ext4

```

And for the mounting before the install 
```
mint@mint:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=8116292k,nr_inodes=2029073,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=1632360k,mode=755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=/filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15062)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1632360k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/nvme1n1p2 on /target type ext4 (rw,relatime,errors=remount-ro)
/dev/nvme0n1p1 on /target/boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme1n1p3 on /target/home type ext4 (rw,relatime)
```

What's strange, and I'm not sure if maybe it's not updated... but GParted GUI says that p2 is at /target, and p3 is at /target/boot, but p1 is not mounted. After looking at the mount log, I noticed that
nvme0n1p1 is mounted to /target/boot/efi and not nvme1n1p1... interesting. 

I attempt to do this to fix it.
sudo umount /target/boot/efi
sudo mount /dev/nvme1n1p1 /target/boot/efi

And now the last bit of the mount log looks like this
```
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1632360k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/nvme1n1p2 on /target type ext4 (rw,relatime,errors=remount-ro)
/dev/nvme1n1p3 on /target/home type ext4 (rw,relatime)
/dev/nvme1n1p1 on /target/boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)

```

Also some general secure boot / uefi mode check ups
```
mint@mint:~$ sudo efibootmgr
BootCurrent: 0005
Timeout: 1 seconds
BootOrder: 0005,0000,0002,0004
Boot0000* Windows Boot Manager
Boot0002* ubuntu
Boot0004* ubuntu
Boot0005* UEFI: VendorCoProductCode 2.00, Partition 1
mint@mint:~$ sudo mokutil --sb-state
SecureBoot disabled
Platform is in Setup Mode
mint@mint:~$ 
```

Still... a grub error? The partitions seem completely fine, the mounts seem correct, what am I missing here?
@oldfred I noticed in the above code that I have ubuntu in Boot0002 and Boot0004, are both of them from failed installations in the past? Perhaps they're on my other drive and the Linux installer is getting
mixed up between them? If that's the case, do you have any suggestions on how to fix that?

Also here is some logs after the grub error
```
mint@mint:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=8116292k,nr_inodes=2029073,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=1632360k,mode=755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=/filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15062)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1632360k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/nvme1n1p2 on /target type ext4 (rw,relatime,errors=remount-ro)

```

```
mint@mint:~$ sudo fdisk -l
Disk /dev/loop0: 1.75 GiB, 1863593984 bytes, 3639832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: ADATA SX6000PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2925A349-CE8D-4F08-B5C6-855FD1DBDE5C

Device             Start        End   Sectors   Size Type
/dev/nvme0n1p1      2048     206847    204800   100M EFI System
/dev/nvme0n1p2    206848     239615     32768    16M Microsoft reserved
/dev/nvme0n1p3    239616  999176274 998936659 476.3G Microsoft basic data
/dev/nvme0n1p4 999178240 1000212479   1034240   505M Windows recovery environment


Disk /dev/nvme1n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: ADATA SX6000PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcdb854d4

Device         Boot    Start        End   Sectors   Size Id Type
/dev/nvme1n1p1 *        2048     999423    997376   487M ef EFI (FAT-12/16/32)
/dev/nvme1n1p2        999424   69359615  68360192  32.6G 83 Linux
/dev/nvme1n1p3      69359616 1000214527 930854912 443.9G 83 Linux


Disk /dev/sda: 7.51 GiB, 8053063680 bytes, 15728640 sectors
Disk model: ProductCode     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B169E3E6-634E-496A-9EE6-ECE54A1EF8B4

Device     Start      End  Sectors  Size Type
/dev/sda1   2048 15728606 15726559  7.5G Microsoft basic data
mint@mint:~$ 


```

```
mint@mint:~$ tail /var/log/syslog
Aug 24 01:47:04 mint rtkit-daemon[1634]: message repeated 3 times: [ Supervising 0 threads of 0 processes of 0 users.]
Aug 24 01:47:04 mint rtkit-daemon[1634]: Failed to make ourselves RT: Operation not permitted
Aug 24 01:47:04 mint rtkit-daemon[1634]: Supervising 0 threads of 0 processes of 1 users.
Aug 24 01:47:06 mint rtkit-daemon[1634]: message repeated 5 times: [ Supervising 0 threads of 0 processes of 1 users.]
Aug 24 01:47:06 mint systemd-resolved[1123]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Aug 24 01:47:06 mint systemd-resolved[1123]: message repeated 3 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.]
Aug 24 01:47:06 mint rtkit-daemon[1634]: Supervising 0 threads of 0 processes of 1 users.
Aug 24 01:47:07 mint rtkit-daemon[1634]: message repeated 3 times: [ Supervising 0 threads of 0 processes of 1 users.]
Aug 24 01:49:16 mint gnome-terminal-[14725]: g_menu_insert_item: assertion 'G_IS_MENU_ITEM (item)' failed
Aug 24 01:49:31 mint gnome-terminal-[14725]: g_menu_insert_item: assertion 'G_IS_MENU_ITEM (item)' failed


```

```
mint@mint:~$ sudo parted /dev/nvme1n1
GNU Parted 3.3
Using /dev/nvme1n1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ADATA SX6000PNP (nvme)
Disk /dev/nvme1n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  512MB   511MB   primary  fat32        boot, esp
 2      512MB   35.5GB  35.0GB  primary  ext4
 3      35.5GB  512GB   477GB   primary  ext4


```

Does any of this info help draw any conclusions? Thanks!

---

### Post by oldfred on 2020-08-24
> Disklabel type: dos

I have seen users install to MBR(msdos) partitioned drives in UEFI mode, but drive really should be gpt partitioned.

Change to gpt and try again.

Windows only installed to gpt with UEFI.
I do not think Ubuntu has changed to gpt only for UEFI, but it really should.

---

### Post by flexbriggs on 2020-08-24
That is really strange! I was just re-attempting before reading your comment, and while in the live session, without changing anything, it now says the disklabel type is gpt! Still giving me a grub-install error. 

I shut down and booted into the live USB and attempted to install boot-repair, using option 2 of the link you sent me earlier @oldfred and on Linux Mint 20.04, it's not responding to when I click "Recommended Repair", or "create bootinfo summary"
Weird, but maybe that's what I get for trying Mint instead of Ubuntu. Anyway, I'm going to attempt the chroot method. 

Also want to note that I removed my Windows hard drive out of the computer, so the only devices are the flash drive /dev/sda and the m.2 hard drive /dev/nvme0n1

Here is my attempted chroot mount code
```
mint@mint:~$ sudo mount /dev/nvme0n1p2 /mnt
mint@mint:~$ sudo mount /dev/nvme0n1p1 /mnt/boot/efi
mint@mint:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
mint@mint:~$ sudo chroot /mnt
root@mint:/# apt-get update
Ign:1 http://packages.linuxmint.com ulyana InRelease
Hit:2 http://packages.linuxmint.com ulyana Release                             
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease                         
Hit:4 http://security.ubuntu.com/ubuntu focal-security InRelease               
Hit:5 http://archive.canonical.com/ubuntu focal InRelease           
Hit:6 http://archive.ubuntu.com/ubuntu focal-updates InRelease
Hit:8 http://archive.ubuntu.com/ubuntu focal-backports InRelease
Reading package lists... Done
root@mint:/# apt-get install --reinstall grub-efi grub-efi-amd64 grub-efi-amd64-signed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc
The following NEW packages will be installed:
  grub-efi grub-efi-amd64
0 upgraded, 2 newly installed, 1 reinstalled, 2 to remove and 291 not upgraded.
Need to get 49.3 kB/519 kB of archives.
After this operation, 417 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 grub-efi-amd64 amd64 2.04-1ubuntu26.2 [46.7 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 grub-efi amd64 2.04-1ubuntu26.2 [2596 B]
Fetched 49.3 kB in 1s (67.8 kB/s)
Preconfiguring packages ...
(Reading database ... 290538 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64-signed_1.142.4+2.04-1ubuntu26.2_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.142.4+2.04-1ubuntu26.2) over (1.142.4+2.04-1ubuntu26.2) ...
(Reading database ... 290538 files and directories currently installed.)
Removing grub-gfxpayload-lists (0.7) ...
dpkg: grub-pc: dependency problems, but removing anyway as you requested:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not installed.
  Package grub-pc is to be removed.

Removing grub-pc (2.04-1ubuntu26.2) ...
Selecting previously unselected package grub-efi-amd64.
(Reading database ... 290516 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64_2.04-1ubuntu26.2_amd64.deb ...
Unpacking grub-efi-amd64 (2.04-1ubuntu26.2) ...
Selecting previously unselected package grub-efi.
Preparing to unpack .../grub-efi_2.04-1ubuntu26.2_amd64.deb ...
Unpacking grub-efi (2.04-1ubuntu26.2) ...
Setting up grub-efi-amd64 (2.04-1ubuntu26.2) ...
Trying to migrate /boot/efi into esp config
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Setting up grub-efi (2.04-1ubuntu26.2) ...
Setting up grub-efi-amd64-signed (1.142.4+2.04-1ubuntu26.2) ...
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for shim-signed (1.40.3+15+1533136590.3beb971-0ubuntu1) ...
Secure Boot not enabled on this system.
root@mint:/# 

```

and here is my hard drive info 
```
mint@mint:~$ sudo fdisk -l
Disk /dev/loop0: 1.75 GiB, 1863593984 bytes, 3639832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: ADATA SX6000PNP                         
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: EB6F8A0C-F306-4E60-8338-D38A3CEE71E3

Device            Start        End   Sectors   Size Type
/dev/nvme0n1p1     2048     999423    997376   487M EFI System
/dev/nvme0n1p2   999424   69359615  68360192  32.6G Linux filesystem
/dev/nvme0n1p3 69359616 1000214527 930854912 443.9G Linux filesystem


Disk /dev/sda: 7.51 GiB, 8053063680 bytes, 15728640 sectors
Disk model: ProductCode     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B169E3E6-634E-496A-9EE6-ECE54A1EF8B4

Device     Start      End  Sectors  Size Type
/dev/sda1   2048 15728606 15726559  7.5G Microsoft basic data

```

What else can I do here? Do you want me to try Ubuntu and re-attempt what I've been doing? Are there any error logs I can post here?

---

### Post by oldfred on 2020-08-24
Do you have latest firmware on your NVMe drives.
I have a Samsung NVMe drive and updated by downloading a bootable ISO that was just for my model. I think for Windows Samsung has an application for all its SSDs. Not sure about Adata.

---

### Post by flexbriggs on 2020-08-24
According to the Adata website and the Adata SSD toolbox, my NVME drives both have the latest firmware. So, it's not the hard drives. It shouldn't be the motherboard. I have the correct BIOS settings. The ISO image is directly from the Linux websites,
and are burned to the USB using Rufus (latest version) with a GPT format. And I do wipe the USB's using diskpart, cleaning them, and then re-imaged them, so the USB's should be okay too. I also removed the Windows hard drive from the computer, so I know that
the windows Hard drive isn't interfering with the process. I'm pretty stumped here, I feel like I've tried just about everything.

---

### Post by oldfred on 2020-08-24
> grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.

Those errors sound like they are from efibootmgr not being able to write into your UEFI.
Do you have some setting that locks UEFI entries? May be a separate security setting whether UEFI Secure Boot is on or not.

What does this show?
sudo efibootmgr -v

---

### Post by flexbriggs on 2020-08-24
Note: I put the windows hard drive M.2 back in the computer for school use. I wiped the linux M.2 I was trying to install on, but can try the installation again later. 

Anyway, I booted into the live USB and ran your command. efibootmgr wasn't a known command, so I installed it and got the following after running your command:
```
mint@mint:~$ sudo efibootmgr -v
BootCurrent: 0007
Timeout: 1 seconds
BootOrder: 0007,0000,0006
Boot0000* Windows Boot Manager    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0006* ubuntu    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0007* UEFI: VendorCoProductCode 2.00, Partition 1    PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/USB(7,0)/HD(1,GPT,2fd4d08d-1607-47cb-b67b-9cbfa4580bc2,0x800,0xeff7df)..BO
mint@mint:~$ 
```

Looking at the errors, it would make sense if there was some setting in the BIOS that was interfering with writing to the hard drive or something.

---

### Post by oldfred on 2020-08-24
That shows an Ubuntu UEFI boot entry in the same ESP as Windows.
This is the GUID/partUUID that the ESP on Windows drive has.
1e5db068-d49d-407d-9349-2d7fbcdfd6e3

You can see that with:
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

### Post by flexbriggs on 2020-08-24
Yeah I do need to fix that. However, when I removed the windows drive from the computer, I still got the same error. So I doubt the ubuntu uefi boot entry in there is the causation of the error. Thank you for your help though @oldfred

---

### Post by oldfred on 2020-08-24
I think the reinstall of grub, will use the mount in the fstab of the ESP as where to reinstall grub.
And then because that does not exist, it gives the error.

Try changing the UUID of the mount of the ESP in fstab from the Windows ESP's to the Ubuntu  drive's ESP.
Then see if the reinstall of grub works.

---

### Post by flexbriggs on 2020-08-26
Hey @oldfred Regarding the fstab solution, it did not work. 

I was going to provide code, but my monzilla firefox crashed and would not let me post the logs. I attempted the install from a live USB, and it gave me the grub-error as always.
I then checked fstab and it didn't have any UUID lines, so I did the manual mount grub-reinstall solution, it gave me the same errors as before, but after that fstab had some UUID's.
You were right, it did install on the wrong partition. It tried to install on the EFI from the window's hard drive. I changed the UUID to the EFI partition on the second hard drive, and
unfortunately I got the same errors when trying the grub-reinstall. Any other ideas??

---

### Post by oldfred on 2020-08-26
Post a new link from Boot-Repair for its report.

---

### Post by flexbriggs on 2020-08-26
Note: I am trying Ubuntu 20.04 again. Also, I disabled the boot flags on the windows hard drive in an attempt to fix the error, but no luck.

[https://paste.ubuntu.com/p/HpjM9VCKSW/](https://paste.ubuntu.com/p/HpjM9VCKSW/)

I am returning the flags for the windows hard drive now. Thanks @oldfred

---

### Post by oldfred on 2020-08-26
You never changed your second NVMe drive to gpt.

> nvme1n1    : notGPT,    

And your UEFI boot entries show MBR, which you can delete with efibootmgr.

```
Boot0006* ubuntu    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0007* ubuntu    HD(1,MBR,0x716656fb,0x800,0xf3800)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0009* ubuntu    HD(1,MBR,0x716656fb,0x800,0x100800)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO

```

Older gparted screenshot on changing to gpt. That erases drive.

---

### Post by flexbriggs on 2020-08-26
Hey @oldfred, I can get back to you in around 3 hours (after school). Just for clarification, the NVME drive is not GPT, thus the partitions are MBR. It's just the NVME, and not the live USB flash drive right?

And I can simply change that drive to GPT using GParted? Would that be the only thing I need to change? Sorry for the stupid questions, still trying to learn all this linux jargon

---

### Post by oldfred on 2020-08-26
If you use gparted to change it, then it is erased & you have to reinstall
It is possible to convert in place, better for data only drives.
But you can then a full reinstall grub & update any setting using UUID or GUID as those all change.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
sudo sfdisk -d /dev/sdc > backup_sdc.txt
sudo gdisk /dev/sdc
Used r, l, o, g, p, and w (write) or q to quit

In your case the example above with sdc, would be your nvme drive.

---

### Post by flexbriggs on 2020-08-26
I don't have any data on the nvme1n1 drive to save, as its sole purpose is to have the linux installation on it. I went to GParted and changed the partition table to GPT. 

Here's proof of the change
```

ubuntu@ubuntu:~$ sudo parted /dev/nvme1n1
GNU Parted 3.3
Using /dev/nvme1n1
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ADATA SX6000PNP (nvme)
Disk /dev/nvme1n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32              boot, esp
 2      538MB   37.2GB  36.7GB  ext4
 3      37.2GB  512GB   475GB   ext4

```

Everything was mounted correctly. I disabled the boot flags of the /dev/nvme0n1 too. Same grub error. 
Here is another boot-repair pastebin, maybe it has new information in it?
[https://paste.ubuntu.com/p/RRMcKddrDq/](https://paste.ubuntu.com/p/RRMcKddrDq/)

That was a solid find @oldfred I thought for sure changing the NVME to GPT would fix the problem. But, it seems like there is something else
messing it up? Thanks for continually trying to help me

---

### Post by oldfred on 2020-08-26
Lets delete these entries. Do not think it will solve any of the issues. But may avoid confusion on which Ubuntu entry is correct.

```
Boot0006* ubuntu    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0007* ubuntu    HD(1,MBR,0x716656fb,0x800,0xf3800)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0009* ubuntu    HD(1,MBR,0x716656fb,0x800,0x100800)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO

```
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

You can delete the /EFI/ubuntu in your Windows drive. nvme0n1p1/efi/ubuntu
And you have what looks like valid entry on Ubuntu drive. nvme1n1p1/efi/ubuntu

And boot entry to configure to full grub in your install looks correct as it has UUID of your new / (root) partition. 
```
search.fs_uuid b7e68ab3-88f8-4b32-b279-40230b145364 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


```

Can you reboot live installer in UEFI mode, not install mode and run Boot-Repair & its reinstall of grub?

Or then run this? You may have to install efibootmgr.

sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme1n1 -p 1

---

### Post by flexbriggs on 2020-08-27
So.. Just to re-confirm your instructions here @oldfred

Right now, I have the /dev/nvme1n1 with a partial failed install on it. I'm not wiping it. I'm booting into the live USB and then deleting Boot006, Boot0007, and Boot008 using efibootmgr.
I will also delete the EFI on the windows drive, and keep the entry which is on nvme1n1p1/efi/ubuntu.
Then you want me to run the Code you provided in the terminal...
Then reboot to the live installer in UEFI mode? How's that different than install mode? 
Once there, I will run boot-repair, and if that fails, the last line of code?

Thank you for working with me

---

### Post by oldfred on 2020-08-27
Yes.

Try the install of the UEFI boot entry using efibootmgr before running Boot-Repair.
And post any error messages.

Boot-Repair is complaining you have /target still mounted which is part of the install mounts.
It may be just boot flash drive and before clicking on any install options, add & run Boot-Repair.
I have not installed from USB flash drive for ages. (I use grub2's loopmount to directly boot an ISO ).

---

### Post by flexbriggs on 2020-08-27
I'm getting an error on the line efibootmgr install attempt

```

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0008
Timeout: 1 seconds
BootOrder: 0008,0000,0007
Boot0000* Windows Boot Manager    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0007* ubuntu    HD(1,GPT,fd82d002-a501-4ac6-a1e5-e7bd37762ef4,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0008* UEFI: VendorCoProductCode 2.00, Partition 1    PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/USB(7,0)/HD(1,GPT,6d9d6460-22f5-4c42-b815-b005c32c162b,0x800,0xeff7df)..BO
ubuntu@ubuntu:~$ sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme1n1 -p 1 
Could not prepare Boot variable: No such file or directory
ubuntu@ubuntu:~$ 
```

ALSO --> I ran a boot-repair "Recommended Repair" and got an error, here's the pastebin
Note: I read the paste bin, and it seemed like the windows hard drive was in hibernation mode (fast start up). 
[https://paste.ubuntu.com/p/xYsVt86KXV/](https://paste.ubuntu.com/p/xYsVt86KXV/)

I don't know why this is text is being marked as a link. Anyway. I disabled the fast start up on the windows OS, and re-ran boot-repair
and it ran into an error again, here is the up-to-date pastebin
[https://paste.ubuntu.com/p/zw9KxcR8pG/](https://paste.ubuntu.com/p/zw9KxcR8pG/)

Also... I noticed in the up-to-date pastebin that there is now an extra ubuntu Boot in my efibootmgr (/dev/nvme0n1 which should be /dev/nvme1n1). I'll delete the extra

---

### Post by oldfred on 2020-08-27
Anytime you boot into Windows it may do an update. 
And many  Windows updates turn fast startup back on.

I often have to click on text I copy from my Zim file that is after a link and click on the world with X icon above to remove it from being part of link.

You show a correct UEFI ubuntu entry for ESP on ubuntu NVMe drive.

```
Boot0000* Windows Boot Manager    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0007* ubuntu    HD(1,GPT,[COLOR=#ff0000]fd82d002-a501-4ac6-a1e5-e7bd37762ef4[/COLOR],0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0008* ubuntu    HD(1,GPT,1e5db068-d49d-407d-9349-2d7fbcdfd6e3,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO

nvme1n1p1 vfat     3AAC-CE48                            [COLOR=#ff0000]fd82d002-a501-4ac6-a1e5-e7bd37762ef4[/COLOR]     


```

UEFI uses GUID also known as partUUID to know which ESP to use to look for boot files.
Your fstab also seems to have all the correct UUIDs and the /EFI/ubuntu/grub.cfg has correct UUID for your / (root) partition to find your full grub.

Does entry 0007 work to boot even with the error on install.

---

### Post by flexbriggs on 2020-08-27
Oddly enough, the NVME isn't even showing up as an option in the Boot menu of the MSI bios.

---

### Post by oldfred on 2020-08-27
I just showed the NVMe drive's partUUID, that was not a boot entry.

0007 would be one of the ubuntu entries you should see in your UEFI as a boot option.
Often not clear which entry is which when you have same description, so may have to try both, if you have not housecleaned out the one from your Windows ESP (0008).

---

### Post by flexbriggs on 2020-08-27
I hear you. But, the BIOS only has 1 adata NVME. After school today I will remove and then install the NVME hard drive again to see if the BOOT in the bios will recognize it.

Interestingly enough, I changed the mode to CSM and the drive showed up... (but not in UEFI mode)

---

### Post by oldfred on 2020-08-27
Sounds like some setting in UEFI.
I would review manual on NVMe drives.
Many NVMe drives conflict with a SATA drive port so you cannot use some ports when using NVMe.
Perhaps a Boot setting, but seems more like drive setting in UEFI.

Have you updated UEFI?
And while different brand do you have IOMMU setting? That is more by chipset.
Asus Rog Strix B550 Disable IOMMU
[https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397](https://askubuntu.com/questions/1265397/unable-to-install-ubuntu-20-04-lts-via-live-usb-ryzen-5-3600?noredirect=1#comment2141726_1265397)

---

### Post by flexbriggs on 2020-08-28
I'm not sure. Tomorrow I will take out both NVME hard drives, and attempt an install on a samsung 860 evo SSD. I will boot into UEFI mode, with secure boot disabled. I will ensure the SSD is a GPT partition, and if not I will partition it using Gparted,
I will choose "Something else" and create a EFI 512mb, 35000mb ext4 formatted at /, and the rest ext4 formatted at /home. I will check the mount before installing... and hopefully this will work. I'll update you tomorrow about it.

---

### Post by oldfred on 2020-08-28
Samsung has firmware updates on its site.
My Samsung NVMe drive has a specific ISO just for update of my model in its support section.
 I think with Windows it has an application, but could not get the Linux version of that to work. App for Linux was in the commercial section of Samsung support.

---

### Post by flexbriggs on 2020-08-28
Alright, that sounds good. Yeah, the only operating system currently working on my computer right now is Windows.... so I'll update the firmware using the Window's Magician Software. Thanks for the heads up

---

### Post by flexbriggs on 2020-08-28
Here is the attempt for the new SSD install.

1) -- The SSD and BIOS are confirmed to be on the latest firmware updates.
2) The boot mode is confirmed to be UEFI
```

ubuntu@ubuntu:~$ #!/bin/bash
ubuntu@ubuntu:~$ [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
UEFI

```

3) Secure boot is disabled 
```

ubuntu@ubuntu:~$ mokutil --sb-state
SecureBoot disabled
Platform is in Setup Mode

```

4) Here is the drive information
```

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.98 GiB, 2103640064 bytes, 4108672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 29.9 MiB, 31334400 bytes, 61200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 255.58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Samsung SSD 860 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 7.51 GiB, 8053063680 bytes, 15728640 sectors
Disk model: ProductCode     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0091245B-D8C7-4F3A-82D2-5EC6B34F2CC6

Device     Start      End  Sectors  Size Type
/dev/sdb1   2048 15728606 15726559  7.5G Microsoft basic data

```

From what I can see, the samsung ssd, which I'll call /dev/sda does not have a partition type. Therefore I will go into gparted and create a new partition type of GPT and post updated fdisk below
```

Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Samsung SSD 860 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: DD95C7C8-88CB-4EB1-99DD-611D7AA346B9

Device        Start       End   Sectors   Size Type
/dev/sda1      2048   1050623   1048576   512M EFI System
/dev/sda2   1050624  72730623  71680000  34.2G Linux filesystem
/dev/sda3  72730624 976773119 904042496 431.1G Linux filesystem

```

Here is some parted info on the /dev/sda
```

ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 3.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA Samsung SSD 860 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32              boot, esp
 2      538MB   37.2GB  36.7GB  ext4
 3      37.2GB  500GB   463GB   ext4

(parted)  
```

Here is some parted information of the USB installer
```

ubuntu@ubuntu:~$ sudo parted /dev/sdb
GNU Parted 3.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: VendorCo ProductCode (scsi)
Disk /dev/sdb: 8053MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                 Flags
 1      1049kB  8053MB  8052MB  fat32        Main Data Partition  msftdata

(parted)                 

```

Will attempt install, and edit this afterwards with more information. . . .

Here is the Something else configuration
[ATTACH=CONFIG]286829[/ATTACH]

Here is the mount info 
```

ubuntu@ubuntu:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,noexec,relatime,size=8113472k,nr_inodes=2028368,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,noexec,relatime,size=1632360k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=/filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup2 on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15264)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
/var/lib/snapd/seed/snaps/snapd_8542.snap on /snap/snapd/8542 type squashfs (ro,nodev,relatime,x-gdu.hide)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1632356k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/fuse on /run/user/999/doc type fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/var/lib/snapd/seed/snaps/core18_1880.snap on /snap/core18/1880 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/seed/snaps/gnome-3-34-1804_36.snap on /snap/gnome-3-34-1804/36 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/seed/snaps/gtk-common-themes_1506.snap on /snap/gtk-common-themes/1506 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/seed/snaps/snap-store_467.snap on /snap/snap-store/467 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda2 on /target type ext4 (rw,relatime,errors=remount-ro)
/dev/sda1 on /target/boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda3 on /target/home type ext4 (rw,relatime)

```

Looks good, going to attempt the install now. . edit to come

"Executing grub-install /dev/sda failed. This is a fatal error." Looks like the hard drive was not the problem. I'm going to reboot and create a boot-repair summary for ya @oldfred
Could it be the motherboard? This felt like the cleanest attempt of a linux install possible. Everything was right leading up to the install.

---

### Post by oldfred on 2020-08-28
All that looks correct to me.
Good luck, I expect install to work.

---

### Post by flexbriggs on 2020-08-28
It unfortunately did not. Same error as before. I forgot to mention in my latest post that when I boot up from the USB, I edit the grub line parameter
linux          casper/vmlinuz    files=/cdrom/pressed/ubuntu.seed maybe-ubiquity quiet [nomodeset acpi=off] splash --- 
where the brackets are the inserted parameters.

I wiped and burned ubuntu 20.04 LTS again on the USB, for a fresh attempt as well.

Also, here is the boot-repair summary (not actually running the repair yet)
[https://paste.ubuntu.com/p/W58dCjJVBd/](https://paste.ubuntu.com/p/W58dCjJVBd/)

---

### Post by oldfred on 2020-08-28
Everything Boot-Repair is showing is correctly.
You have a new ubuntu entry in UEFI using GUID/partUUID of the new ESP to find shimx64.efi.
You have grub.cfg in  ESP that configfile entry is to full grub in your install.
And fstab has correct UUIDs.

If you needed nomodeset to boot live installer, you will need it for initial boot of install or until you go into system settings & install nVidia driver.

---

### Post by flexbriggs on 2020-08-28
If everything is correct, then why am I getting a grub-error? What would be my next step? Should I try the recommended boot-repair, or just try to boot into the hard drive.

Also... I am using the AMD Radeon RX 580 as a graphics card. Not nVidia. Should I wait to install the AMD drives until I boot in the hard drive correctly? And, how could I edit
the nomodeset when booting into a hard drive instead of a flash drive?

---

### Post by oldfred on 2020-08-28
I did not think nomodeset was required with AMD, but I used to have nVidia, but now only use the Intel Chips's video (as it was better than my old nVidia card). Not really up to speed on AMD video, but thought defaults now just worked.

What is exact grub error?

---

### Post by flexbriggs on 2020-08-28
Hey @oldfred I tried to boot into the hard drive, but was faced with a GNU grub menu. From there, I tried to find the kernel, but couldn't find it.

Anyway, so I ran boot-repair again, this time trying the recommended repair, and got a pastebin for you.
[https://paste.ubuntu.com/p/F9ztrXGy78/](https://paste.ubuntu.com/p/F9ztrXGy78/)

It looks like the 
grub-install: error: failed to register the EFI boot entry: Operation not permitted.

Is messing things up.

---

### Post by oldfred on 2020-08-28
If you got a grub menu, you are booting.

And you had working entry before. Not sure what re-running Boot-Repair did.
And I still do not understand the failed to register EFI boot entry, but more related to your UEFI than Ubuntu.

From grub menu are you able to boot the recovery mode? Second entry in grub menu.
That should take you to a command line or a menu of options. But without a gui.

---

### Post by flexbriggs on 2020-08-28
Sorry, I meant that I was booting to a GNU Grub, not a grub menu. Are  you thinking this is something to do with the moderboard, perhaps a BIOS  setting I'm missing or something? I could always just replace the  motherboard...

---

### Post by oldfred on 2020-08-29
If you are getting grub> can you manually boot?

First try:
configfile (hd0,2)/boot/grub/grub.cfg

Or:
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/boot/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/boot/initrd.img
boot

---

### Post by flexbriggs on 2020-08-29
When I woke up today, I booted into the hard drive without the USB in the computer, and it booted into Linux successfully. I have no idea why it’s working now. I’m skeptical really. Is there a way I can confirm that the installation is complete? Or if I need to finish it manually? Also, if I put the windows nvme back in the computer, could I just boot into Linux and update grub for dual boot? Thanks!

---

### Post by oldfred on 2020-08-29
I expect you can plug in Windows NVMe and update grub.

Only issue may be if drive 0 & drive 1 get changed. Not sure how two NVMe drives are ordered in UEFI.
With SATA it is port order and sometimes that makes a difference. And some NVMe drives can conflict with SATA ports.

---

### Post by flexbriggs on 2020-08-30
I was able to make it work. Can now dual boot as I desired. To be honest -- I'm not entirely sure what the solution was to this problem. But, I'm glad it's working. Thanks for all your help @oldfred

---

### Post by oldfred on 2020-08-30
Took a bit, but glad you got it working.

---

### Post by donjuane2 on 2020-10-25
Laptop: Lenovo Flex 5 (how I gave up UEFI and lived to tell)

I worked for over a year trying to install both Mint and Windows on my laptop (had a working laptop before this one but wearing out my second keyboard after 4 years of use, I bought another laptop) and finally got the new one working yesterday.   I was holding off moving to the new laptop until I could figure out how to install both Linux and Windows fairly seamlessly and it took me over a year working here and there (as I regained my patience) to finally get it working.  

- download fresh install of Windows 10 from MS (registration for Win on my laptop is in the bios)
- backed up photos, documents, etc from small work I'd done in Windows
- purchased EaseUS Partition master to create a USB bootable WinPE ISO with PM on the drive
- used Rufus to create GPT formatted USB stick to install WinPE USB bootable copy of Partition Master
- used Windows UEFI interface (via Windows settings) to boot from the USB stick (only way I could make laptop boot from USB)
- used EaseUS to convert the GPT formatted SSD on the laptop to MBR 
- struck F2 after restart to change BIOS secure boot off and change storage setting from raid to non-raid for storage option
- also  change BIOS type setting from UEFI to Legacy
- used RUFUS to re-format all my USB bootable thumb drives from GPT to MBR
- used EaseUS to delete all partitions on SSD and create a single NTFS for Windows 10
- used EaseUS command line (with Win 10 on another USB drive) to install fresh copy of Windows 10 back on the drive
- used EaseUS to create an unallocated space just beyond where the Windows partition was by stealing some space from Windows
- used USB bootable thumb drive (Rufus/MBR option) with Mint on it to install Mint on the unallocated space
- now the Linux boot manager (forgot the name, Grub or something like that) to choose windows or Mint
- downloaded the GUI "app" version of the same boot-manager "manager" and changed default boot to Windows
- so far so good

---

### Post by oldfred on 2020-10-25
Do not recommend MBR(msdosl) & BIOS boot, but if it works for you that is ok.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

