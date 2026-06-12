---
title: "[ERROR] The execution of &lt;&lt;grub-install /dev/sda&gt;&gt; failed.  This is a fatal error."
date: 2023-07-27
forum: MINT
---

### Post by garox23 on 2023-07-27
Hello Ubuntu community, how are you? I hope you are well. I need help with this error, I try to install **Ubuntu 22.04.2 LTS **on my HP Laptop, but for some reason when I'm installing it, when it is finishing installing, and comes the part of when it tries to install Grub, I get this error.

[B]"The execution of <<grub-install /dev/sda>> failed.  This is a fatal error."
[/B]
Previously a few days ago, I had already installed Ubuntu on this laptop, the first time I did it, it didn't give me any problems and it installed correctly. I used it for a few days, and deleted the partition where Ubuntu was installed, to create a new partition with more space, the previous partition only had 40Gb of storage and I created this new partition to add a little more storage. It should be noted that I have Windows 10, in a separate partition and for the installation of Ubuntu, I created another separate partition of 80Gb.

I hope you can help me.

Thanks.

---

### Post by Rubi1200 on 2023-07-27
Hi and welcome to the forums :-)

Let me summarize: currently there is no Ubuntu install on the laptop, correct?

Have you checked BIOS to make sure fast startup and secure boot are disabled before attempting to install Ubuntu?

Best thing is to run the boot info script report in my signature and post the results here for us. No repair, just the summary report please.

Thanks.

---

### Post by garox23 on 2023-07-28
Yes, I don't currently have Ubuntu installed on the 80gb partition I created, I had previously installed ubuntu on this laptop as mentioned and it installed with no problems.


The laptop BIOS  is update, the drivers are update too, my laptop is a HP ProBook 650 G2

---

### Post by Rubi1200 on 2023-07-29
Please provide the boot info summary report I asked for. It will help diagnose the issue. No personally identifiable information is collected, if that is a concern.

Thanks.

---

### Post by yancek on 2023-07-29
Generally best to just shrink the windows partition and leave unallocated space as you will need to create a Linux filesystem on the partition and you can't do that from windows but can do during the install.  If you have windows installed in UEFI mode, you also need to boot and install Ubuntu in UEFI mode.  Did you do that?  It may have been possible to enlarge the Ubuntu partition or to create another partition for Ubuntu rather than reinstall.  Consider that option in the future

Posting the output of the boot repair script will probably give enough information to solve the problem.

---

