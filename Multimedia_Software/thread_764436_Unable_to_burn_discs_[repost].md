---
title: "Unable to burn discs [repost]"
date: 2008-04-23
forum: Multimedia Software
---

### Post by tjbk_tjb on 2008-04-23
I decided to repost this on the new board instead of bumping the orignal topic.
Info I did not include in the original post:
In the intervening time, I've found that other DVD burners work. Also of note is that this particular drive works fine in Windows XP.
> **tjbk_tjb said:**
> A while back, I bought a Plextor PX-608CU DVD burner to use with my laptop. Now, my internel Sony DRU-500A has failed, so I need a DVD burner and I just found out that I couldn't figure out how to get it to burn. When I try to burn anything, K3b announces that I don't have permission. All logs will be placed at the bottom. I've changed /dev/scd0's permissions to 777, but that doesn't help. I'm already in the cdrom group. It doesn't even work if I run it as root. In that case, it reports that a buffer underrun probably occurred.

I'm running Kubuntu Gutsy on an x64, but the problem can be repeated on an x86.

K3b Debugging Output
```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
SONY DVD RW DRU-500A 2.1a (/dev/hda, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite]

PLEXTOR DVDR    PX-608CU 1.00 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]
Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/X11/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'PLEXTOR '
Identification : 'DVDR    PX-608CU'
Revision       : '1.00'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0002 (Removable disk) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 4194304 = 4096 KB
pregap1: -1
Track 01: audio   36 MB (03:35.82) no preemp swab copy
Track 02: audio   45 MB (04:28.52) no preemp swab copy
Track 03: audio   49 MB (04:56.68) no preemp swab copy
Track 04: audio   44 MB (04:23.24) no preemp swab copy
Track 05: audio   46 MB (04:33.72) no preemp swab copy
Track 06: audio   45 MB (04:28.88) no preemp swab copy
Track 07: audio   41 MB (04:06.08) no preemp swab copy
Track 08: audio   43 MB (04:20.60) no preemp swab copy
Track 09: audio   59 MB (05:55.29) no preemp swab copy
Track 10: audio   42 MB (04:13.00) no preemp swab copy
Track 11: audio   37 MB (03:44.18) no preemp swab copy
Track 12: audio   46 MB (04:35.44) no preemp swab copy
Track 13: audio   43 MB (04:17.73) no preemp swab copy
Track 14: audio   42 MB (04:13.21) no preemp swab copy
Total size:      624 MB (61:52.41) = 278431 sectors
Lout start:      624 MB (61:54/31) = 278431 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
Speed set to 4233 KB/s
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 81415
Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   36 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 01 95 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 2C 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x00 (command sequence error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 0.003s timeout 200s
/usr/bin/X11/wodim: A write error occured.
/usr/bin/X11/wodim: Please properly read the error message above.
write track data: error after 952560 bytes
Writing  time:   18.117s
Average write speed 342.4x.
Fixating...
Fixating time:    0.010s
/usr/bin/X11/wodim: fifo had 79 puts and 16 gets.
/usr/bin/X11/wodim: fifo was 0 times empty and 2 times full, min fill was 87%.

cdrecord command:
-----------------------
/usr/bin/X11/wodim -v gracetime=2 dev=/dev/scd0 speed=24 -dao driveropts=burnfree fs=4m -overburn -useinfo -audio /home/tommy/tmp/kde-tommy/k3b_audio_0_01.inf 

```
```

$ dmesg |tail -n20
[  505.358123] usb 2-10: new high speed USB device using ehci_hcd and address 3
[  505.494136] usb 2-10: configuration #1 chosen from 1 choice
[  505.602321] usbcore: registered new interface driver libusual
[  505.653208] Initializing USB Mass Storage driver...
[  505.653385] scsi6 : SCSI emulation for USB Mass Storage devices
[  505.653490] usb-storage: device found at 3
[  505.653493] usb-storage: waiting for device to settle before scanning
[  505.653595] usbcore: registered new interface driver usb-storage
[  505.653655] USB Mass Storage support registered.
[  510.640217] usb-storage: device scan complete
[  510.644827] scsi 6:0:0:0: CD-ROM            PLEXTOR  DVDR    PX-608CU 1.00 PQ: 0 ANSI: 0
[  510.645227] scsi 6:0:0:0: Attached scsi generic sg1 type 5
[  510.934885] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[  510.935071] sr 6:0:0:0: Attached scsi CD-ROM sr0
[  549.564659] cdrom: This disc doesn't have any tracks I recognize!
[  652.867184] scsi: unknown opcode 0xe9
[  652.867283] scsi: unknown opcode 0xed
[  661.108736] scsi: unknown opcode 0xf5
[  679.138993] scsi: unknown opcode 0xeb
[  909.054995] usb 2-10: USB disconnect, address 3

```

---

### Post by tjbk_tjb on 2008-04-25
I'll just bump this thread. Hopefully, someone can help me.

---

### Post by feardotcom on 2008-04-29
dont worryyour not the only one...im having a sorta same problem....im just trying to copy files from my quake 4 cd and its telling me i dont have permissions to do so....

---

