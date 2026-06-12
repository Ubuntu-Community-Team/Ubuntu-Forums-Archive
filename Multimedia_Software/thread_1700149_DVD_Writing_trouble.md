---
title: "DVD Writing trouble"
date: 2011-03-04
forum: Multimedia Software
---

### Post by macky66 on 2011-03-04
Hello,

I'm opening this thread to find a solution on a DVD burning problem.

Since few months, I decided to install Ubuntu on my PC after several years of Winzoz and now I am quite happy.
However, a DVD (both Video or Data disk with AVI files) created on Ubuntu using K3B, Nero Linux is read with errors by my DVD player, especially from the mid to the end of the movie. Some square blocks appears on screen and sometime the video freeze skipping some frames.
Using the same PC, the problem does not occur in Windows XP; I still kept the old windows partition on system disk.
I performed several tests, changing the writing speed (1x, 2x or 4x) but the result is
always the same.
Today, I've noticed that the colour of the written part on DVD changes from the inner (near the central hole) to the edge of support media. The written area becomes more lighter when it reach the middle. While a disk created on Windows appears with the same darker color from the inner to the edge.
Please find attached a photo showing a DVD created on Ubuntu

The problem exists with both DVD writers:
LG: HL-DT-ST GH22NS40
TSSTcorp SH-W162C

Ubuntu 10.10

Could you please help me to find a solution.

Thank-you


[IMG]file:///home/mac/Desktop/DVDPhoto.jpg[/IMG]

---

### Post by macky66 on 2011-03-07
Being the problem generalised and it does not seem related to HW issues,
could be helpful to re-install the low level software performing the writing?

Do you have any suggestion on that?

Thank-you in advance for any feedback

---

### Post by nomko on 2011-03-07
Start K3B using the terminal. Post the message you get when its started up.

 
And is is normal that burned areas differs in color then not burned area ;).

---

### Post by macky66 on 2011-03-07
Hello Nomko,
please find below the **Output of K3b :**
[FONT=Courier New]mac@macless:~$ k3b
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kbuildsycoca4 running...
QMetaObject::invokeMethod: No such method K3b::Application::loadCommandLineOptionsForNewInstance()
mac@macless:~$ k3b(2817)/kdeui (kdelibs): Attempt to use QAction "view_projects" with KXMLGUIFactory! 
k3b(2817)/kdeui (kdelibs): Attempt to use QAction "view_dir_tree" with KXMLGUIFactory! 
k3b(2817)/kdeui (kdelibs): Attempt to use QAction "view_contents" with KXMLGUIFactory! 
k3b(2817)/kdeui (kdelibs): Attempt to use QAction "location_bar" with KXMLGUIFactory! 
mac@macless:~$ QDBusObjectPath: invalid path ""
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
klauncher(2887)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2887)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2887)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2887)/kio (KLauncher): SlavePool: No communication with slave. 

klauncher(2887)/kio (KLauncher): SlavePool: No communication with slave. 

QLayout: Attempting to add QLayout "" to QFrame "", which already has a layout
K3bQProcess::QProcess(0x0)
mac@macless:~$ QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
params.c:OpenConfFile() - Unable to open configuration file "/home/mac/.smb/smb.conf":
    No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/mac/.smb/smb.conf.append":
    No such file or directory[/FONT]

---

### Post by macky66 on 2011-03-07
For sake of completeness, please find attached the Debug output from K3B dialog window

Devices
-----------------------
HL-DT-ST DVDRAM GH22NS40 NL02 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]
TSSTcorp CD/DVDW SH-W162C TS10 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.1 (KDE 4.5.1)
QT Version:  4.7.0
Kernel:      2.6.35-27-generic-pae

Used versions
-----------------------
cdrecord: 1.1.10

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GH22NS40 '
Revision       : 'NL02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1114112 = 1088 KB
Drive DMA Speed: 17295 kB/s 98x CD 12x DVD
FIFO size      : 12582912 = 12288 KB
Speed set to 5540 KB/s
Track 01: data  2667 MB        
Total size:     3063 MB (303:29.70) = 1365728 sectors
Lout start:     3063 MB (303:31/53) = 1365728 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 932768
Starting to write CD/DVD at speed   4.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Track 01:    0 of 2667 MB written.
Track 01:    1 of 2667 MB written (fifo  99%) [buf  99%]   0.0x.
Track 01:    2 of 2667 MB written (fifo  99%) [buf  99%]   4.1x.
Track 01:    3 of 2667 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:    4 of 2667 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:    5 of 2667 MB written (fifo 100%) [buf  99%]   4.2x.
Track 01:    6 of 2667 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:    7 of 2667 MB written (fifo  99%) [buf  99%]   4.2x.
Track 01:    8 of 2667 MB written (fifo 100%) [buf  99%]   4.1x.
Track 01:    9 of 2667 MB written (fifo  99%) [buf  99%]   4.2x.
Track 01:   10 of 2667 MB written (fifo 100%) [buf  98%]   4.1x.
Track 01:   11 of 2667 MB written (fifo  99%) [buf  98%]   4.2x.
Track 01:   12 of 2667 MB written (fifo  99%) [buf  98%]   4.1x.
Track 01:   13 of 2667 MB written (fifo 100%) [buf  98%]   4.2x.
Track 01:   14 of 2667 MB written (fifo  99%) [buf  98%]   4.1x.
Track 01:   15 of 2667 MB written (fifo 100%) [buf  98%]   4.2x.
Track 01:   16 of 2667 MB written (fifo 100%) [buf  98%]   4.1x.
[... snip ...]
Track 01: 2661 of 2667 MB written (fifo 100%) [buf  97%]   4.0x.
Track 01: 2662 of 2667 MB written (fifo 100%) [buf  97%]   4.2x.
Track 01: 2663 of 2667 MB written (fifo 100%) [buf  97%]   4.0x.
Track 01: 2664 of 2667 MB written (fifo 100%) [buf  97%]   4.1x.
Track 01: 2665 of 2667 MB written (fifo 100%) [buf 100%]   4.1x.
Track 01: 2666 of 2667 MB written (fifo 100%) [buf 100%]   4.1x.
Track 01: 2667 of 2667 MB written (fifo 100%) [buf  99%]   4.0x.
Track 01: Total bytes read/written: 2797010944/2797010944 (1365728 sectors).
Writing  time:  531.315s
Average write speed   3.8x.
Min drive buffer fill was 94%
Fixating...
Fixating time:   30.167s
/usr/bin/wodim: fifo had 44056 puts and 44056 gets.
/usr/bin/wodim: fifo was 0 times empty and 23539 times full, min fill was 95%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -data -tsize=1365728s -

---

### Post by macky66 on 2011-03-10
I performed again a test under Windows XP and the created DVD is also read with errors !!

The problem was the DVD burner that it does not work well.
I'm going to buy a new one ...

I apologise for wasting your time.

---

### Post by nomko on 2011-03-11
> **macky66 said:**
> I performed again a test under Windows XP and the created DVD is also read with errors !!
 
The problem was the DVD burner that it does not work well.
I'm going to buy a new one ...
 
I apologise for wasting your time.
 
Heee...you wasted nobodies time! So don't apologize for that.

---

### Post by nathan58 on 2011-03-18
I am using windows vista with Nero burnLite 6.0 for disk burning.....you can also follow same software.    :D

---