### Post by garox23 on 2023-08-02
```
boot-repair-4ppa200                                              [20230802_2223]


============================== Boot Info Summary ===============================


 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /bootmgr /Windows/System32/winload.exe


sda4: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 21.2
    Boot files:        /etc/fstab /etc/default/grub


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 32864 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /efi/boot/grubx64.efi 
                       /efi/boot/mmx64.efi /ldlinux.sys




================================ 2 OS detected =================================


OS#1:   Windows 8 or 10 on sda3
OS#2:   Linux Mint 21.2 on sda4


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: Skylake GT2 [HD Graphics 520] from Intel Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: N76 Ver. 01.60(1.60) from HP
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled - SecureBoot disabled - Please report this message to [email]boot.repair@gmail.com[/email].
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,0007,0008,0000,0002,0006
Boot0000* Windows Boot Manager	HD(1,GPT,174e8181-943a-4da1-a1c7-b8c98f989027,0x800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}........................ISPH
Boot0001* ubuntu	HD(1,GPT,174e8181-943a-4da1-a1c7-b8c98f989027,0x800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* HP v150w 070011C745AE2F66	PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)N.....YM....R,Y.....ISPH
Boot0006* hp DVDRW GUD1N 	PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)N.....YM....R,Y.....ISPH
Boot0007* IPV6 Network - Intel(R) Ethernet Connection I219-V	PciRoot(0x0)/Pci(0x1f,0x6)/MAC(ec8eb5a10d9a,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.....ISPH
Boot0008* IPV4 Network - Intel(R) Ethernet Connection I219-V	PciRoot(0x0)/Pci(0x1f,0x6)/MAC(ec8eb5a10d9a,0)/IPv4(0.0.0.00.0.0.0,0,0)N.....YM....R,Y.....ISPH


725b49513de6143386868608003c2870   sda1/Boot/bootx64.efi
85fa9d77b929ec4231aba29476574eb6   sda1/Boot/fbx64.efi
469e608783843a701d172242f016c79c   sda1/Boot/mmx64.efi
4e8b20a69032adbb60ea19d3d09f7637   sda1/HP/DI.efi
5ddf997e8b025bfbc2009e85b32f60dc   sda1/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   sda1/ubuntu/mmx64.efi
251e647380cfb4246ec84bffeee1e74a   sda1/ubuntu/shimx64.efi
a96537c7fa189564b38473456b33f7e5   sda1/HP/BiosUpdate/CryptRSA.efi
e991dcae4b3fd2f6b2231072c3f80edf   sda1/HP/BiosUpdate/HpBiosMgmt.efi
cd1c62403e2274a8cff3ddd5e8771329   sda1/HP/BiosUpdate/HpBiosUpdate.efi
a96537c7fa189564b38473456b33f7e5   sda1/HP/SystemDiags/CryptRSA.efi
4e8b20a69032adbb60ea19d3d09f7637   sda1/HP/SystemDiags/DI.efi
e2d941b2ff51fcdd68a4e5828258d61a   sda1/HP/SystemDiags/HpSysDiags.efi
a8d4d9c2cef1cbbba29cf8a0128cb720   sda1/HP/SystemDiags/SystemDiags.efi
81f3c3b088444c6c9f71673b8ae0945c   sda1/Microsoft/Boot/bootmgfw.efi
9e44b1bd33336231b48914b7fc3d4164   sda1/Microsoft/Boot/bootmgr.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda1	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far
sda3	: is-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios
sda4	: is-os,	64, apt-get,	signed grub-pc grub-efi ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios
sda5	: no-os,	32, nopakmgr,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	farbios


Partitions info (2/3): _________________________________________________________


sda1	: is---ESP,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda3	: isnotESP,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	notwinboot
sda4	: isnotESP,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda5	: isnotESP,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot


Partitions info (3/3): _________________________________________________________


sda1	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda3	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda
sda4	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda5	: not--sepboot,	no---boot,	part-has-no-fstab,	not-sep-usr,	no---usr,	part-has-no-fstab,	no--grub.d,	sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: BD32DD9D-E7EE-42F3-B718-DF76C95E8860
          Start       End   Sectors   Size Type
sda1       2048    206847    204800   100M EFI System
sda2     206848    239615     32768    16M Microsoft reserved
sda3     239616 376165493 375925878 179.3G Microsoft basic data
sda4  376166400 499047259 122880860  58.6G Microsoft basic data
sda5  499048448 500115455   1067008   521M Windows recovery environment
Disk sdb: 28.91 GiB, 31042043904 bytes, 60628992 sectors
Disk identifier: 0x0089e247
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 60628991 60626944 28.9G  c W95 FAT32 (LBA)


parted -lm (filtered): _________________________________________________________


sda:256GB:scsi:512:512:gpt:ATA LITEON L8H-256V2:;
1:1049kB:106MB:105MB:fat32:EFI system partition:boot, esp;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres;
3:123MB:193GB:192GB:ntfs:Basic data partition:msftdata;
4:193GB:256GB:62.9GB:ext4:Basic data partition:msftdata;
5:256GB:256GB:546MB:ntfs::hidden, diag;
sdb:31.0GB:scsi:512:512:msdos:hp v150w:;
1:1049kB:31.0GB:31.0GB:fat32::boot, lba;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL    PARTLABEL
sda                                                                                                
&#9500;&#9472;sda1 vfat     F43E-B5AC                            174e8181-943a-4da1-a1c7-b8c98f989027          EFI system partition
&#9500;&#9472;sda2                                               4408f428-11c2-4b5c-a8d3-74d924fe29ce          Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     E0A8D1C6A8D19B7C                     f51ee7bd-8f01-4e6d-a8f4-bbc3aa26dd48          Basic data partition
&#9500;&#9472;sda4 ext4     9950d5bd-78bb-4e54-be49-dfc9f3b9f7b9 d24b242f-943c-4e70-b270-f72b40844b76          Basic data partition
&#9492;&#9472;sda5 ntfs     467AAEC57AAEB0DB                     d3668d6e-add5-4b53-9b01-e75961c189c4          
sdb                                                                                                
&#9492;&#9472;sdb1 vfat     664F-34EA                            0089e247-01                          JUAN USB 


Mount points (filtered): _______________________________________________________


            Avail Use% Mounted on
/dev/sda1        0 100% /target/boot/efi
/dev/sda3   121.1G  32% /mnt/boot-sav/sda3
/dev/sda4    43.5G  19% /target
/dev/sda5    88.4M  83% /mnt/boot-sav/sda5
/dev/sdb1    26.1G  10% /cdrom


Mount options (filtered): ______________________________________________________


/dev/sda1   vfat            rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4   ext4            rw,relatime,errors=remount-ro
/dev/sda5   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb1   vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro


========================== sda4/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=9950d5bd-78bb-4e54-be49-dfc9f3b9f7b9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=F43E-B5AC  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


======================= sda4/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


==================== sda4: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 197.998096466 = 212.598837248  boot/vmlinuz                                   2
 197.998096466 = 212.598837248  boot/vmlinuz-5.15.0-76-generic                 2
 208.667778015 = 224.055320576  boot/initrd.img                                1
 208.667778015 = 224.055320576  boot/initrd.img-5.15.0-76-generic              1
 208.667778015 = 224.055320576  boot/initrd.img.old                            1


===================== sda4: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Sep 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom


=========================== sda4/etc/grub.d/35_fwupd ===========================


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


====================== sdb1/boot/grub/grub.cfg (filtered) ======================


Start Linux Mint 21.2 Cinnamon 64-bit
Start Linux Mint 21.2 Cinnamon 64-bit (compatibility mode)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory


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
            ?? = ??             ldlinux.sys                                    1






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda4,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file


Blockers in case of suggested repair: __________________________________________


/target detected. Please close the Linuxmint installer, then retry. 


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Linux Mint 21.2 entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)


*******.us ko ()

```

