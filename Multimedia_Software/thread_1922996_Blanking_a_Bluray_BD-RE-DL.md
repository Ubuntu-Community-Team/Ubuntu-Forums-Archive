---
title: "Blanking a Bluray BD-RE-DL"
date: 2012-02-09
forum: Multimedia Software
---

### Post by gbrowning on 2012-02-09
I am trying to get a good handle on how to manipulate rewritable material. As a test I wrote a 2GB iso file to a 50GB BD-DL-RE.  Then I tested the data, a movie, and tried to blank the disk.  Can you please point me to somewhere with a tutorial even an idiot can understand.  the error messages point to configuration information I know nothing about. Below are two of my attempts. see this....


[I]george@Ronin:~$ wodim -scanbus
scsibus2:
    2,0,0    200) 'PLEXTOR ' 'DVDR   PX-870A  ' '1.01' Removable CD-ROM
    2,1,0    201) *
    2,2,0    202) *
    2,3,0    203) *
    2,4,0    204) *
    2,5,0    205) *
    2,6,0    206) *
    2,7,0    207) *
scsibus11:
    11,0,0    1100) 'ASUS    ' 'BW-12B1ST       ' '1.03' Removable CD-ROM
    11,1,0    1101) *
    11,2,0    1102) *
    11,3,0    1103) *
    11,4,0    1104) *
    11,5,0    1105) *
    11,6,0    1106) *
    11,7,0    1107) *
george@Ronin:~$ wodim -v dev=/dev/dcrw -blank=fast
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/dcrw'
devname: '/dev/dcrw'
scsibus: -2 target: -2 lun: -2
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
george@Ronin:~$ wodim -v dev=/dev/11,0,0 -blank=fast
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
wodim: Invalid argument. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation[/I]

Other attempts return similar results.

[I]george@Ronin:~$ wodim -v dev=/dev/sg4 -blank=all
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sg4'
devname: '/dev/sg4'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.34
Wodim version: 1.1.11
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ASUS    '
Identification : 'BW-12B1ST       '
Revision       : '1.03'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0043 (BD-RE)
Profile: 0x0043 (BD-RE) (current)
Profile: 0x0042 (BD-R random recording) 
Profile: 0x0041 (BD-R sequential recording) 
Profile: 0x0040 (BD-ROM) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 5898240 = 5760 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Current Secsize: 2048
  ATIP start of lead in:  -150 (00:00/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Forcespeed is OFF.
Speed set to 8990 KB/s
Starting to write CD/DVD at speed  51.0 in real BLANK mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Performing OPC...
Blanking entire disk
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 9600s
wodim: Cannot blank disk, aborting.

Just a bit more progress.  Eliminated Illegal Operation Error by issuing SUDO command before.  Now the most important flag seems to be this 

Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 9600s
wodim: Cannot blank disk, aborting.


[/I]

---

### Post by wolfen69 on 2012-02-09
K3B now has support for Blu-ray and should be able to erase it, provided you don't mind using a gui app.

---

### Post by gbrowning on 2012-02-09
Thank you Wolfen.  K3B worked quickly and intuitively. 
   Without GUI I would be nearly useless. In this instance I just assumed the CLI would work better.  The parameters and how they fit into wodim put me off balance.  The problem with GUI is that I am lazy and will never learn something unless it is necessary for progress. Definitely not an artist.
    Again, thank you.

---

