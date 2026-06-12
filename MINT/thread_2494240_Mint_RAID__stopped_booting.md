---
title: "Mint RAID  stopped booting"
date: 2024-01-09
forum: MINT
---

### Post by reshetovdenis on 2024-01-09
Hi, please help. My Ubuntu has stopped booting.
boot-repair-4ppa2074                                              [20240109_1949]

```
============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/nvme0n1 and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (mduuid/81614e8b27d500fdd516c634f1d7a592)/grub. It also embeds 
    following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos diskfilter mdraid1x biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/nvme1n1 and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (mduuid/81614e8b27d500fdd516c634f1d7a592)/grub. It also embeds 
    following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos diskfilter mdraid1x biosdisk
    ---------------------------------------------------------------------------

nvme0n1p1: _____________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

nvme0n1p2: _____________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

nvme1n1p1: _____________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

nvme1n1p2: _____________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

nvme1n1p3: _____________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

md/0: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

md/1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

md/2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /etc/fstab /etc/default/grub

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: ASPEED Graphics Family from ASPEED Technology, Inc.
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: L0.31(5.17) from American Megatrends International, LLC.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________


Partitions info (1/3): _________________________________________________________


Partitions info (2/3): _________________________________________________________


Partitions info (3/3): _________________________________________________________


fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 0xc1fe505d
         Boot    Start        End    Sectors   Size Id Type
nvme0n1p1          2048   67110911   67108864    32G fd Linux raid autodetect
nvme0n1p2      67110912   69208063    2097152     1G fd Linux raid autodetect
nvme0n1p3      69208064 2000407215 1931199152 920.9G fd Linux raid autodetect
Disk nvme1n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 0xf44fd805
         Boot    Start        End    Sectors   Size Id Type
nvme1n1p1          2048   67110911   67108864    32G fd Linux raid autodetect
nvme1n1p2      67110912   69208063    2097152     1G fd Linux raid autodetect
nvme1n1p3      69208064 2000407215 1931199152 920.9G fd Linux raid autodetect
Disk sda: 28.82 GiB, 30943995904 bytes, 60437492 sectors
Disk identifier: 0x14eb2669
     Boot   Start      End  Sectors  Size Id Type
sda1  *          0  5138431  5138432  2.5G  0 Empty
sda2           572     9067     8496  4.1M ef EFI (FAT-12/16/32)
sda3       5140480 60437491 55297012 26.4G 83 Linux
Disk md0: 31.97 GiB, 34325135360 bytes, 67041280 sectors
Disk md1: 1022 MiB, 1071644672 bytes, 2093056 sectors
Disk md2: 920.74 GiB, 988638674944 bytes, 1930934912 sectors

parted -lm (filtered): _________________________________________________________

sda:30.9GB:scsi:512:512:msdos:Kingston DataTraveler 3.0:;
2:293kB:4643kB:4350kB:::esp;
3:2632MB:30.9GB:28.3GB:ext4::;
nvme0n1:1024GB:nvme:512:512:msdos:SAMSUNG MZVLB1T0HBLR-00000:;
1:1049kB:34.4GB:34.4GB:::raid;
2:34.4GB:35.4GB:1074MB:::raid;
3:35.4GB:1024GB:989GB:::raid;
md2:989GB:md:512:512:loop:Linux Software RAID Array:;
1:0.00B:989GB:989GB:ext4::;
md0:34.3GB:md:512:512:loop:Linux Software RAID Array:;
1:0.00B:34.3GB:34.3GB:linux-swap(v1)::;
nvme1n1:1024GB:nvme:512:512:msdos:SAMSUNG MZVLB1T0HBLR-00000:;
1:1049kB:34.4GB:34.4GB:::raid;
2:34.4GB:35.4GB:1074MB:::raid;
3:35.4GB:1024GB:989GB:::raid;
md1:1072MB:md:512:512:loop:Linux Software RAID Array:;
1:0.00B:1072MB:1072MB:ext3::;

Free space >10MiB: ______________________________________________________________

sda: 4.43MiB:2510MiB:2506MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE            UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda         iso9660           2023-12-23-05-05-55-00                                                    Boot-Repair-Disk 64bit 
&#9500;&#9472;sda1      iso9660           2023-12-23-05-05-55-00               14eb2669-01                          Boot-Repair-Disk 64bit 
&#9500;&#9472;sda2      vfat              8D6C-A9F8                            14eb2669-02                          ESP                    
&#9492;&#9472;sda3      ext4              2f713068-b78e-4244-9697-fe8e03b912ef 14eb2669-03                          writable               
nvme0n1                                                                                                                        
&#9500;&#9472;nvme0n1p1 linux_raid_member 03e245d4-5f49-0ce4-f739-3d80f5d5ac16 c1fe505d-01                          rescue:0               
&#9474; &#9492;&#9472;md0     swap              b79ea468-99c9-49ee-bfc6-ca8f37da3ab1                                                             
&#9500;&#9472;nvme0n1p2 linux_raid_member 81614e8b-27d5-00fd-d516-c634f1d7a592 c1fe505d-02                          rescue:1               
&#9474; &#9492;&#9472;md1     ext3              f46bb5be-4dd8-4df4-9a68-2376de4e93a0                                                             
&#9492;&#9472;nvme0n1p3 linux_raid_member 831a9940-4c26-1e15-e19d-a51334eac5f3 c1fe505d-03                          rescue:2               
  &#9492;&#9472;md2     ext4              90b829bc-271e-4891-b9cc-e4e6740b0850                                                             
nvme1n1                                                                                                                        
&#9500;&#9472;nvme1n1p1 linux_raid_member 03e245d4-5f49-0ce4-f739-3d80f5d5ac16 f44fd805-01                          rescue:0               
&#9474; &#9492;&#9472;md0     swap              b79ea468-99c9-49ee-bfc6-ca8f37da3ab1                                                             
&#9500;&#9472;nvme1n1p2 linux_raid_member 81614e8b-27d5-00fd-d516-c634f1d7a592 f44fd805-02                          rescue:1               
&#9474; &#9492;&#9472;md1     ext3              f46bb5be-4dd8-4df4-9a68-2376de4e93a0                                                             
&#9492;&#9472;nvme1n1p3 linux_raid_member 831a9940-4c26-1e15-e19d-a51334eac5f3 f44fd805-03                          rescue:2               
  &#9492;&#9472;md2     ext4              90b829bc-271e-4891-b9cc-e4e6740b0850                                                             

Mount points (filtered): _______________________________________________________

                                                            Avail Use% Mounted on
/dev/sda1                                                       0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                                                   iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

======================== md/1/grub/grub.cfg (filtered) =========================

Ubuntu   md2
Ubuntu, with Linux 5.15.0-91-generic   md2
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

==================== md/1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   0.511875153 = 0.549621760    grub/grub.cfg                                  1
   0.527370453 = 0.566259712    grub/i386-pc/core.img                          1
   0.582439423 = 0.625389568    vmlinuz                                        8
   0.581066132 = 0.623915008    vmlinuz-5.15.0-53-generic                      7
   0.582439423 = 0.625389568    vmlinuz-5.15.0-91-generic                      8
   0.581066132 = 0.623915008    vmlinuz.old                                    7
   0.564598083 = 0.606232576    initrd.img                                     1
   0.510143280 = 0.547762176    initrd.img-5.15.0-53-generic                   1
   0.564598083 = 0.606232576    initrd.img-5.15.0-91-generic                   1
   0.510143280 = 0.547762176    initrd.img.old                                 1

========================== md/2/etc/fstab (filtered) ===========================

proc /proc proc defaults 0 0
UUID=b79ea468-99c9-49ee-bfc6-ca8f37da3ab1 none swap sw 0 0
UUID=f46bb5be-4dd8-4df4-9a68-2376de4e93a0 /boot ext3 defaults 0 0
UUID=90b829bc-271e-4891-b9cc-e4e6740b0850 / ext4 defaults 0 0

======================= md/2/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="consoleblank=0 systemd.show_status=true"
GRUB_TERMINAL=console

===================== md/2: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
-rwxr-xr-x 1 root root 43031 Apr 15  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Apr 15  2022 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sda



=================== blkid (filtered) before raid activation ====================

/dev/nvme0n1p1: UUID="03e245d4-5f49-0ce4-f739-3d80f5d5ac16" UUID_SUB="ce28d445-76ae-f967-0ed5-75175ca1fe22" LABEL="rescue:0" TYPE="linux_raid_member" PARTUUID="c1fe505d-01"
/dev/nvme0n1p2: UUID="81614e8b-27d5-00fd-d516-c634f1d7a592" UUID_SUB="e2129d70-e723-576c-9dc6-e31115f94456" LABEL="rescue:1" TYPE="linux_raid_member" PARTUUID="c1fe505d-02"
/dev/nvme0n1p3: UUID="831a9940-4c26-1e15-e19d-a51334eac5f3" UUID_SUB="dd4ccce2-e28d-a27e-c029-4a8255d43c36" LABEL="rescue:2" TYPE="linux_raid_member" PARTUUID="c1fe505d-03"
/dev/nvme1n1p1: UUID="03e245d4-5f49-0ce4-f739-3d80f5d5ac16" UUID_SUB="8d1e61d0-d898-9047-1770-0e7ec12f2dd8" LABEL="rescue:0" TYPE="linux_raid_member" PARTUUID="f44fd805-01"
/dev/nvme1n1p2: UUID="81614e8b-27d5-00fd-d516-c634f1d7a592" UUID_SUB="d1e5ebba-e1df-ec1f-ffb8-c5db5e949f77" LABEL="rescue:1" TYPE="linux_raid_member" PARTUUID="f44fd805-02"
/dev/nvme1n1p3: UUID="831a9940-4c26-1e15-e19d-a51334eac5f3" UUID_SUB="229f98a4-81d8-c63c-ac76-bf33b42257a0" LABEL="rescue:2" TYPE="linux_raid_member" PARTUUID="f44fd805-03"
/dev/sda1: BLOCK_SIZE="2048" UUID="2023-12-23-05-05-55-00" LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660" PTUUID="14eb2669" PTTYPE="dos" PARTUUID="14eb2669-01"
/dev/sda2: SEC_TYPE="msdos" LABEL_FATBOOT="ESP" LABEL="ESP" UUID="8D6C-A9F8" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="14eb2669-02"
/dev/sda3: LABEL="writable" UUID="2f713068-b78e-4244-9697-fe8e03b912ef" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="14eb2669-03"


==================================== dmraid ====================================

dmraid -si -c
no block devices found
dmraid -ay:
no block devices found
dmraid -sa -c:
no block devices found


==================================== mdadm =====================================
mdadm --assemble --scan

mdadm --detail --scan
ARRAY /dev/md/0 metadata=1.2 name=rescue:0 UUID=03e245d4:5f490ce4:f7393d80:f5d5ac16
ARRAY /dev/md/1 metadata=1.2 name=rescue:1 UUID=81614e8b:27d500fd:d516c634:f1d7a592
ARRAY /dev/md/2 metadata=1.2 name=rescue:2 UUID=831a9940:4c261e15:e19da513:34eac5f3
Successfully activated RAID.


==================== blkid (filtered) after raid activation ====================

/dev/nvme0n1p1: UUID="03e245d4-5f49-0ce4-f739-3d80f5d5ac16" UUID_SUB="ce28d445-76ae-f967-0ed5-75175ca1fe22" LABEL="rescue:0" TYPE="linux_raid_member" PARTUUID="c1fe505d-01"
/dev/nvme0n1p2: UUID="81614e8b-27d5-00fd-d516-c634f1d7a592" UUID_SUB="e2129d70-e723-576c-9dc6-e31115f94456" LABEL="rescue:1" TYPE="linux_raid_member" PARTUUID="c1fe505d-02"
/dev/nvme0n1p3: UUID="831a9940-4c26-1e15-e19d-a51334eac5f3" UUID_SUB="dd4ccce2-e28d-a27e-c029-4a8255d43c36" LABEL="rescue:2" TYPE="linux_raid_member" PARTUUID="c1fe505d-03"
/dev/nvme1n1p1: UUID="03e245d4-5f49-0ce4-f739-3d80f5d5ac16" UUID_SUB="8d1e61d0-d898-9047-1770-0e7ec12f2dd8" LABEL="rescue:0" TYPE="linux_raid_member" PARTUUID="f44fd805-01"
/dev/nvme1n1p2: UUID="81614e8b-27d5-00fd-d516-c634f1d7a592" UUID_SUB="d1e5ebba-e1df-ec1f-ffb8-c5db5e949f77" LABEL="rescue:1" TYPE="linux_raid_member" PARTUUID="f44fd805-02"
/dev/nvme1n1p3: UUID="831a9940-4c26-1e15-e19d-a51334eac5f3" UUID_SUB="229f98a4-81d8-c63c-ac76-bf33b42257a0" LABEL="rescue:2" TYPE="linux_raid_member" PARTUUID="f44fd805-03"
/dev/sda1: BLOCK_SIZE="2048" UUID="2023-12-23-05-05-55-00" LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660" PTUUID="14eb2669" PTTYPE="dos" PARTUUID="14eb2669-01"
/dev/sda2: SEC_TYPE="msdos" LABEL_FATBOOT="ESP" LABEL="ESP" UUID="8D6C-A9F8" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="14eb2669-02"
/dev/sda3: LABEL="writable" UUID="2f713068-b78e-4244-9697-fe8e03b912ef" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="14eb2669-03"
/dev/md2: UUID="90b829bc-271e-4891-b9cc-e4e6740b0850" BLOCK_SIZE="4096" TYPE="ext4"
/dev/md0: UUID="b79ea468-99c9-49ee-bfc6-ca8f37da3ab1" TYPE="swap"
/dev/md1: UUID="f46bb5be-4dd8-4df4-9a68-2376de4e93a0" SEC_TYPE="ext2" BLOCK_SIZE="4096" TYPE="ext3"


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by oldfred on 2024-01-09
Moved to the Mint sub-forum since not Ubuntu official flavor.

Added RAID to title as only a few know that.

You have old BIOS boot, but newer UEFI system as it has NVMe drives.

---