---

### Post by garox23 on 2023-08-02
I tried installing Linux Mint to see if it was an error in my computer, and if I got the same error with Linux Mint, something that had never happened before, I used the Repair boot app and there I indicated the error. Will I have to format windows?

---

### Post by yancek on 2023-08-03
So  you have this problem when you select Boot0001 (ubuntu) in your BIOS firmware to boot?  Can you go into the BIOS boot option to boot from EFI file and select ubuntu/grubx64.efi to boot?  If so, what happens?  Boot repair shows the correct Mint and windows EFI boot files.  The EFI partition info near the top of the page does not show the expected EFI files but they show further down in the boot repair info.  If you are booting this from the Mint installer be sure you do not have the installer started when running the repair.

---

### Post by garox23 on 2023-08-03
Yes, when I go to the BIOS and go to the boot menu, I get Ubuntu (I don't have it installed) there must be the problem, previously I selected it, and it doesn't boot anything, the screen goes black and returns to the boot menu.

---

### Post by garox23 on 2023-08-03
I recorded a video to make it look better, but the site won't let me upload mp4 files.

---

### Post by yancek on 2023-08-03
>  Yes, when I go to the BIOS and go to the boot menu, I get Ubuntu 

That's because Mint and several other Ubuntu derivatives use "ubuntu" as the name and directory for an EFI boot.  If this was working, selecting ubuntu as you show in your UEFI boot menu would boot Mint.

Have you selected ubuntu in the UEFI menu since you installed Mint?  Do you get the same problem?  Have you tried going to the BIOS and select boot from EFI file and select the /EFI/ubuntu/grubx64.efi entry?  What happens?

Can you use the install USB, boot it and mount the EFI partition on the internal hard drive which shows as sda1 in your boot repair output?  You should see several directories there"

> Boot  HP  Microsoft  ubuntu 

If you don't see those directories, particularly the ubuntu directory, you need to reinstall grub.

---

### Post by oldfred on 2023-08-03
Moved to Mint Sub-Forum.

Mint is not an official flavor of Ubuntu, but uses parts of Ubuntu. 
I believe it uses the same boot, so boot entry for 'ubuntu' is really for Mint.

---

