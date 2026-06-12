---
title: "k3b does not burn multisession / CD-Extra"
date: 2010-01-11
forum: Multimedia Software
---

### Post by Danstroem on 2010-01-11
Hello,

I have a problem while burning a CD-Extra (audio+data in two seperate sessions) in k3b 1.68.0~alpha3-0ub on Karmic. The audio tracks are being burned and the session is closed, but k3b does not start burning the second session. There is the last status message in the log: "Searching previous session" and one near the progress bar: "Closing session". Normally it should close the audio session, eject the burner for resetting his state and begin burning the second session. But in fact it just stops, instead of burning the second session. My only option is to cancel.

I already tried to add -eject into the user options of wodim/cdrecord. It ejects, but it didn't help. The first (audio-)session nevertheless is correctly burned, only the second (data-)session is missing. I tried to switch the writing app to cdrdao (option in k3b), but in this mode k3b dies with a segmentation fault. Only "auto" or "cdrecord" mode works. (In fact "auto" chooses cdrecord).

There doesn't seem to be a different version of k3b available in synaptic to try out. I switched over from gentoo, where k3b worked. Unfortunately I cannot remember the exact version of k3b in gentoo. The system was approx. 1 year old.

I have included the debugging output and the screenshot of k3b below.  Any hint greatly appreciated!


PS: Is there a native Gnome/GTK app that does CD-Extra? Brasero and GnomeBaker do not support it yet.

