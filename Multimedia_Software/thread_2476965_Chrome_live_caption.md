---
title: "Chrome live caption"
date: 2022-07-12
forum: Multimedia Software
---

### Post by esso10 on 2022-07-12
chrome live caption works for only minutes and then it's not showing.

---

### Post by mIk3_08 on 2022-07-14
> **esso10 said:**
> chrome live caption works for only minutes and then it's not showing.
Please run the command below in your terminal and post the result here in this thread. To open the terminal in your desktop just press ctrl and alt + t or just find it under installed Ubuntu applications, Regards and cheers.
```
hostnamectl status
```

---

### Post by esso10 on 2022-07-14
for what?

---

### Post by mIk3_08 on 2022-07-15
> **esso10 said:**
> for what?
Please run the script on this give url page below and post the information or pastebin link in this thread. Regards and cheers.
```
https://github.com/UbuntuForums/system-info
```

---

### Post by esso10 on 2022-07-17
> **mIk3_08 said:**
> Please run the script on this give url page below and post the information or pastebin link in this thread. Regards and cheers.
```
https://github.com/UbuntuForums/system-info
```

Are you a hacker?

---

### Post by bobunderwood99 on 2022-07-17
No. See

[https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)

---

### Post by esso10 on 2022-07-24
> **mIk3_08 said:**
> Please run the command below in your terminal and post the result here in this thread. To open the terminal in your desktop just press ctrl and alt + t or just find it under installed Ubuntu applications, Regards and cheers.
```
hostnamectl status
```

Static hostname: lava
   Pretty hostname: Lava
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 8b8051ec359344cd9d3ef5ecc099ba9a
           Boot ID: 17777511ea51469586e0dc0501b96037
  Operating System: Ubuntu 20.04.4 LTS
            Kernel: Linux 5.15.0-41-generic
      Architecture: x86-64

I am sorry I thought you were a hacker!

---

### Post by esso10 on 2022-07-24
> **mIk3_08 said:**
> Please run the script on this give url page below and post the information or pastebin link in this thread. Regards and cheers.
```
https://github.com/UbuntuForums/system-info
```

