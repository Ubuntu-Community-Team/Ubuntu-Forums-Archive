---
title: "Booting problem"
date: 2023-11-23
forum: MINT
---

### Post by rana009 on 2023-11-23
This is the report - 
```

boot-repair-4ppa200                                              [20231123_1325]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    489259008 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt2)/boot/grub. It also embeds following 
    components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 21.2
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdc1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /efi/boot/grubx64.efi 
                       /efi/boot/mmx64.efi /ldlinux.sys


================================ 1 OS detected =================================

OS#1:   Linux Mint 21.2 Victoria (21.2) on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: 2nd Generation Core Processor Family Integrated Graphics Controller from Intel Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.18(1.18) from FUJITSU // Phoenix Technologies Ltd.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


a9c517741ac31962d7feb152948ad1ee   sda4/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda4/BOOT/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda4/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda4/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda4/ubuntu/shimx64.efi
64349b3622c65f495a99dbf6102496e3   sda4/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    hasBIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda2    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
sda3    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda4    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda6    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda4    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda3    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda6    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 298.09 GiB, 320072933376 bytes, 625142448 sectors
Disk identifier: F88E9835-2992-4D12-8BC9-979B19AF5A4D
          Start       End   Sectors   Size Type
sda1  605468672 625141759  19673088   9.4G Linux swap
sda2       2048 292968447 292966400 139.7G Linux filesystem
sda3  292968448 488280063 195311616  93.1G Linux filesystem
sda4  488280064 489259007    978944   478M EFI System
sda5  489259008 489453567    194560    95M BIOS boot
sda6  489453568 605468671 116015104  55.3G Linux filesystem
Partition table entries are not in disk order.
Disk sdc: 14.45 GiB, 15514730496 bytes, 30302208 sectors
Disk identifier: 0x0e4338a5
      Boot Start      End  Sectors  Size Id Type
sdc1  *     2048 30302207 30300160 14.4G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:320GB:scsi:512:4096:gpt:ATA WDC WD3200BPVT-1:;
2:1049kB:150GB:150GB:ext4::;
3:150GB:250GB:100GB:ext4::;
4:250GB:251GB:501MB:fat32::boot, esp;
5:251GB:251GB:99.6MB:::bios_grub;
6:251GB:310GB:59.4GB:ext4::;
1:310GB:320GB:10.1GB:linux-swap(v1)::swap;
sdc:15.5GB:scsi:512:512:msdos:USB3.0 FLASH DRIVE:;
1:1049kB:15.5GB:15.5GB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL      PARTLABEL
sda                                                                                                  
&#9500;&#9472;sda1 swap     d373d1f0-460f-4229-afdc-25f0011fb1f6 8cbd2d05-fcb9-47ff-ad7a-4cc6a03528b1            
&#9500;&#9472;sda2 ext4     8322f48d-8e97-4c83-997b-21fa84d35bd8 31f6feb0-d146-4aa7-a012-c9a95ca1118a            
&#9500;&#9472;sda3 ext4     a7be83ae-f052-4bcb-be5e-73a8ee8737af f69d9d0a-90a6-4731-b0da-f8cdcf551fa6            
&#9500;&#9472;sda4 vfat     76D8-7530                            4fd1ccc3-ccef-4b48-8966-8a42c230f6cd            
&#9500;&#9472;sda5                                               54a3c87e-7ed6-4e0b-be9b-25174506624c            
&#9492;&#9472;sda6 ext4     50c80ff4-b47b-48ec-ab26-5b5a1de97644 65d8102b-81ad-492c-981c-40ac0cf9cefc            
sdb                                                                                                  
sdc                                                                                                  
&#9492;&#9472;sdc1 vfat     BC9A-1BFD                            0e4338a5-01                          LINUX MINT 

Mount points (filtered): _______________________________________________________

            Avail Use% Mounted on
/dev/sda2   120.4G   7% /mnt/boot-sav/sda2
/dev/sda3    86.4G   0% /mnt/boot-sav/sda3
/dev/sda4   470.9M   1% /mnt/boot-sav/sda4
/dev/sda6    51.4G   0% /mnt/boot-sav/sda6
/dev/sdc1    11.6G  20% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda2   ext4            rw,relatime
/dev/sda3   ext4            rw,relatime
/dev/sda4   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda6   ext4            rw,relatime
/dev/sdc1   vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

====================== sda2/boot/grub/grub.cfg (filtered) ======================

Linux Mint 21.2 Cinnamon   8322f48d-8e97-4c83-997b-21fa84d35bd8
Linux Mint 21.2 Cinnamon, with Linux 5.15.0-76-generic   8322f48d-8e97-4c83-997b-21fa84d35bd8
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sda2/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=8322f48d-8e97-4c83-997b-21fa84d35bd8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda4 during installation
UUID=76D8-7530  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda3 during installation
UUID=a7be83ae-f052-4bcb-be5e-73a8ee8737af /home           ext4    defaults        0       2
# /usr/local was on /dev/sda6 during installation
UUID=50c80ff4-b47b-48ec-ab26-5b5a1de97644 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=d373d1f0-460f-4229-afdc-25f0011fb1f6 none            swap    sw              0       0

======================= sda2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 128.147838593 = 137.597693952  boot/grub/grub.cfg                             1
   6.402446747 = 6.874574848    boot/grub/i386-pc/core.img                     1
  63.433643341 = 68.111355904   boot/vmlinuz                                   1
  63.433643341 = 68.111355904   boot/vmlinuz-5.15.0-76-generic                 1
 129.259586334 = 138.791424000  boot/initrd.img                                1
 129.259586334 = 138.791424000  boot/initrd.img-5.15.0-76-generic              1
 129.259586334 = 138.791424000  boot/initrd.img.old                            1

===================== sda2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Sep 20  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

=========================== sda2/etc/grub.d/35_fwupd ===========================

#! /bin/sh
# SPDX-License-Identifier: LGPL-2.1+
set -e
[ -d ${pkgdatadir:?} ]
# shellcheck source=/dev/null
. "$pkgdatadir/grub-mkconfig_lib"
if [ -f /var/lib/fwupd/uefi_capsule.conf ] &&
   ls /sys/firmware/efi/efivars/fwupd-*-0abba7dc-e516-4167-bbf5-4d9d1c739416 1>/dev/null 2>&1; then
      . /var/lib/fwupd/uefi_capsule.conf
      if [ "${EFI_PATH}" != "" ] && [ "${ESP}" != "" ]; then
      echo "Adding Linux Firmware Updater entry" >&2
cat << EOF
menuentry 'Linux Firmware Updater' \$menuentry_id_option 'fwupd' {
EOF
      ${grub_probe:?}
      prepare_grub_to_access_device '`${grub_probe} --target=device \${ESP}` | sed -e "s/^/\t/"'
cat << EOF
    chainloader ${EFI_PATH}
}
EOF
      fi
fi

===================== sda4/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 8322f48d-8e97-4c83-997b-21fa84d35bd8 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sdc1/boot/grub/grub.cfg (filtered) ======================

Start Linux Mint 21.2 Cinnamon 64-bit
Start Linux Mint 21.2 Cinnamon 64-bit (compatibility mode)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

========================= sdc1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdc1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdc1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda2,
using the following options:  sda4/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Blockers in case of suggested repair: __________________________________________

 The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Linux Mint 21.2 Victoria (21.2) entry (sda4/efi/****/grub****.efi (**** will be updated in the final message) file) !
The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.

```

Can anyone help me?
Thanks

---

### Post by oldfred on 2023-11-23
Moved to Mint sub-forum since not Ubuntu official flavor.

Please use Code Tags for any terminal or long text output. Easy to add with Forum's advanced Editor & # icon.
But with Boot-Repair better to just post link it gives to pastebin site.

Do not mix UEFI & BIOS.
Since UEFI system, you need to always boot in UEFI mode to avoid confusion.

You have grub installed in very old BIOS boot mode & in UEFI boot mode. Since fstab mount shows mount of ESP, last install/fix was UEFI mode.
Make sure system is set to boot in UEFI mode, with UEFI secure boot off.

How you boot install media, UEFI or BIOS/Legacy/CSM is then how it installs or repairs your system. Always use UEFI mode.

---

