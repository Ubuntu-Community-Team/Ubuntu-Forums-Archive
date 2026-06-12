---
title: "need some help with my ssd"
date: 2019-02-17
forum: MINT
---

### Post by guece on 2019-02-17
[http://paste.ubuntu.com/p/P847jqYZ3w/](http://paste.ubuntu.com/p/P847jqYZ3w/)

---

### Post by yancek on 2019-02-17
Why are you posting?  The boot repair output shows that you are booting from a Linux Mint on a usb and you have a 119GB drive with nothing on it, no partitions or filesystem.  Interestingly, the efibootmgr output shows and entry for Linpux Lite.  Did this computer come with Linpus Lite.  What are your intentions?  Do you want to install Mint?

---

### Post by howefield on 2019-02-17
Thread moved to the "*MINT*" forum.

---

### Post by guece on 2019-02-17
no i dont want mint 
there has to be a win 10 64 installation but i cannot boot into it 
so i tryed with usb mint to look at but i have no clue how to fix that

---

### Post by oldfred on 2019-02-17
You show no evidence of Windows or any NTFS partitions.
You do show this error:
> Invalid MBR Signature found.


So you may have NTFS partitions that cannot be seen. 

But new systems are required by vendors to use UEFI with gpt partitioning, not MBR partitioning.
And you do not have a Windows UEFI boot entry in UEFI boot menu.

Generally better to use Windows tools for Windows.
Does testdisk show anything on sda?
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
      
 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by guece on 2019-02-17
thank you for reply
testdisk didnt find partion


```
Sun Feb 17 18:52:39 2019
Command line: TestDisk

TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 4.15.0-20-generic (#21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018) x86_64
Compiler: GCC 7.2
ext2fs lib: 1.44.1, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none, curses lib: ncurses 6.0
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       250069680 sectors
/dev/sda: user_max   250069680 sectors
/dev/sda: native_max 250069680 sectors
/dev/sda: dco        250069680 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - 0 sectors, sector size=512
Hard disk list
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63, sector size=512 - HFS128G39TND-N210A, S/N:EI83N068410503Q1A, FW:30001P10
Disk /dev/sdb - 15 GB / 14 GiB - CHS 14875 64 32, sector size=512 - SanDisk Ultra, FW:1.00
Disk /dev/sdc - 16 GB / 14 GiB - CHS 15259 64 32, sector size=512 - Kingston DT 101 II, FW:1.00

Partition table type default to Intel
Disk /dev/sda - 128 GB / 119 GiB - HFS128G39TND-N210A
Partition table type: EFI GPT

Analyse Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63
Bad GPT partition, invalid signature.
Trying alternate GPT
Bad GPT partition, invalid signature.
Current partition structure:
Bad GPT partition, invalid signature.
Trying alternate GPT
Bad GPT partition, invalid signature.

search_part()
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63

Results

interface_write()
 
No partition found or selected for recovery
simulate write!

TestDisk exited normally.
```

---

### Post by oldfred on 2019-02-17
Please use code tags with longer text or terminal output.
Easy to add code tags with forum's advanced editor and # icon.

What does this show?
sudo gdisk -l /dev/sda

But you are not showing NTFS anywhere. Did you overwrite entire drive with previous install?

---

### Post by guece on 2019-02-17
```
mint@mint:~$  sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Model: HFS128G39TND-N21
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 3D9FFE91-D501-4B3E-837D-3FC993A9FFA4
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2048-sector boundaries
Total free space is 250069613 sectors (119.2 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
mint@mint:~$
```


i got the laptop from a friend he says it was windows 10 home installed 
he said it stopped worked and doesnt find a boot parition

---

### Post by oldfred on 2019-02-17
It looks like it stopped working because he erased it.

---

### Post by guece on 2019-02-17
any chance to get it back

i need the recovery part to get a fresh win install for him

---

### Post by yancek on 2019-02-17
In post 6, you show the following:  Partition table type: EFI GPT and just below that it shows:  Bad GPT partition, invalid signature
It looks like everything was deleted regarding windows including the EFI, system and recovery partitions.  If there is any possibility, I expect you would need some type of windows software.

---

### Post by oldfred on 2019-02-17
If system is a newer UEFI system, it has product key inside UEFI. So if you reinstall in UEFI boot mode, it will automatically use valid product key.

       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

---

### Post by guece on 2019-02-17
yes i tried just to install win 10 from usb i read also that the product key should be in the bios 
but the instalation stopped because my ssd will probably be broken 
befor i saw in mint linux that the ssd will be broken in the next 24 hour

---

### Post by guece on 2019-02-18
can someone please explain what is going on with my ssd

i dont understand what this errors mean and how i can fix it

the ssd dont allow to format or partition 

smartctl

```
mint@mint:~$ sudo smartctl -a /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-20-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     HFS128G39TND-N210A
Serial Number:    EI83N068410503Q1A
Firmware Version: 30001P10
User Capacity:    128,035,676,160 bytes [128 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    Solid State Device
Form Factor:      M.2
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Mon Feb 18 11:58:32 2019 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
No failed Attributes found.

General SMART Values:
Offline data collection status:  (0x03)    Offline data collection activity
                    is in progress.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32)    The self-test routine was interrupted
                    by the host with a hard or soft reset.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x19) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0002)    Does not save SMART data before
                    entering power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  10) minutes.

SMART Attributes Data Structure revision number: 0
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   166   166   006    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0032   253   100   036    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       52
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       517
100 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       181920
168 Unknown_Attribute       0x0032   253   100   000    Old_age   Always       -       0
169 Unknown_Attribute       0x0032   099   099   000    Old_age   Always       -       20
171 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
174 Unknown_Attribute       0x0030   100   100   000    Old_age   Offline      -       11
175 Program_Fail_Count_Chip 0x0032   253   253   000    Old_age   Always       -       0
176 Erase_Fail_Count_Chip   0x0032   253   253   000    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0032   100   100   000    Old_age   Always       -       5
178 Used_Rsvd_Blk_Cnt_Chip  0x0032   100   100   000    Old_age   Always       -       23
179 Used_Rsvd_Blk_Cnt_Tot   0x0032   100   100   000    Old_age   Always       -       123
180 Unused_Rsvd_Blk_Cnt_Tot 0x0032   100   100   000    Old_age   Always       -       2517
184 End-to-End_Error        0x0032   253   253   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   253   253   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   030   000   000    Old_age   Always       -       30 (Min/Max 12/43)
195 Hardware_ECC_Recovered  0x0032   253   253   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   253   100   036    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0032   253   253   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0032   253   253   000    Old_age   Always       -       0
204 Soft_ECC_Correction     0x000e   100   097   000    Old_age   Always       -       12
212 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
234 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       549
241 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       153
242 Total_LBAs_Read         0x0032   100   100   000    Old_age   Always       -       1789
250 Read_Error_Retry_Rate   0x0032   100   100   000    Old_age   Always       -       8721

SMART Error Log Version: 1
ATA Error Count: 551 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 551 occurred at disk power-on lifetime: 52 hours (2 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 41 00 00 00 00 00  Error: ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 30 00 00 00 40 40      00:41:50.260  WRITE FPDMA QUEUED
  47 00 01 30 08 00 a0 a0      00:41:50.260  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0      00:41:50.260  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0      00:41:50.260  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 a0      00:41:50.260  IDENTIFY DEVICE

Error 550 occurred at disk power-on lifetime: 52 hours (2 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 41 00 00 00 00 00  Error: ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 28 00 00 00 40 40      00:41:50.230  WRITE FPDMA QUEUED
  47 00 01 30 08 00 a0 a0      00:41:50.230  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0      00:41:50.230  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0      00:41:50.230  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 a0      00:41:50.230  IDENTIFY DEVICE

Error 549 occurred at disk power-on lifetime: 52 hours (2 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 41 00 00 00 00 00  Error: ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 90 00 00 00 40 40      00:41:50.200  WRITE FPDMA QUEUED
  47 00 01 30 08 00 a0 a0      00:41:50.200  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0      00:41:50.200  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0      00:41:50.200  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 a0      00:41:50.200  IDENTIFY DEVICE

Error 548 occurred at disk power-on lifetime: 52 hours (2 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 41 00 00 00 00 00  Error: ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 80 00 00 00 40 40      00:41:50.150  WRITE FPDMA QUEUED
  60 08 78 18 00 00 40 40      00:41:36.860  READ FPDMA QUEUED
  60 08 70 08 00 00 40 40      00:41:36.860  READ FPDMA QUEUED
  60 08 68 00 00 00 40 40      00:41:36.860  READ FPDMA QUEUED
  60 08 e8 00 10 00 40 40      00:41:36.860  READ FPDMA QUEUED

Error 547 occurred at disk power-on lifetime: 51 hours (2 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 41 00 00 00 00 00  Error: ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 18 e0 00 00 00 40 40      00:11:03.280  WRITE FPDMA QUEUED
  61 18 d8 98 c2 e7 40 40      00:11:03.280  WRITE FPDMA QUEUED
  47 00 01 30 08 00 a0 a0      00:11:03.280  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0      00:11:03.280  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0      00:11:03.280  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

Selective Self-tests/Logging not supported

 
```

and hdparm

```
mint@mint:~$ sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       HFS128G39TND-N210A                      
    Serial Number:      EI83N068410503Q1A   
    Firmware Revision:  30001P10
    Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Supported: 9 8 7 6 5 
    Likely used: 9
Configuration:
    Logical        max    current
    cylinders    16383    0
    heads        16    0
    sectors/track    63    0
    --
    LBA    user addressable sectors:   250069680
    LBA48  user addressable sectors:   250069680
    Logical  Sector size:                   512 bytes
    Physical Sector size:                  4096 bytes
    Logical Sector-0 offset:                  0 bytes
    device size with M = 1024*1024:      122104 MBytes
    device size with M = 1000*1000:      128035 MBytes (128 GB)
    cache/buffer size  = unknown
    Form Factor: unknown (0x0007]
    Nominal Media Rotation Rate: Solid State Device
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, no device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 1
    Advanced power management level: disabled
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
            Advanced Power Management feature set
            SET_MAX security extension
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
            WRITE_DMA_QUEUED_FUA_EXT
       *    WRITE_UNCORRECTABLE_EXT command
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Phy event counters
       *    READ_LOG_DMA_EXT equivalent to READ_LOG_EXT
            Non-Zero buffer offsets in DMA Setup FIS
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
            In-order data delivery
       *    Software settings preservation
            Device Sleep (DEVSLP)
       *    SANITIZE feature set
       *    CRYPTO_SCRAMBLE_EXT command
       *    BLOCK_ERASE_EXT command
       *    reserved 69[4]
       *    DOWNLOAD MICROCODE DMA command
       *    Data Set Management TRIM supported (limit 1 block)
       *    Deterministic read data after TRIM
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
    not    frozen
    not    expired: security count
        supported: enhanced erase
    2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT.
Device Sleep:
    DEVSLP Exit Timeout (DETO): 20 ms (default)
    Minimum DEVSLP Assertion Time (MDAT): 10 ms (default)
Checksum: correct

```

and fdisk returns me```
mint@mint:~$ sudo fdisk /dev/sda

Welcome to fdisk (util-linux 2.31.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0x4243c433.

Command (m for help): g
Created a new GPT disklabel (GUID: B96E04FF-2F5E-B041-AC48-96251BB6E200).

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
/dev/sda: close device failed: Input/output error

mint@mint:~$ 


```

---

