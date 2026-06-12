---
title: "Terrible DVD performance"
date: 2008-12-03
forum: Multimedia Software
---

### Post by fieldstone on 2008-12-03
I had this problem before on Hardy with a custom-compiled 2.6.27 kernel, and I hoped it would be resolved in Intrepid. No luck, I guess.

I have a Compaq Presario V3000 series notebook with a SATA DVD-RW drive. When I'm using it for playing a video DVD or backing one up using k9copy, my system gets slow for doing anything else, even just browsing the web in Firefox. In addition, playing a video DVD results in jerky video... unwatchably jerky video.

This didn't happen under Hardy with the 2.6.24 kernel. If someone can help me figure out what might be causing it, I'd be eternally grateful.

---

### Post by fieldstone on 2008-12-03
An update - I don't have this problem with an external USB DVD-RW drive, only the internal SATA one.

---

### Post by incubii on 2008-12-03
Im just stabbing in the dark here, but sounds like the SATA drive has been put into PIO mode which is horribly slow and the USB drive is using DMA. You might want to google turning DMA on your SATA drive.

---

### Post by fieldstone on 2008-12-03
Good thought. I thought I read that the Linux kernel automatically assumes DMA for all Sata devices, though. Can someone confirm or deny this?

---

### Post by fieldstone on 2008-12-03
Based on some other posts I read, I ran "hdparm -i /dev/scd0" . The output was as follows:

/dev/scd0:

 Model=MATSHITAUJ-840D                         , FwRev=1.02    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 *mdma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6

 * signifies the current active mode


Running "dmesg | grep ata" yields the following:

[    0.000000]  BIOS-e820: 0000000077f00000 - 0000000077f17000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] Kernel command line: root=/dev/sda1 ro quiet splash rootflags=data=writeback combined_mode=libata
[    0.004000] Memory: 1931988k/1965056k available (2572k kernel code, 31808k reserved, 1160k data, 424k init, 1047552k highmem)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.644214] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[    2.399675] Write protecting the kernel read-only data: 936k
[    3.552647] libata version 3.00 loaded.
[    4.148375] pata_amd 0000:00:0d.0: version 0.3.10
[    4.148428] pata_amd 0000:00:0d.0: setting latency timer to 64
[    4.148550] scsi0 : pata_amd
[    4.148682] scsi1 : pata_amd
[    4.149671] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    4.149675] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    4.480473] ata2.00: ATAPI: MATSHITAUJ-840D, 1.02, max MWDMA2
[    4.480490] ata2: nv_mode_filter: 0x39f&0x7001->0x1, BIOS=0x0 (0x0) ACPI=0x7001 (60:600:0x11)
[    4.496485] ata2.00: configured for PIO0
[    5.079050] sata_nv 0000:00:0e.0: version 3.5
[    5.079064] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    5.079564] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 16 (level, high) -> IRQ 16
[    5.079568] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    5.079617] sata_nv 0000:00:0e.0: setting latency timer to 64
[    5.083557] scsi2 : sata_nv
[    5.083687] scsi3 : sata_nv
[    5.083915] ata3: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 16
[    5.083919] ata4: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 16
[    5.556071] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.564443] ata3.00: ATA-8: Hitachi HTS722020K9SA00, DC4OC54P, max UDMA/133
[    5.564447] ata3.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.581213] ata3.00: configured for UDMA/133
[    5.910604] ata4: SATA link down (SStatus 0 SControl 300)
[    6.258880] EXT3-fs: mounted filesystem with writeback data mode.
[   34.078548] NVRM : nv_acpi_nvif_method : NVIF data invalid. function d subFunction 0

---

### Post by alexserver on 2008-12-10
I have bad news for you:
I am writing from an Intrepid release on a Compa V3417LA, with Nvidia chipset as well as yours, and still there is this bug.
So as you said, this bug is present since hardy.
It might be solved with compiled kernel with old 2.6.24 modules , as i read, but o dont know how to do this.

---

