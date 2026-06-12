---
title: "Commercial DVDs Not Working"
date: 2011-05-14
forum: Multimedia Software
---

### Post by MST3Kakalina on 2011-05-14
**BEFORE I SAY ANYTHING** let me make it clear that I have:

1. Read the documentation

and

2. Installed libdvdread4

and


3. Run the "sudo /usr/share/doc/libdvdread4/install-css.sh" command


I am running Natty, but for the last couple releases (not just Natty) I have been unable to mount and read commercial DVDs. Case in point: [my last thread here]("http://ubuntuforums.org/showthread.php?t=1633201").  Blank or burned DVD-Rs and CDs of any stripe work fine.  Sometimes in Maverick a DVD would just randomly mount and autoplay, but that was rare and I can't seem to reproduce it.

I've tried reinstalling libdvdread4, no dice.  Here's the output from terminal when I run VLC and try to open a DVD:

```
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0xa1cbe8c] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0xb75006fc] main input error: open of `dvdsimple:///dev/sr0' failed: (null)
```

Nonetheless, my computer (hp pavilion dv5000) *knows there's something in there* because **sudo lshw -C disk** yields:

```
*-cdrom 
description: DVD-RAM writer
product: DVDRAM GSA-4084N
vendor: HL-DT-ST
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/scd0
logical name: /dev/sr0
version: KQ09
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=ready
*-medium
physical id: 0
logical name: /dev/cdrom
```

though interestingly enough there is NOT an icon for the disc on Thunar or Nautilus.

My region is set as well (region 1).  I've tried with multiple discs, some of which I KNOW have worked previously.  It's not the DVD that's to blame.

**WHAT THE HELL AM I DOING WRONG?** Is this a problem with the switchover from libdvdread3 to libdvdread4?

I'm really frustrated that this problem seems to have fossilized from whatever release.  Ubuntu has been around for quite a while, now, there's not really a good excuse for issues like this.  I'm happy otherwise, but you can imagine this problem really grinds my gears.  Where's the RAGE smiley to include with this post?

---

### Post by handy on 2011-05-14
Toss in Restricted Formats:

[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

And the Medibuntu repo, (if you haven't already:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mc4man on 2011-05-14
MST3Kakalina - 
I remember your thread - too bad this is still an issue
ie. - 
the UDF filesystem on the dvd is not being automounted 
manually mounting the fs didn't work?
using vlc to directly access the drive as dvd_video doesn't work.
(  vlc dvd:///dev/sr0

It may be worthwhile to see if DMA or UDMA is enabled (should be by default

To check this (if in a pio mode that could be an issue
```
sudo hdparm -i /dev/sr0
```

---

### Post by MST3Kakalina on 2011-05-14
@mc4man: trying to manually mount it (mount /dev/sr0 and mount /dev/scd0) doesn't work, neither does trying to access it directly via VLC.

```
katherine@Priscilla:/dev$ sudo hdparm -i /dev/sr0 

/dev/sr0:

 Model=HL-DT-ST DVDRAM GSA-4084N, FwRev=KQ09, SerialNo=K0164I52602
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 *mdma2 
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 3:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode
```


@handy: I have all of the restricted extras installed; I also have the Medibuntu repositories in my sources.list.

---

### Post by MST3Kakalina on 2011-05-15
And a NEW AND EXCITING WRINKLE:  when the disc randomly attempts to mount (or at least when Xubuntu makes a random attempt to read it), everything freezes.  The screen goes black, the touchpad no longer responds.  Is this X taking a dump?  Or something?

This has happened twice in the past 24 hours, each freeze-up preceded by the sound of the disc spinning in the drive, as if being read.

I'm seriously considering just dumping everything and switching to Mint, at this point.

---

### Post by MST3Kakalina on 2011-05-16
The NEW AND EXCITING WRINKLE is largely mitigated (I hope, knock wood) by a fresh install of Xubuntu.  I scrapped everything and started fresh.  And yet---still this persists.

1.) I reinstalled.

2.) I installed "xubuntu-restricted-extras"

3.) I ran the terminal command to install libdvdread4

4.) I installed libdvdcss2

5.) I changed the permissions on my DVD drive as suggested in the documentation.

6.) I have the Medibuntu repositories in my sources.list and have installed and updated from them.

7.) The drive knows there's something in there; **sudo lshw -C disk** again brings up **status=ready**.

8.) The region on the DVD drive is set.

9.) I've even tried to the absolutely inane "insert an audio CD first" trick described here: [http://ubuntuforums.org/showthread.php?p=10158192#post10158192](http://ubuntuforums.org/showthread.php?p=10158192#post10158192) to no avail. 

It's almost like it's not mounting, but trying to mount it manually (/dev/dvd )  doesn't work either.

I don't mean to keep spamming my own thread....but really, I do.  If I have to deal with my DVD playback capabilities being borked from now until forever, I want someone to at least explain to me WHY this is.  It's frustrating to keep hitting this brick wall of silence; does that mean everyone is confounded by my problem and there is no solution?

---

