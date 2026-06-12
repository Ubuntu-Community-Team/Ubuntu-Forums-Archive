---
title: "No DVD playback in myth, but works in vlc"
date: 2009-06-25
forum: Mythbuntu
---

### Post by laffinet on 2009-06-25
Hi !

I can't play DVDs anymore in myth. I now it worked when I had 8.10 installed, not sure if it ever worked since I installed 9.04.

I've got the codecs enabled in mythbuntu control centre, also ran:

```
sudo apt-get install libxine1-ffmpeg libdvdread
```
and
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

I can play the dvd fine when just starting vlc.

I've opened the frontend in a terminal, when trying to play a dvd I get this:
```
libdvdnav: Using dvdnav version 0.1.10-xine from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /dev/dvd
No such file or directory
libdvdnav: vm: faild to open/read the DVD
2009-06-25 17:38:46.022 Failed to open DVD device at /dev/dvd

```

hdparm returns this:

```
hdparm /dev/sr0

/dev/sr0:
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

and this

```
sudo hdparm -Tt /dev/sr0

/dev/sr0:
read(2097152) returned 786432 bytes
 Timing buffered disk reads:  read() failed: Input/output error

```

Any ideas ?

---

### Post by ian dobson on 2009-06-25
Hi,

The error message is "2009-06-25 17:38:46.022 Failed to open DVD device at /dev/dvd" but you check /dev/sr0 (I know it should be symbolic linked but it doesn't always work). 

Why not just reconfigure myth-frontend to use /dev/sr0, thats what I did on my box.

Regards
Ian Dobson

---

### Post by laffinet on 2009-06-25
some more info

```
hdparm -i /dev/sr0

/dev/sr0:

 Model=PIONEER DVD-RW  DVR-216                 , FwRev=1.09    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

```

---

### Post by laffinet on 2009-06-25
> **ian dobson said:**
> Hi,

The error message is "2009-06-25 17:38:46.022 Failed to open DVD device at /dev/dvd" but you check /dev/sr0 (I know it should be symbolic linked but it doesn't always work). 

Why not just reconfigure myth-frontend to use /dev/sr0, thats what I did on my box.

Regards
Ian Dobson

Yeah, I noticed that after I posted, too. How do I reconfigure the frontend to use /dev/sr0 ? Had a quick look, but couldn't find it.

---

### Post by .Maleficus. on 2009-06-25
IIRC, HAL defaults the first drive at /dev/cdrom, regardless of the type.  On my main Arch install that's what it is anyways, and was the last time I used Kubuntu (and it's a DVDRW).  You could give that a try too.

---

### Post by laffinet on 2009-06-25
> **.Maleficus. said:**
> IIRC, HAL defaults the first drive at /dev/cdrom, regardless of the type.  On my main Arch install that's what it is anyways, and was the last time I used Kubuntu (and it's a DVDRW).  You could give that a try too.

Sorry, I don't understand what you mean...:confused:
Can you simplify ?

---

### Post by laffinet on 2009-06-26
Found it.

Setup -> Media Settings -> Video -> General

Changed it to /dev/sr0, playback now works in myth.

---