Uploaded Report: 2022-07-24  16:08:42 EET (+0200):
View at: [https://termbin.com/z10u](https://termbin.com/z10u)

Is it correct like this?

---

### Post by #&amp;thj^% on 2022-07-24
> **esso10 said:**
> Uploaded Report: 2022-07-24  16:08:42 EET (+0200):
View at: [https://termbin.com/z10u](https://termbin.com/z10u)

Is it correct like this?

Yep, perfect.
If you run it from a terminal it will provide more info for us to help you with.
IE:
```
/usr/bin/google-chrome-stable %U
Gtk-Message: 09:30:14.645: Failed to load module "appmenu-gtk-module"
[percpu.cc : 535] RAW: rseq syscall failed with errno 22 after membarrier sycall succeeded.
WARNING: Logging before InitGoogle() is written to STDERR
W0000 00:00:1658676804.687918  220899 soda_async_impl.cc:334] Creating soda_impl.
W0000 00:00:1658676804.687943  220899 soda_async_impl.cc:336] Created with thread priority 0
W0000 00:00:1658676804.758698  220899 terse_processor.cc:342] TISID disabled.
W0000 00:00:1658676804.769071  223204 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676804.769337  220899 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676804.769761  220899 soda_async_impl.cc:561] SODA session starting (require_hotword:0, hotword_timeout_in_millis:0, trigger_type:TRIGGER_TYPE_UNSPECIFIED, hybrid_asr_config.mode:MODE_DEFAULT)
W0000 00:00:1658676804.770043  223180 soda_async_impl.cc:1327] SODA received first mic audio buffer, size in bytes: 1920, format: 1, channels: 1, : sample rate: 48000
W0000 00:00:1658676805.270423  223180 soda_async_impl.cc:1046] Not receiving any loopback audio in 500ms. Last audio received time: 0, Current time in us: 1658676805270423
W0000 00:00:1658676827.273442  223180 soda_async_impl.cc:945] SODA stopped processing audio, mics audio processed in millis: 22680, loopback audio processed in millis: 0
W0000 00:00:1658676827.273654  223221 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676827.276045  223180 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676827.281856  223180 soda_async_impl.cc:1000] SODA session stopped due to: STOP_CALLED
W0000 00:00:1658676827.301889  220899 soda_async_impl.cc:1076] Deleting soda_impl
W0000 00:00:1658676827.340229  220899 soda_async_impl.cc:334] Creating soda_impl.
W0000 00:00:1658676827.340265  220899 soda_async_impl.cc:336] Created with thread priority 0
W0000 00:00:1658676827.406775  220899 terse_processor.cc:342] TISID disabled.
W0000 00:00:1658676827.411987  224805 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676827.412624  220899 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676827.413436  220899 soda_async_impl.cc:561] SODA session starting (require_hotword:0, hotword_timeout_in_millis:0, trigger_type:TRIGGER_TYPE_UNSPECIFIED, hybrid_asr_config.mode:MODE_DEFAULT)
W0000 00:00:1658676827.413731  224786 soda_async_impl.cc:1327] SODA received first mic audio buffer, size in bytes: 1920, format: 1, channels: 1, : sample rate: 48000
W0000 00:00:1658676827.918215  224786 soda_async_impl.cc:1046] Not receiving any loopback audio in 500ms. Last audio received time: 0, Current time in us: 1658676827918215
W0000 00:00:1658676833.660560  224822 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676833.661518  224786 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676852.239917  225221 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676852.241568  224786 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676871.118998  226498 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
```

---

### Post by esso10 on 2022-07-24
> **1fallen said:**
> Yep, perfect.
If you run it from a terminal it will provide more info for us to help you with.
IE:
```
/usr/bin/google-chrome-stable %U
Gtk-Message: 09:30:14.645: Failed to load module "appmenu-gtk-module"
[percpu.cc : 535] RAW: rseq syscall failed with errno 22 after membarrier sycall succeeded.
WARNING: Logging before InitGoogle() is written to STDERR
W0000 00:00:1658676804.687918  220899 soda_async_impl.cc:334] Creating soda_impl.
W0000 00:00:1658676804.687943  220899 soda_async_impl.cc:336] Created with thread priority 0
W0000 00:00:1658676804.758698  220899 terse_processor.cc:342] TISID disabled.
W0000 00:00:1658676804.769071  223204 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676804.769337  220899 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676804.769761  220899 soda_async_impl.cc:561] SODA session starting (require_hotword:0, hotword_timeout_in_millis:0, trigger_type:TRIGGER_TYPE_UNSPECIFIED, hybrid_asr_config.mode:MODE_DEFAULT)
W0000 00:00:1658676804.770043  223180 soda_async_impl.cc:1327] SODA received first mic audio buffer, size in bytes: 1920, format: 1, channels: 1, : sample rate: 48000
W0000 00:00:1658676805.270423  223180 soda_async_impl.cc:1046] Not receiving any loopback audio in 500ms. Last audio received time: 0, Current time in us: 1658676805270423
W0000 00:00:1658676827.273442  223180 soda_async_impl.cc:945] SODA stopped processing audio, mics audio processed in millis: 22680, loopback audio processed in millis: 0
W0000 00:00:1658676827.273654  223221 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676827.276045  223180 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676827.281856  223180 soda_async_impl.cc:1000] SODA session stopped due to: STOP_CALLED
W0000 00:00:1658676827.301889  220899 soda_async_impl.cc:1076] Deleting soda_impl
W0000 00:00:1658676827.340229  220899 soda_async_impl.cc:334] Creating soda_impl.
W0000 00:00:1658676827.340265  220899 soda_async_impl.cc:336] Created with thread priority 0
W0000 00:00:1658676827.406775  220899 terse_processor.cc:342] TISID disabled.
W0000 00:00:1658676827.411987  224805 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676827.412624  220899 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676827.413436  220899 soda_async_impl.cc:561] SODA session starting (require_hotword:0, hotword_timeout_in_millis:0, trigger_type:TRIGGER_TYPE_UNSPECIFIED, hybrid_asr_config.mode:MODE_DEFAULT)
W0000 00:00:1658676827.413731  224786 soda_async_impl.cc:1327] SODA received first mic audio buffer, size in bytes: 1920, format: 1, channels: 1, : sample rate: 48000
W0000 00:00:1658676827.918215  224786 soda_async_impl.cc:1046] Not receiving any loopback audio in 500ms. Last audio received time: 0, Current time in us: 1658676827918215
W0000 00:00:1658676833.660560  224822 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676833.661518  224786 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676852.239917  225221 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
W0000 00:00:1658676852.241568  224786 decoder_endpointer_stream.cc:68] Acoustic ep reader thread cancelled.
W0000 00:00:1658676871.118998  226498 portable_intended_query_stream.cc:236] Exiting due to stream cancellation.
```

[https://paste.ubuntu.com/p/ksjmhgHxNg/](https://paste.ubuntu.com/p/ksjmhgHxNg/)
```

Starting the Ubuntu Forums 'system-info' Report: 2022-07-24  18:06:18 EET (+0200)
    Part of the Ama-gi Project
    Version: 01.00-19, Script Date: 2022.06.21

---------------------------------------------------------------
Main Complaint: chrome caption doesn't work all the time
Problem Description:  some times transcription appears and some other times it doesn't.
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz
    Vendor: Intel Corp.
    Physical id: 0
    Bus info: cpu@0
    Version: Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz
    Slot: CPU 1
    Size: 2892MHz
    Capacity: 3300MHz
    Width: 64 bits
    Clock: 100MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse 
        sse2 ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs 
        bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq 
        dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 
        sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb pti 
        ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt 
        dtherm ida arat pln pts md_clear flush_l1d cpufreq
    Configuration: cores=2 enabledcores=2 threads=4

computer
    Description: Notebook
    Product: HP EliteBook 2560p (H0Q54EP#AK8)
    Vendor: Hewlett-Packard
    Version: A0001D02
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-2.6 dmi-2.6 smp vsyscall32
    Configuration:
        boot=normal
        chassis=notebook
        family=103C_5336AN
        sku=H0Q54EP#AK8
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         Hewlett-Packard
Bios Version:        68SSU Ver. F.29
Bios Release:        15.41
Board Vendor:        Hewlett-Packard
Board Name:          162B
Board Version:       KBC Version 04.23
Board Serial:        PCEYA001Y2J2ZR
Board Asset Tag:     

Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
   --- SecureBoot Status from 'mokutil':
    This would check / have checked if SecureBoot was enabled or not, 
    and checks if the system BIOS was UEFI or Lagacy only BIOS, 
    but package mokutil was not installed. If you would like to check
    this information, please install 'mokutil' and rerun script.

---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:          3.7Gi       2.2Gi       123Mi       405Mi       1.4Gi       890Mi
Swap:         2.0Gi       1.0Gi       1.0Gi

---------- IP Address Information:
  --- IP Address Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
4: enx028037ec0200: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: lava


---------- Storage Controller Information From 'lspci':
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Hewlett-Packard Company 6 Series/C200 Series Chipset Family 6 port Mobile SATA AHCI Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 31
    Region 0: I/O ports at 4088 [size=8]
    Region 1: I/O ports at 409c [size=4]
    Region 2: I/O ports at 4080 [size=8]
    Region 3: I/O ports at 4098 [size=4]
    Region 4: I/O ports at 4040 [size=32]
    Region 5: Memory at d4727000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Address: fee00358  Data: 0000
    Capabilities: [70] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [a8] SATA HBA v1.0 BAR4 Offset=00000004
    Capabilities: [b0] PCI Advanced Features
        AFCap: TP+ FLR+
        AFCtrl: FLR-
        AFStatus: TP-
    Kernel driver in use: ahci
    Kernel modules: ahci


---------- File system specs from 'df -h':
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda7      ext4       65G   32G   30G  52% /
/dev/sda6      vfat      512M   24K  512M   1% /boot/efi

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: TOSHIBA MQ01ABD0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x397d34dc

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 242767871 242765824 115.8G  7 HPFS/NTFS/exFAT
/dev/sda2       242767872 350879651 108111780  51.6G  7 HPFS/NTFS/exFAT
/dev/sda3       350879742 733499391 382619650 182.5G  f W95 Ext'd (LBA)
/dev/sda4       733499392 976769023 243269632   116G  7 HPFS/NTFS/exFAT
/dev/sda5       490231808 733499391 243267584   116G  7 HPFS/NTFS/exFAT
/dev/sda6       350879744 351930367   1050624   513M  b W95 FAT32
/dev/sda7       351932416 490223615 138291200    66G 83 Linux

Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.


---------- Disk/Partition Information From 'lsblk':
NAME     SIZE FSTYPE   LABEL      MOUNTPOINT                    MODEL
sda    465.8G                                                   TOSHIBA_MQ01ABD050V
|-sda1 115.8G ntfs                                              
|-sda2  51.6G ntfs     New Volume                               
|-sda3     1K                                                   
|-sda4   116G ntfs     New Volume                               
|-sda5   116G ntfs     New Volume                               
|-sda6   513M vfat                /boot/efi                     
`-sda7    66G ext4                /                             
   ------- 'lsblk' information continued ...
NAME   HOTPLUG PARTUUID                             UUID
sda          0                                      
|-sda1       0 397d34dc-01                          309A4AEF9A4AB160
|-sda2       0 397d34dc-02                          3E649FE2649F9B6B
|-sda3       0 397d34dc-03                          
|-sda4       0 397d34dc-04                          2052ECA452EC7FC0
|-sda5       0 397d34dc-05                          62B60241B60215E7
|-sda6       0 397d34dc-06                          A20C-1EE6
`-sda7       0 397d34dc-07                          69bc7ccc-3659-40eb-8ab1-a07fc65bcac6

---------- Mount Details of '/etc/fstab':
UUID=69bc7ccc-3659-40eb-8ab1-a07fc65bcac6 /               ext4    errors=remount-ro 0       1
UUID=A20C-1EE6  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

---------- Current Mount Details of 'mount':
/dev/fuse on /run/user/1000/doc type fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda6 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda7 on / type ext4 (rw,relatime,errors=remount-ro)

---------- USB Information from 'lsusb -t -v':
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
        |__ Port 2: Dev 3, If 0, Class=Audio, Driver=snd-usb-audio, 12M
            ID 8086:0808 Intel Corp. 
        |__ Port 2: Dev 3, If 1, Class=Audio, Driver=snd-usb-audio, 12M
            ID 8086:0808 Intel Corp. 
        |__ Port 2: Dev 3, If 2, Class=Audio, Driver=snd-usb-audio, 12M
            ID 8086:0808 Intel Corp. 
        |__ Port 2: Dev 3, If 3, Class=Human Interface Device, Driver=usbhid, 12M
            ID 8086:0808 Intel Corp. 
        |__ Port 4: Dev 4, If 1, Class=Video, Driver=uvcvideo, 480M
            ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam
        |__ Port 4: Dev 4, If 0, Class=Video, Driver=uvcvideo, 480M
            ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam
        |__ Port 6: Dev 5, If 2, Class=Vendor Specific Class, Driver=, 12M
            ID 03f0:231d HP, Inc Broadcom 2070 Bluetooth Combo
        |__ Port 6: Dev 5, If 0, Class=Wireless, Driver=btusb, 12M
            ID 03f0:231d HP, Inc Broadcom 2070 Bluetooth Combo
        |__ Port 6: Dev 5, If 3, Class=Application Specific Interface, Driver=, 12M
            ID 03f0:231d HP, Inc Broadcom 2070 Bluetooth Combo
        |__ Port 6: Dev 5, If 1, Class=Wireless, Driver=btusb, 12M
            ID 03f0:231d HP, Inc Broadcom 2070 Bluetooth Combo
        |__ Port 8: Dev 6, If 0, Class=Chip/SmartCard, Driver=, 12M
            ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
        |__ Port 1: Dev 3, If 0, Class=Vendor Specific Class, Driver=, 12M
            ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
        |__ Port 2: Dev 4, If 3, Class=Communications, Driver=cdc_acm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 1, Class=Communications, Driver=cdc_acm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 8, Class=Communications, Driver=cdc_wdm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 10, Class=CDC Data, Driver=cdc_acm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 6, Class=Communications, Driver=cdc_ncm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 4, Class=CDC Data, Driver=cdc_acm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 2, Class=CDC Data, Driver=cdc_acm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 0, Class=Communications, Driver=, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 9, Class=Communications, Driver=cdc_acm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 7, Class=CDC Data, Driver=cdc_ncm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband
        |__ Port 2: Dev 4, If 5, Class=Communications, Driver=cdc_wdm, 480M
            ID 03f0:3a1d HP, Inc hs2340 HSPA+ mobile broadband

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: 
           irq:34 
           memory:d4000000-d43fffff 
           memory:c0000000-cfffffff 
           ioport:4000(size=64) 
           memory:c0000-dffff

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 277mm x 156mm
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
The Current Session Type is: x11 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru'
The Current Virtual TTY's being used are:
    TTY#    Used By
    tty2    gdm-x-session
    tty2    Xorg
    tty2    gnome-session-b
    pts/0    bash
    pts/0    system-info
    pts/0    system-info
    pts/0    sed
    pts/0    system-info
    pts/0    ps
    pts/0    awk

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal main restricted
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal-updates main restricted
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal universe
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal-updates universe
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal multiverse
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal-updates multiverse
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal-backports main restricted universe multiverse
deb [trusted=yes] [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
deb-src [trusted=yes] [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal-security main restricted
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal-security universe
deb [trusted=yes] [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) focal-security multiverse
deb [arch=amd64] [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable main
deb-src [arch=amd64] [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable main

Sources List from SourcesD:
/etc/apt/sources.list.d/audio-recorder-ubuntu-ppa-focal.list:
deb [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) focal main
/etc/apt/sources.list.d/dart_stable.list.save:
deb [arch=amd64] [https://storage.googleapis.com/download.dartlang.org/linux/debian](https://storage.googleapis.com/download.dartlang.org/linux/debian) stable main
/etc/apt/sources.list.d/nrbrtx-ubuntu-xorg-hotkeys-focal.list:
File had no entries.
/etc/apt/sources.list.d/deadsnakes-ubuntu-ppa-focal.list.save:
deb [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) focal main
/etc/apt/sources.list.d/dartsim-ubuntu-ppa-focal.list.save:
deb [http://ppa.launchpad.net/dartsim/ppa/ubuntu](http://ppa.launchpad.net/dartsim/ppa/ubuntu) focal main
/etc/apt/sources.list.d/vscode.list.save:
deb [arch=amd64,arm64,armhf] [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable main
/etc/apt/sources.list.d/anydesk-stable.list.save:
deb [http://deb.anydesk.com/](http://deb.anydesk.com/) all main
/etc/apt/sources.list.d/dart_stable.list:
deb [arch=amd64] [https://storage.googleapis.com/download.dartlang.org/linux/debian](https://storage.googleapis.com/download.dartlang.org/linux/debian) stable main
/etc/apt/sources.list.d/nrbrtx-ubuntu-xorg-hotkeys-focal.list.save:
File had no entries.
/etc/apt/sources.list.d/vscode.list:
deb [arch=amd64,arm64,armhf] [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable main
/etc/apt/sources.list.d/deadsnakes-ubuntu-ppa-focal.list:
deb [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) focal main
/etc/apt/sources.list.d/google-chrome.list:
deb [arch=amd64] [https://dl.google.com/linux/chrome/deb/](https://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/dartsim-ubuntu-ppa-focal.list:
deb [http://ppa.launchpad.net/dartsim/ppa/ubuntu](http://ppa.launchpad.net/dartsim/ppa/ubuntu) focal main
/etc/apt/sources.list.d/anydesk-stable.list:
deb [http://deb.anydesk.com/](http://deb.anydesk.com/) all main
/etc/apt/sources.list.d/google-chrome.list.save:
deb [arch=amd64] [https://dl.google.com/linux/chrome/deb/](https://dl.google.com/linux/chrome/deb/) stable main

---------- Other Details from 'Various':
The current kernel version is:       5.15.0-41-generic 
The current release description is:  Ubuntu 20.04.4 LTS 
Original Installation Date:          2020-09-12+11:40:43 
Original Installation Media: Ubuntu 20.04.1 LTS "Focal Fossa" - Release amd64 (20200731)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.15.0.41.44
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

   --- HWE Package Status from 'dpkg':
Package linux-generic-hwe-20.04 is installed.

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

   --- User Installed Package List:
acpi-call-dkms
anydesk
build-essential
checkinstall
dart
deborphan
default-jre
ffmpeg
flatpak
gconf-service
gconf-service-backend
gconf2-common
google-chrome-stable
gufw
libappindicator1
libbz2-dev
libc++1
libc++1-10
libc++abi1-10
libc6-dev
libdbusmenu-gtk4
libffi-dev
libgconf-2-4
libgdbm-dev
libncursesw5-dev
libreadline-gplv2-dev
libsqlite3-dev
libssl-dev
lm-sensors
net-tools
packettracer
pastebinit
python3-pip
python3-pydrive
python3.10
synaptic
timeshift
tk-dev
tlp
tp-smapi-dkms
ubuntu-restricted-extras
vlc
youtube-dl
zlib1g-dev

Currently logged in User(s):
NAME     LINE         TIME             COMMENT
esso     :0           2022-07-24 16:59 (:0)

The User running this script was: esso
uid=1000(esso)
gid=1000(esso)
groups=1000(esso),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),
120(lpadmin),131(lxd),132(sambashare)

The 'system-info' script was booted from an installed system.

The 'system-info' script was run locally on the system

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=/boot/vmlinuz-5.15.0-41-generic root=UUID=69bc7ccc-3659-40eb-8ab1-a07fc65bcac6 ro quiet splash vt.handoff=7

---- Required Programs For Report.
    --- Some Programs This Script Uses Were Missing --- 
    mokutil

*** End Of Report ***
```

---

### Post by #&amp;thj^% on 2022-07-24
You miss-understood I meant Chrome, not the script we already have that. ;)
IE: "/usr/bin/google-chrome-stable %U"

---

### Post by esso10 on 2022-07-25
> **1fallen said:**
> You miss-understood I meant Chrome, not the script we already have that. ;)
IE: "/usr/bin/google-chrome-stable %U"

```
#!/bin/bash
#
# Copyright (c) 2011 The Chromium Authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.

# Let the wrapped binary know that it has been run through the wrapper.
export CHROME_WRAPPER="`readlink -f "$0"`"

HERE="`dirname "$CHROME_WRAPPER"`"

# We include some xdg utilities next to the binary, and we want to prefer them
# over the system versions when we know the system versions are very old. We
# detect whether the system xdg utilities are sufficiently new to be likely to
# work for us by looking for xdg-settings. If we find it, we leave $PATH alone,
# so that the system xdg utilities (including any distro patches) will be used.
if ! command -v xdg-settings &> /dev/null; then
  # Old xdg utilities. Prepend $HERE to $PATH to use ours instead.
  export PATH="$HERE:$PATH"
else
  # Use system xdg utilities. But first create mimeapps.list if it doesn't
  # exist; some systems have bugs in xdg-mime that make it fail without it.
  xdg_app_dir="${XDG_DATA_HOME:-$HOME/.local/share/applications}"
  mkdir -p "$xdg_app_dir"
  [ -f "$xdg_app_dir/mimeapps.list" ] || touch "$xdg_app_dir/mimeapps.list"
fi

# Always use our versions of ffmpeg libs.
# This also makes RPMs find the compatibly-named library symlinks.
if [[ -n "$LD_LIBRARY_PATH" ]]; then
  LD_LIBRARY_PATH="$HERE:$HERE/lib:$LD_LIBRARY_PATH"
else
  LD_LIBRARY_PATH="$HERE:$HERE/lib"
fi
export LD_LIBRARY_PATH

export CHROME_VERSION_EXTRA="stable"

# We don't want bug-buddy intercepting our crashes. [http://crbug.com/24120](http://crbug.com/24120)
export GNOME_DISABLE_CRASH_DIALOG=SET_BY_GOOGLE_CHROME

# Sanitize std{in,out,err} because they'll be shared with untrusted child
# processes ([http://crbug.com/376567](http://crbug.com/376567)).
exec < /dev/null
exec > >(exec cat)
exec 2> >(exec cat >&2)

# Note: exec -a below is a bashism.
exec -a "$0" "$HERE/chrome" "$@"
```

This one? :)

