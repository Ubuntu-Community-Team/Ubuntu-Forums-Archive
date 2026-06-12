---
title: "cant play dvds without getting choppy audio and video that you cant understand"
date: 2014-12-25
forum: Multimedia Software
---

### Post by afrohippie82 on 2014-12-25
I'm trying to find a way to play dvd's for personal use that will allow me to play them without getting choppy audio and visual playback I've installed ubuntu unrestricted extraxas libdvdccs, nav4, and read 4 I also looked at this[  Page]("http://ubuntuforums.org/showthread.php?t=956779&highlight=playing+dvd%27s+sound+picture+choppy") but can't find the answer to my question any help would be greatly appreciated......

---

### Post by carl4926 on 2014-12-25
Probably you should tell us about your GPU

---

### Post by afrohippie82 on 2014-12-25
amd rv515 Radeon X1300 256 mb video card

---

### Post by carl4926 on 2014-12-26
Please check
[http://ubuntuforums.org/showthread.php?t=2204440](http://ubuntuforums.org/showthread.php?t=2204440)

---

### Post by Yellow Pasque on 2014-12-26
> **afrohippie82 said:**
> amd rv515 Radeon X1300 256 mb video card

In that case, you should tell us about your CPU, because you're not getting decoding help from an X1300 :(

---

### Post by afrohippie82 on 2014-12-26
CPU amd semperon 3200+ 939 chipset

---

### Post by afrohippie82 on 2014-12-26
I was looking @ the[ post]("http://ubuntuforums.org/showthread.php?t=2204440") that [**[COLOR=#DD4814][B]carl4926**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=809261") posted for me thank you [**[COLOR=#DD4814][B]carl4926**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=809261") I have been looking for a post like this for a long time and you just find it with ease not fair lol.... Looking at the post and a entry that a  member posted I found a difference between their working system and my not so dvd working  system again i don't know exactly what these numbers mean but I’m trying to learn. FYI Youtube works fine with my system.

This is the Code that Member [**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508")  wrote, the difference between the two systems will be highlighted

```
sysop@1310mini:~$ lspci -nnk | grep -iA3 vga
[COLOR=#ff0000]06:00.0[/COLOR] VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
        Kernel driver in use: radeon
[COLOR=#ff0000]06:00.1[/COLOR] Display controller [0380]: Advanced Micro Devices, Inc.  [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
sysop@1310mini:~$                       
```

My Code:
```
lspci -nnk | grep -iA3 vga
[COLOR=#ff0000]01:00.0[/COLOR] VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
        Kernel driver in use: radeon
[COLOR=#ff0000]01:00.1[/COLOR] Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]

```
I'm guessing this is the version of the display controller?

---

### Post by Yellow Pasque on 2014-12-26
> I'm guessing this is the version of the display controller? 
The numbers you highlight are PCI bus numbers (nothing to be concerned with).

> FYI Youtube works fine with my system.
That's funny, because I would guess your CPU is crippling video playback, but Flash tends to take a lot more CPU than playing a local video file.

What video player are you using? Have you tried different ones?

---

### Post by carl4926 on 2014-12-26
> **afrohippie82 said:**
> I'm trying to find a way to play dvd's for personal use that will allow me to play them without getting choppy audio and visual playback I've installed ubuntu unrestricted extraxas libdvdccs, nav4, and read 4 I also looked at this[  Page]("http://ubuntuforums.org/showthread.php?t=956779&highlight=playing+dvd%27s+sound+picture+choppy") but can't find the answer to my question any help would be greatly appreciated......

If you make an .iso of the DVD and open the .iso with VLC
How is playback

---

### Post by afrohippie82 on 2014-12-26
@[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") ived tried vlc and video player @[**[COLOR=#DD4814][B]carl4926**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=809261") i'll try that in a few and get back with you.

---

### Post by afrohippie82 on 2014-12-26
> **Temüjin said:**
> The numbers you highlight are PCI bus numbers (nothing to be concerned with).


That's funny, because I would guess your CPU is crippling video playback, but Flash tends to take a lot more CPU than playing a local video file.

What video player are you using? Have you tried different ones?

After closely examining youtube the sound is before or after the picture but the picture and sound is smooth just not together.

---

### Post by afrohippie82 on 2014-12-27
Just upgraded to the athlon 64 x2 4800+highest in the 939 chipset and 4GB of Ram and this machine is screaming fast compared to what is was but dvd play back is still choppy but a whole lot better youtube is now marching in order and working  correctly now lets see if we can get this choppiness taken care of.....

---

### Post by Yellow Pasque on 2014-12-27
Well, maybe the CD drive is at fault. Let's start with basic info: (rememebr to use code tags)
```
sudo apt-get install libcdio-utils
cd-drive
dmesg | grep -i ata
```

---

### Post by afrohippie82 on 2014-12-27
> **Temüjin said:**
> Well, maybe the CD drive is at fault. Let's start with basic info: (rememebr to use code tags)
```
sudo apt-get install libcdio-utils
cd-drive
dmesg | grep -i ata
```

[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") Here is the basic info. should I remove the dkms with autoremove?

                        ```

sudo apt-get install libcdio-utils

Reading package lists... Done

 Building dependency tree        

 Reading state information... Done
 The following package was automatically installed and is no longer required:
   dkms

 Use 'apt-get autoremove' to remove it.
 The following NEW packages will be installed:
   libcdio-utils
 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
 Need to get 66.7 kB of archives.
 After this operation, 395 kB of additional disk space will be used.
 Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libcdio-utils i386 0.83-4.1ubuntu1 [66.7 kB]
 Fetched 66.7 kB in 0s (88.3 kB/s)       
 debconf: unable to initialize frontend: Dialog
 debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
 debconf: falling back to frontend: Readline
 Selecting previously unselected package libcdio-utils.
 (Reading database ... 241263 files and directories currently installed.)
 Preparing to unpack .../libcdio-utils_0.83-4.1ubuntu1_i386.deb ...
 Unpacking libcdio-utils (0.83-4.1ubuntu1) ...
 Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
 Setting up libcdio-utils (0.83-4.1ubuntu1) &#8230;
 


```


                        ```
cd-drive

 cd-drive version 0.83 i686-pc-linux-gnu
 Copyright (c) 2003, 2004, 2005, 2007, 2008, 2011 R. Bernstein
 This is free software; see the source for copying conditions.
 There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
 PARTICULAR PURPOSE.
 The driver selected is GNU/Linux
 The default device for this driver is /dev/cdrom
 

 Drivers available...
   GNU/Linux ioctl and MMC driver      
   cdrdao (TOC) disk image driver      
   bin/cuesheet disk image driver      
   Nero NRG disk image driver          
 

 CD-ROM drive supports MMC 3
 

                        Drive: /dev/cdrom
 Vendor                      : HL-DT-ST
 Model                       : DVDRRW GWA-4166B
 Revision                    : 1823
 Profile List Feature
         DVD+R Double Layer - DVD Recordable Double Layer
         DVD+R - DVD Recordable
         DVD+RW - DVD Rewritable
         Re-recordable DVD using Sequential Recording
         Re-recordable DVD using Restricted Overwrite
         Re-recordable DVD using Sequential recording
         Read only DVD - on
         CD-RW Re-writable Compact Disc capable
         Write once Compact Disc capable
 

 Core Feature
         ATAPI interface
 

 Morphing Feature
         Operational Change Request/Notification not supported
         Synchronous GET EVENT/STATUS NOTIFICATION supported
 

 Removable Medium Feature
         Tray type loading mechanism
         can eject the medium or magazine via the normal START/STOP command
         can be locked into the Logical Unit
 

 Write Protect Feature
 

 Random Readable Feature
 

 Multi-Read Feature
 

 CD Read Feature
         C2 Error pointers are not supported
         CD-Text is supported
 

 DVD Read Feature
 

 Random Writable Feature
 

 Incremental Streaming Writable Feature
 

 Formattable Feature
 

 Restricted Overwrite Feature
 

 DVD+RW Feature
 

 DVD+R Feature
 

 Rigid Restricted Overwrite Feature
 

 CD Track at Once Feature
 

 CD Mastering (Session at Once) Feature
 

 DVD-R/RW Write Feature
 

 DVD+R Double Layer Feature
 

 Initiator- and Device-directed Power Management Feature
 

 CD Audio External Play Feature
         SCAN command is not supported
         audio channels can not be muted separately
         audio channels can not have separate volume levels
         255 volume levels can be set
 

 Ability to respond to all commands within a specific time Feature
 

 Ability to perform DVD CSS/CPPM authentication via RPC Feature
         CSS version 1
 

 Ability to read and write using Initiator requested performance parameters Feature
 

 The Logical Unit Unique Identifier Feature
         &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
 

 Vendor-specific code a8e8 Feature
 

 Hardware                                  : CD-ROM or DVD
 Can eject                                 : Yes
 Can close tray                            : Yes
 Can disable manual eject                  : Yes
 Can select juke-box disc                  : No
 

 Can set drive speed                       : No
 Can read multiple sessions (e.g. PhotoCD) : Yes
 Can hard reset device                     : Yes
 

 Reading....
   Can read Mode 2 Form 1                  : Yes

   Can read Mode 2 Form 2                  : Yes
   Can read (S)VCD (i.e. Mode 2 Form 1/2)  : Yes
   Can read C2 Errors                      : No
   Can read IRSC                           : Yes
   Can read Media Channel Number (or UPC)  : Yes
   Can play audio                          : Yes
   Can read CD-DA                          : Yes
   Can read CD-R                           : Yes
   Can read CD-RW                          : Yes
   Can read DVD-ROM                        : Yes
 

 Writing....
   Can write CD-RW                         : Yes
   Can write DVD-R                         : Yes
   Can write DVD-RAM                       : No
   Can write DVD-RW                        : No
   Can write DVD+RW                        : No
 


```

```

   dmesg | grep -i ata

 [    0.000000] BIOS-e820: [mem 0x00000000cfef3000-0x00000000cfefffff] ACPI data
 [    0.000000] Memory: 4112936K/4192824K available (6546K kernel code, 640K rwdata, 2764K rodata, 876K init, 924K bss, 79888K reserved, 3279816K highmem)
 [    0.000000]       .data : 0xc1664ef4 - 0xc19ba3c0   (3413 kB)
 [    0.321296] libata version 3.00 loaded.
 [    1.652360] Write protecting the kernel read-only data: 2772k
 [    1.652362] NX-protecting the kernel data: 5740k
 [    1.720577] pata_atiixp 0000:00:14.1: PCI->APIC IRQ transform: INT A -> IRQ 17
 [    1.721489] scsi0 : pata_atiixp
 [    1.721569] scsi1 : pata_atiixp
 [    1.721613] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
 [    1.721615] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
 [    1.721657] sata_sil 0000:00:12.0: version 2.4
 [    1.721686] sata_sil 0000:00:12.0: can't find IRQ for PCI INT A; probably buggy MP table
 [    1.733141] scsi2 : sata_sil
 [    1.744546] scsi3 : sata_sil
 [    1.744577] ata3: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 11
 [    1.744581] ata4: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 11
 [    1.896735] ata2.00: ATAPI: HL-DT-STDVDRRW GWA-4166B, 1823, max UDMA/33
 [    1.896735] ata2.01: ATA-5: WDC WD400BB-60DGA0, 05.03E05, max UDMA/100
 [    1.896735] ata2.01: 78165360 sectors, multi 16: LBA  
 [    1.912718] ata2.00: configured for UDMA/33
 [    1.928579] ata2.01: configured for UDMA/100
 [    2.064136] ata3: SATA link down (SStatus 0 SControl 300)
 [    2.124663] ata1.00: ATA-6: ST380011A, 8.11, max UDMA/100
 [    2.124663] ata1.00: 156301488 sectors, multi 16: LBA  
 [    2.140578] ata1.00: configured for UDMA/100
 [    2.140582] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.11 PQ: 0 ANSI: 5
 [    2.152241] scsi 1:0:1:0: Direct-Access     ATA      WDC WD400BB-60DG 05.0 PQ: 0 ANSI: 5
 [    2.472160] ata4: SATA link down (SStatus 0 SControl 300)
 [    3.845766] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)


```

---

### Post by afrohippie82 on 2014-12-27
all of my drives are ide  should i have replace the code with  IDE
 ```
dmesg | grep -i ata
```


```
dmesg | grep -i ide
```

---

### Post by Yellow Pasque on 2014-12-27
No, I see the info I needed. ("PATA" is used interchangeably with "IDE" for a long time now).

Nothing jumps out at me, so I don't know what to tell you other than make sure you're using a high quality, 80-pin PATA cable and have the drives jumpered correctly. Also consider that there's a firmware update available  for the drive [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=us&lc=en&dlc=en&softwareitem=pv-37908-1](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=us&lc=en&dlc=en&softwareitem=pv-37908-1)

---

### Post by Yellow Pasque on 2014-12-27
I have a very similar system, though it's AM2 and it has a RadeonHD 4550 to give some video decode acceleration. It's still a very nice system that plays media in the home gym.

Since you upgraded the CPU and RAM, I would be on the lookout for cheap cards that will give you VDPAU capabilites like a Radeon HD4350/4550 or an Nvidia 8400GS, G210, etc. I don't think they'll be too hard to find since people buy systems with these kinds of cards and then find some game they want to play needs a video card upgrade.

---

### Post by afrohippie82 on 2014-12-28
> **Temüjin said:**
> No, I see the info I needed. ("PATA" is used interchangeably with "IDE" for a long time now).

Nothing jumps out at me, so I don't know what to tell you other than make sure you're using a high quality, 80-pin PATA cable and have the drives jumpered correctly. Also consider that there's a firmware update available  for the drive [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=us&lc=en&dlc=en&softwareitem=pv-37908-1](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?cc=us&lc=en&dlc=en&softwareitem=pv-37908-1)

I don't know if this question needs to be in another post or not but if so please let me know.  How do i run this firmware update  in the pastI've tried running the bios update for this motherboard that had the exe. file format on wine but it would not allow me to do it. any suggestions would be appreciated...

---