```

Devices
 -----------------------
 Optiarc DVD RW AD-7543A 1-00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]
  K3b::IsoImager
 -----------------------
 mkisofs print size result: 74835 (153262080 bytes)
  System
 -----------------------
 K3b Version: 1.68.0
 KDE Version: 4.3.2 (KDE 4.3.2)
 QT Version:  4.5.2
 Kernel:      2.6.31-16-generic
  Used versions
 -----------------------
 mkisofs: 1.1.9
 cdrecord: 1.1.9
  cdrecord
 -----------------------
 /usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
 devname: '/dev/sr0'
 scsibus: -2 target: -2 lun: -2
 Linux sg driver version: 3.5.27
 Wodim version: 1.1.9
 SCSI buffer size: 64512
 Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
 communication breaks or freezes immediately after that.
 Text len: 666
 TOC Type: 0 = CD-DA
 Driveropts: 'burnfree'
 Device type    : Removable CD-ROM
 Version        : 5
 Response Format: 2
 Capabilities   : 
 Vendor_info    : 'Optiarc '
 Identification : 'DVD RW AD-7543A '
 Revision       : '1-00'
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
 Profile: 0x0011 (DVD-R sequential recording) 
 Profile: 0x0010 (DVD-ROM) 
 Profile: 0x000A (CD-RW) 
 Profile: 0x0009 (CD-R) (current)
 Profile: 0x0008 (CD-ROM) (current)
 Profile: 0x0002 (Removable disk) 
 Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
 Driver flags   : MMC-3 SWABAUDIO BURNFREE 
 Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
 Drive buf size : 890880 = 870 KB
 FIFO size      : 12582912 = 12288 KB
 Speed set to 4234 KB/s
 pregap1: -1
 Track 01: audio   34 MB (03:26.85) no preemp swab copy
 Track 02: audio   46 MB (04:35.25) no preemp swab copy
 Track 03: audio   43 MB (04:18.57) no preemp swab copy
 Total size:      124 MB (12:20.68) = 55551 sectors
 Lout start:      124 MB (12:22/51) = 55551 sectors
 Current Secsize: 2048
 ATIP info from disk:
   Indicated writing power: 4
   Is not unrestricted
   Is not erasable
   Disk sub type: Medium Type A, low Beta category (A-) (2)
   ATIP start of lead in:  -12508 (97:15/17)
   ATIP start of lead out: 359845 (79:59/70)
 Disk type:    Short strategy type (Phthalocyanine or similar)
 Manuf. index: 22
 Manufacturer: Ritek Co.
 Blocks total: 359845 Blocks current: 359845 Blocks remaining: 304294
 Starting to write CD/DVD at speed  24.0 in real SAO mode for multi session.
 Last chance to quit, starting real write in    2 seconds.
    1 seconds.
    0 seconds. Operation starts.
 Waiting for reader process to fill input buffer ... input buffer ready.
 Performing OPC...
 Sending CUE sheet...
 SAO startsec: -12508
 Writing lead-in...
 Lead-in write time:   31.114s
 Writing pregap for track 1 at -150
 Starting new track at sector: 0
 Track 01:    0 of   34 MB written.
 Track 01:    1 of   34 MB written (fifo 100%) [buf 100%]  11.5x.
 Track 01:    2 of   34 MB written (fifo 100%) [buf 100%]   3.6x.
 Track 01:    3 of   34 MB written (fifo 100%) [buf 100%]   3.5x.

...

 Track 01:   31 of   34 MB written (fifo 100%) [buf 100%]  12.5x.
 Track 01:   32 of   34 MB written (fifo 100%) [buf 100%]   2.3x.
 Track 01:   33 of   34 MB written (fifo 100%) [buf 100%]  12.5x.
 Track 01:   34 of   34 MB written (fifo 100%) [buf 100%]  12.1x.
 Track 01: Total bytes read/written: 36488928/36488928 (15514 sectors).
 Starting new track at sector: 15514
 Track 02:    0 of   46 MB written.
 Track 02:    1 of   46 MB written (fifo 100%) [buf 100%]  12.6x.
 Track 02:    2 of   46 MB written (fifo 100%) [buf 100%]  12.5x.
 Track 02:    3 of   46 MB written (fifo 100%) [buf 100%]  12.9x.
 Track 02:    4 of   46 MB written (fifo 100%) [buf 100%]  12.5x.

...

 Track 02:   42 of   46 MB written (fifo 100%) [buf 100%]  13.2x.
 Track 02:   43 of   46 MB written (fifo 100%) [buf 100%]  13.6x.
 Track 02:   44 of   46 MB written (fifo 100%) [buf 100%]  14.1x.
 Track 02:   45 of   46 MB written (fifo 100%) [buf 100%]  13.6x.
 Track 02:   46 of   46 MB written (fifo 100%) [buf 100%]  14.0x.
 Track 02: Total bytes read/written: 48554688/48554688 (20644 sectors).
 Starting new track at sector: 36158
 Track 03:    0 of   43 MB written.
 Track 03:    1 of   43 MB written (fifo 100%) [buf 100%]  13.9x.
 Track 03:    2 of   43 MB written (fifo 100%) [buf 100%]  13.7x.
 Track 03:    3 of   43 MB written (fifo 100%) [buf 100%]  14.2x.

...

 Track 03:   40 of   43 MB written (fifo 100%) [buf 100%]  14.3x.
 Track 03:   41 of   43 MB written (fifo 100%) [buf 100%]  14.8x.
 Track 03:   42 of   43 MB written (fifo 100%) [buf 100%]  14.3x.
 Track 03:   43 of   43 MB written (fifo 100%) [buf 100%]  14.8x.
 Track 03: Total bytes read/written: 45612336/45612336 (19393 sectors).
 Writing  time:   94.994s
 Average write speed  11.6x.
 Min drive buffer fill was 100%
 Fixating...
 Fixating time:   21.168s
 /usr/bin/wodim: fifo had 2059 puts and 2059 gets.
 /usr/bin/wodim: fifo was 0 times empty and 1854 times full, min fill was 98%.
 BURN-Free was never needed.
  cdrecord command:
 -----------------------
 /usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=24 -sao driveropts=burnfree -multi textfile=/tmp/qt_temp.N22400 -useinfo -audio -pad -shorttrack /tmp/kde-daniel/k3b_audio_0_01.inf /tmp/kde-daniel/k3b_audio_0_02.inf /tmp/kde-daniel/k3b_audio_0_03.inf
  mkisofs
 -----------------------
 74835
  mkisofs calculate size command:
 -----------------------
 /usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid DespiseConquer -volset  -appid K3B THE CD KREATOR (C) 1998-2007 SEBASTIAN TRUEG -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-daniel/k3bc22400.tmp -rational-rock -hide-list /tmp/kde-daniel/k3bV22400.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-daniel/k3bH22400.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-daniel/k3br22400.tmp
 
```

---

### Post by Danstroem on 2010-01-14
Workaround: Download and install the three packages