---

### Post by #&amp;thj^% on 2022-07-25
> **esso10 said:**
> ```
#!/bin/bash
#
# Copyright (c) 2011 The Chromium Authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.

# Let the wrapped binary know that it has been run through the wrapper.
export CHROME_WRAPPER="`readlink -f "$0"`"

HERE="`dirname "$CHROME_WRAPPER"`"

# We include some xdg utilities next to the binary, and we want to prefer them
# over the system versions when we know the system versions are very old. We
# detect whether the system xdg utilities are sufficiently new to be likely to
# work for us by looking for xdg-settings. If we find it, we leave $PATH alone,
# so that the system xdg utilities (including any distro patches) will be used.
if ! command -v xdg-settings &> /dev/null; then
  # Old xdg utilities. Prepend $HERE to $PATH to use ours instead.
  export PATH="$HERE:$PATH"
else
  # Use system xdg utilities. But first create mimeapps.list if it doesn't
  # exist; some systems have bugs in xdg-mime that make it fail without it.
  xdg_app_dir="${XDG_DATA_HOME:-$HOME/.local/share/applications}"
  mkdir -p "$xdg_app_dir"
  [ -f "$xdg_app_dir/mimeapps.list" ] || touch "$xdg_app_dir/mimeapps.list"
fi

# Always use our versions of ffmpeg libs.
# This also makes RPMs find the compatibly-named library symlinks.
if [[ -n "$LD_LIBRARY_PATH" ]]; then
  LD_LIBRARY_PATH="$HERE:$HERE/lib:$LD_LIBRARY_PATH"
else
  LD_LIBRARY_PATH="$HERE:$HERE/lib"
fi
export LD_LIBRARY_PATH

export CHROME_VERSION_EXTRA="stable"

# We don't want bug-buddy intercepting our crashes. [http://crbug.com/24120](http://crbug.com/24120)
export GNOME_DISABLE_CRASH_DIALOG=SET_BY_GOOGLE_CHROME

# Sanitize std{in,out,err} because they'll be shared with untrusted child
# processes ([http://crbug.com/376567](http://crbug.com/376567)).
exec < /dev/null
exec > >(exec cat)
exec 2> >(exec cat >&2)

# Note: exec -a below is a bashism.
exec -a "$0" "$HERE/chrome" "$@"
```

This one? :)
See deadflowr's post below first
 but I need you run it while using the " live caption " option.
It may give a clue as to why yours partly works.
**Also please use Code Tags for the return from terminal output, See my signature "Code Tags"**
Thanks deadflowr ;)

---

### Post by deadflowr on 2022-07-25
> This one? 
[s]No.
The output from when you run the command
```
/usr/bin/google-chrome-stable %U
```
in the terminal.
Type that into the terminal as is, don't add anything.
It should generate output just like what 1fallen posted in post #9.[/s]

Nevermind, I think I might have misunderstood.

Or I am still misunderstanding.

---

### Post by esso10 on 2022-08-13
> **deadflowr said:**
> [s]No.
The output from when you run the command
```
/usr/bin/google-chrome-stable %U
```
in the terminal.
Type that into the terminal as is, don't add anything.
It should generate output just like what 1fallen posted in post #9.[/s]

Nevermind, I think I might have misunderstood.

Or I am still misunderstanding.


[HTML]libva error: /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so init failed

[/HTML]

---

### Post by esso10 on 2022-08-13
[HTML]file:///usr/bin/google-chrome-stable%20%25U[/HTML]

---

