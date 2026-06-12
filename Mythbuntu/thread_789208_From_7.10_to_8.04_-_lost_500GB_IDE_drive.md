---
title: "From 7.10 to 8.04 - lost 500GB IDE drive"
date: 2008-05-10
forum: Mythbuntu
---

### Post by freymann on 2008-05-10
I decided I would upgrade my mythbuntu 7.10 to 8.04 today. I'm just working on the main fe/be.

I was surprised by the upgrade process. When it asked me about remotes all I saw in the drop down was None or Custom, so selected none. After it rebooted I had to go into the Mythbuntu Control Center and select my remote there (and so far I haven't selected a transmitter? that looks like a new option).

I also had to re-enable VNC and the Medibuntu Proprietary Codec Support, which I had enabled in 7.10

My drives seems a little out whack though.

I have a 250GB Sata Drive which holds the OS and recordings dir, and another 500GB IDE drive that holds my other content (movies, photos, music).

The sata drive was /dev/sda1 (root dir) and /dev/sda5 (swap).

The IDE drive was /dev/hda1 (/nas)

As near as I can tell from dmesg, the IDE drive is being detected as /dev/sdb1 but when I update /etc/fstab and reboot it complains about the drive and drops me into a shell, where I can press CTRL-D to carry on, which it does, but no /nas drive exists anymore.

Was there a change in devices with 8.04? How do I get my drive back in action?

---

### Post by freymann on 2008-05-10
Here's the relevent sections from dmesg about the drives. I'm curious as to what this means as well:

 Driver 'sd' needs updating - please use bus_type methods
 sda:<4>Driver 'sr' needs updating - please use bus_type methods


```

[   19.497971] scsi0 : sata_nv
[   19.498089] scsi1 : sata_nv
[   19.498257] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 19
[   19.498260] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 19
[   19.865233] usb 2-7: new full speed USB device using ohci_hcd and address 2
[   19.965147] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.973413] ata1.00: ATA-7: ST3250310AS, 3.AAB, max UDMA/133
[   19.973418] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   19.989392] ata1.00: configured for UDMA/133
[   20.080144] usb 2-7: configuration #1 chosen from 1 choice
[   20.456670] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.620658] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-S183L, SB02, max UDMA/33
[   20.620661] ata2.00: applying bridge limits
[   20.792504] ata2.00: configured for UDMA/33
[   20.792611] scsi 0:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[   20.793526] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S183L SB02 PQ: 0 ANSI: 5
[   20.793616] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[   20.793655] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   20.793703] scsi2 : sata_nv
[   20.793752] scsi3 : sata_nv
[   20.793918] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 16
[   20.793922] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 16
[   21.104018] ata3: SATA link down (SStatus 0 SControl 300)
[   21.423694] ata4: SATA link down (SStatus 0 SControl 300)
[   21.433956] pata_amd 0000:00:0d.0: version 0.3.10
[   21.433993] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   21.434524] scsi4 : pata_amd
[   21.434576] scsi5 : pata_amd
[   21.435197] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[   21.435200] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[   21.444989] Driver 'sd' needs updating - please use bus_type methods
[   21.445065] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   21.445081] sd 0:0:0:0: [sda] Write Protect is off
[   21.445084] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.445108] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.445159] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   21.445173] sd 0:0:0:0: [sda] Write Protect is off
[   21.445176] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.445199] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.445202]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   21.466983]  sda1 sda2 < sda5 >
[   21.487828] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.492991] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.493012] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   21.501055] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.501059] Uniform CD-ROM driver Revision: 3.20
[   21.501106] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   21.639745] ata5.00: ATA-7: ST3500641A, 3.AAE, max UDMA/100
[   21.639750] ata5.00: 976773168 sectors, multi 16: LBA48 
[   21.648900] Attempting manual resume
[   21.648903] swsusp: Resume From Partition 8:5
[   21.648905] PM: Checking swsusp image.
[   21.649035] PM: Resume from disk failed.
[   21.677874] kjournald starting.  Commit interval 5 seconds
[   21.677887] EXT3-fs: mounted filesystem with ordered data mode.
[   21.731195] ata5.00: configured for UDMA/100
[   21.731236] ata6: port disabled. ignoring.
[   21.731348] scsi 4:0:0:0: Direct-Access     ATA      ST3500641A       3.AA PQ: 0 ANSI: 5
[   21.731438] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   21.731454] sd 4:0:0:0: [sdb] Write Protect is off
[   21.731457] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   21.731481] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.731532] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   21.731546] sd 4:0:0:0: [sdb] Write Protect is off
[   21.731549] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   21.731572] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.731576]  sdb:<3>ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.195945] ata5.00: BMDMA stat 0x64
[   22.195954] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   22.195956]          res 51/84:00:bf:03:48/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
[   22.195960] ata5.00: status: { DRDY ERR }
[   22.195963] ata5.00: error: { ICRC ABRT }
[   22.195997] ata5: soft resetting link
[   22.471060] ata5.00: configured for UDMA/100
[   22.471071] ata5: EH complete
[   22.935910] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   22.935916] ata5.00: BMDMA stat 0x64
[   22.935923] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   22.935925]          res 51/84:00:bf:03:48/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
[   22.935929] ata5.00: status: { DRDY ERR }
[   22.935932] ata5.00: error: { ICRC ABRT }
[   22.935963] ata5: soft resetting link
[   23.227666] ata5.00: configured for UDMA/100
[   23.227675] ata5: EH complete
[   23.692486] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   23.692492] ata5.00: BMDMA stat 0x64
[   23.692500] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   23.692502]          res 51/84:00:bf:03:48/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
[   23.692506] ata5.00: status: { DRDY ERR }
[   23.692508] ata5.00: error: { ICRC ABRT }
[   23.692544] ata5: soft resetting link
[   23.975948] ata5.00: configured for UDMA/100
[   23.975961] ata5: EH complete
[   24.440750] ata5.00: limiting speed to UDMA/66:PIO4
[   24.440757] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   24.440761] ata5.00: BMDMA stat 0x64
[   24.440769] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   24.440771]          res 51/84:00:bf:03:48/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
[   24.440774] ata5.00: status: { DRDY ERR }
[   24.440777] ata5.00: error: { ICRC ABRT }
[   24.440811] ata5: soft resetting link
[   24.732504] ata5.00: configured for UDMA/66
[   24.732518] ata5: EH complete
[   25.197327] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   25.197331] ata5.00: BMDMA stat 0x64
[   25.197337] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   25.197339]          res 51/84:00:bf:03:48/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
[   25.197342] ata5.00: status: { DRDY ERR }
[   25.197344] ata5.00: error: { ICRC ABRT }
[   25.197371] ata5: soft resetting link
[   25.480755] ata5.00: configured for UDMA/66
[   25.480771] ata5: EH complete
[   25.945597] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   25.945602] ata5.00: BMDMA stat 0x64
[   25.945609] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   25.945610]          res 51/84:00:bf:03:48/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
[   25.945614] ata5.00: status: { DRDY ERR }
[   25.945616] ata5.00: error: { ICRC ABRT }
[   25.945643] ata5: soft resetting link
[   26.229054] ata5.00: configured for UDMA/66
[   26.229068] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   26.229072] sd 4:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   26.229078] Descriptor sense data with sense descriptors (in hex):
[   26.229080]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   26.229090]         02 48 03 bf 
[   26.229095] sd 4:0:0:0: [sdb] Add. Sense: Scsi parity error
[   26.229100] end_request: I/O error, dev sdb, sector 0
[   26.229104] Buffer I/O error on device sdb, logical block 0
[   26.229118] ata5: EH complete
[   26.693874] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   26.693879] ata5.00: BMDMA stat 0x64
[   26.693885] ata5.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[   26.693887]          res 51/84:00:bf:03:48/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
[   26.693890] ata5.00: status: { DRDY ERR }
[   26.693892] ata5.00: error: { ICRC ABRT }
[   26.693919] ata5: soft resetting link
[   26.939658] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   26.985629] ata5.00: configured for UDMA/66
[   26.985641] ata5: EH complete

```

---

### Post by Dewey_Oxberger on 2008-05-10
This might be related to this (read into the second page for the fix):

[http://ubuntuforums.org/showthread.php?t=772485](http://ubuntuforums.org/showthread.php?t=772485)

---

### Post by freymann on 2008-05-10
That thread is interesting.

I am using the UUID's on the two sata partitions. Even correcting /etc/fstab to use /etc/sdb1 doesn't seem to bring the 500 GB IDE drive back though.

So I was going to change that to the UUID of the drive, but now I can't remember how you get the UUID for a drive??

---

### Post by freymann on 2008-05-10
Here's the results of

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35cb95f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9fdc9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29645   238123431   83  Linux
/dev/sdb2           29646       30401     6072570    5  Extended
/dev/sdb5           29646       30401     6072538+  82  Linux swap / Solaris

 I take that to mean that sda1 is my 500GB IDE drive. It uses EXT3. sdb is my 250GB Sata drive...

 So I simply edited /etc/fstab to read:

# media drive 500GB
/dev/sda1	/nas 	ext3 	defaults 	0 	1

 and it crashes during a reboot with:

Log of fsck -C3 -R -A -a 
Sat May 10 14:26:23 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: No such file or directory while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat May 10 14:26:23 2008

 What do I do to get this previously working /dev/hda1 drive back in action?

---

### Post by freymann on 2008-05-10
So now that I know that 

/etc/sda = 500GB IDE Drive (data only)

/etc/sdb = 250GB SATA Drive with OS

should /boot/grub/device.map contain this?

(hd0)	/dev/sda

I would think it should be /dev/sdb now?

---

