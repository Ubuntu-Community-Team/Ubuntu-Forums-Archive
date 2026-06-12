---
title: "Choppy DVD playback and slow disc burning"
date: 2009-08-19
forum: Multimedia Software
---

### Post by psychobot on 2009-08-19
I'm having issues with DVD playback and disc burning in Jaunty. Burning with Brasero is very slow and DVD playback is choppy. I'm wondering if it could be because DMA is not enabled and if so, how do I enable it? The output of dmsg | grep ata is:


$ dmesg | grep ata
[    0.000000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]  modified: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.004000] Memory: 2025736k/2096768k available (4760k kernel code, 452k absent, 70036k reserved, 2540k data, 536k init)
[    0.416342] libata version 3.00 loaded.
[    1.510278] ata1: SATA max UDMA/133 abar m1024@0xd7cffc00 port 0xd7cffd00 irq 2299
[    1.510280] ata2: SATA max UDMA/133 abar m1024@0xd7cffc00 port 0xd7cffd80 irq 2299
[    1.510283] ata3: SATA max UDMA/133 abar m1024@0xd7cffc00 port 0xd7cffe00 irq 2299
[    1.510285] ata4: SATA max UDMA/133 abar m1024@0xd7cffc00 port 0xd7cffe80 irq 2299
[    1.992027] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.992020] ata1.00: qc timeout (cmd 0xec)
[    6.992027] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[    7.476030] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    7.482143] ata1.00: ATA-8: WDC WD3000GLFS-01F8U0, 03.03V01, max UDMA/133
[    7.482145] ata1.00: 586072368 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    7.488186] ata1.00: configured for UDMA/133
[    8.392022] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.392465] ata2.00: ATA-7: WDC WD800JD-00LSA0, 06.01D06, max UDMA/133
[    8.392467] ata2.00: 156301488 sectors, multi 16: LBA48 
[    8.393012] ata2.00: configured for UDMA/133
[    8.728027] ata3: SATA link down (SStatus 0 SControl 300)
[    9.064026] ata4: SATA link down (SStatus 0 SControl 300)
[    9.117186] sata_sil24 0000:03:00.0: version 1.1
[    9.117200] sata_sil24 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.117269] sata_sil24 0000:03:00.0: setting latency timer to 64
[    9.117461] scsi4 : sata_sil24
[    9.117527] scsi5 : sata_sil24
[    9.117552] ata5: SATA max UDMA/100 host m128@0xd7fffc00 port 0xd7ff8000 irq 17
[    9.117556] ata6: SATA max UDMA/100 host m128@0xd7fffc00 port 0xd7ffa000 irq 17
[   11.196033] ata5: SATA link down (SStatus 0 SControl 0)
[   13.276033] ata6: SATA link down (SStatus 0 SControl 0)
[   13.276126] pata_ali 0000:00:1f.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.276272] scsi6 : pata_ali
[   13.276350] scsi7 : pata_ali
[   13.278224] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   13.278226] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   13.448407] ata7.00: ATAPI: ASUS    DVD-E616A2, 1.03, max UDMA/100
[   13.448419] ata7.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[   13.448421] ata7.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[   13.448429] ata7.01: ATAPI: ASUS    DRW-1608P3S, 1.24, max UDMA/66
[   13.448441] ata7.01: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[   13.448442] ata7.01: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[   13.464361] ata7.00: configured for UDMA/100
[   13.480402] ata7.01: configured for UDMA/66
[   13.919236] Write protecting the kernel read-only data: 6708k
[   14.767016] EXT4-fs: mounted filesystem with ordered data mode.
[   18.855006] EXT3-fs: mounted filesystem with ordered data mode.



Any ideas of what my problem could be? thanks

---

### Post by psychobot on 2009-08-20
bump

---

### Post by Jiawen on 2009-08-20
Does [this bug]("https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/15424") sound similar? I'm having problems with that bug, but I don't know enough to tell if it's what you're having problems with.

---

### Post by psychobot on 2009-08-20
Solved by enabling DMA. DVD playback works flawlessly, even under compiz effects. Disc burning, cd-r, is over twice as fast as it was before. After tireless research, I found that many users were having problems enabling DMA in Jaunty. What I did to enable it was simply add 'pata_ali.atapi_dma=1' to the kernel boot parameters. How I did it:

type [COLOR="Red"]gksudo gedit /boot/grub/menu.lst[/COLOR] in terminal. 
enter password
add [COLOR="Red"]pata_ali.atapi_dma=1[/COLOR] to the boot parameter of the kernel you want to enable DMA. 

I hope this helps whoever has the same problem.

---