[http://packages.ubuntu.com/jaunty/libk3b3](http://packages.ubuntu.com/jaunty/libk3b3)
[http://packages.ubuntu.com/jaunty/k3b-data](http://packages.ubuntu.com/jaunty/k3b-data)
[http://packages.ubuntu.com/jaunty/k3b](http://packages.ubuntu.com/jaunty/k3b)

from the previous Ubuntu version (Jaunty) with the GDebi package manager (gdebi-gtk). The order of installing the three packages is important. Libk3b3 requires additional 7 packages like qt3, kde3, etc. They get installed automatically from the Karmic repository.

After this procedure k3b version 1.0.5 from Jaunty is installed on Karmic and it works like a charm! K3b is complaining that gvfsd-cdda is blocking the burning device, but suggests to kill the process. By doing this, the problem is SOLVED!

---

### Post by TimGS on 2010-01-15
I've had a problem with multisession data DVDs also.

From a search of this forum and the wider internet it seems there is a problem with k3b on karmic, or more likely, cdrecord (there are reported problems with multisession DVDs in packages other than k3b).

Danstroem's instructions for regressing to Jaunty's K3B worked for me (thanks!), but to ensure that apt-get doesn't 'upgrade' these back to Karmic's you need to create a preferences file to 'pin' K3B at version 1.0.5 (the Jaunty release).

```
sudo nano /etc/apt/preferences
```

and enter

```
Package: k3b
Pin: version 1.0.5*
Pin-Priority: 1001

Package: k3b-data
Pin: version 1.0.5*
Pin-Priority: 1001
```

To find out more about pinning and apt-get just do a quick search of the net. I found [http://automate-everything.com/2009/04/prevent-apt-get-from-upgrading-a-package-on-ubuntu/](http://automate-everything.com/2009/04/prevent-apt-get-from-upgrading-a-package-on-ubuntu/) was short and to the point, whereas [http://ccrma.stanford.edu/planetccrma/man/man5/apt_preferences.5.html](http://ccrma.stanford.edu/planetccrma/man/man5/apt_preferences.5.html) is more informative but probably more than you need to know!

-- Tim.

---

### Post by mageus on 2010-01-24
Same problem here.

Same solution works (regressing to Jaunty ver.)

There is something definitely wrong with Karmic's cd burning.  Actually, Karmic has been a downright miserable experience overall from so many other problems that make it unusable (I'm using my Jaunty partition as my regular boot).

Here are the k3b problems I've experienced:

- Multisession CDs
- There's a long delay between 'Starting Disc Write' and the buffers filling and actually starting to burn (about 30-60 seconds).  This was never there in Jaunty.
- I have many failed burns (about every 5th) that crashes wodim and k3b, forcing me to kill them.  I know it's not my burner since it doesn't happen under Jaunty.

---

### Post by AbdRahim on 2010-02-12
Warning: I tried this on an Intel 64 bit machine and it locked up the machine and messed up the file system.

---

### Post by BigAl-SA on 2010-03-31
> **Danstroem said:**
> Workaround: Download and install the three packages

[http://packages.ubuntu.com/jaunty/libk3b3](http://packages.ubuntu.com/jaunty/libk3b3)
[http://packages.ubuntu.com/jaunty/k3b-data](http://packages.ubuntu.com/jaunty/k3b-data)
[http://packages.ubuntu.com/jaunty/k3b](http://packages.ubuntu.com/jaunty/k3b)

from the previous Ubuntu version (Jaunty) with the GDebi package manager (gdebi-gtk). The order of installing the three packages is important. Libk3b3 requires additional 7 packages like qt3, kde3, etc. They get installed automatically from the Karmic repository.

After this procedure k3b version 1.0.5 from Jaunty is installed on Karmic and it works like a charm! K3b is complaining that gvfsd-cdda is blocking the burning device, but suggests to kill the process. By doing this, the problem is SOLVED!Thanks for this! I thought something was wrong with my writer with all the different errors that Karmic's version of K3b threw at me!

---

### Post by timesarehard4dreamers on 2010-08-21
Using a previous version is not a n ideal solution, new versions have bug fixes (usually!). I can't believe this bug hasn't been fixed yet and i'm using 10.0.4 Lucid!

---

### Post by Criminel on 2010-11-07
Same problem here. Still no solution or fix.

---

