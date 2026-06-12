---
title: "unable to burn wav to audio cd with k3b"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by djlyx on 2007-02-03
Hmm, 

Cant seem to burn an audio CD with K3B...

it throws this error:

System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
TSSTcorp DVD+-RW TS-H553A DE04 (/dev/scd0, /dev/sg1) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-10-386
/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Linux sg driver version: 3.5.33
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/sg1 exclusively (Device or resource busy)... retrying in 1 second.
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/sg1'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=16 -raw96r driveropts=burnfree -eject -useinfo -audio -shorttrack /tmp/kde-djlyx/k3b_audio_0_01.inf /tmp/kde-djlyx/k3b_audio_0_02.inf /tmp/kde-djlyx/k3b_audio_0_03.inf /tmp/kde-djlyx/k3b_audio_0_04.inf /tmp/kde-djlyx/k3b_audio_0_05.inf /tmp/kde-djlyx/k3b_audio_0_06.inf /tmp/kde-djlyx/k3b_audio_0_07.inf /tmp/kde-djlyx/k3b_audio_0_08.inf /tmp/kde-djlyx/k3b_audio_0_09.inf 



any guesses? :confused:

---

### Post by BjarneJ on 2007-02-04
This might help:

[http://ubuntuforums.org/showthread.php?t=217472](http://ubuntuforums.org/showthread.php?t=217472)

---

### Post by djlyx on 2007-02-06
I unistalled then reinstalled k3b, appears to work now

go fig

---

