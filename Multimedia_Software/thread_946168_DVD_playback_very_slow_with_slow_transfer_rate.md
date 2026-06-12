---
title: "DVD playback very slow with slow transfer rate"
date: 2008-10-13
forum: Multimedia Software
---

### Post by mnj1979 on 2008-10-13
Hello Everyone,
  My DVD playback is sluggish and choppy with low memory although it works well on other OS such as MAC Leopard. There is something about the DMA but I cant set DMA because my drive is /dev/scd0.
udo hdparm -i /dev/scd0

/dev/scd0:

 Model=MATSHITADVD-R   UJ-857D                 , FwRev=KBVB    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6

 * signifies the current active mode

 sudo hdparm /dev/scd0
[sudo] password for mark: 

/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
.. 
It appears I cant set hdparm on my scd0 drive.  What should I do to increase CD/DVD speed to normal?
~$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000007e2f9000 - 000000007eebe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007eeef000 - 000000007ef00000 (ACPI data)
[    0.000000] ACPI: SSDT 7EEBD000, 064F (r1 SataRe  SataPri     1000 INTL 20050309)
[    0.000000] ACPI: SSDT 7EEBC000, 069C (r1 SataRe  SataSec     1000 INTL 20050309)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[   37.705493] Memory: 2024112k/2065376k available (2489k kernel code, 40876k reserved, 1318k data, 320k init)
[   38.429926] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   39.496742] libata version 3.00 loaded.
[   39.497973] scsi0 : ata_generic
[   39.498037] scsi1 : ata_generic
[   39.498534] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[   39.498537] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[   39.815939] ata1.00: ATAPI: MATSHITADVD-R   UJ-857D, KBVB, max UDMA/66
[   39.815949] ata1.00: configured for PIO
[   39.984352] scsi2 : ata_generic
[   39.984414] scsi3 : ata_generic
[   39.985264] ata3: PATA max UDMA/100 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19
[   39.985267] ata4: PATA max UDMA/100 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19
[   40.167673] ata3.01: ATA-7: FUJITSU MHV2080BHPL, 00817030, max UDMA/100
[   40.167676] ata3.01: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   40.167687] ata3.01: configured for UDMA/100
[   42.901032] EXT3-fs: mounted filesystem with ordered data mode.
[   61.772085] appletouch: incomplete data package (first byte: 2, length: 4).
Thank you for your help and I hope this information is useful.

Regards,
Mark

---

