---
title: "Choppy DVD playback in Jaunty"
date: 2009-05-16
forum: Multimedia Software
---

### Post by ice cold on 2009-05-16
I did a complete fresh install of Jaunty but now DVD playback is really choppy with vlc, xine and mplayer.  I've tried with and without the nVidia 96 series driver, various output modules, desktop effects enabled and not and with and without hardware acceleration.  DVD playback was fine in Hardy with all these players.  I think this might be a DMA issue, can anyone help???  I'd really appreciate it!

---

### Post by zero777zero on 2009-05-16
did you install libcss2 yet?

---

### Post by ice cold on 2009-05-16
Yeah, libdvdcss2, libdvdnav4, libdvdread4, libdvdetc. etc. are all installed.  I'm just having problems with frame drops, momentary pauses and generally very unsmooth playback.  I'm using the nvidia 96.43.10 driver.  Hardy worked fine, so I'm wondering if there are differences between the way hardy and jaunty handle video DVDs?

---

### Post by rmbell on 2009-05-18
I am also having issuses with DMA and jaunty. No matter what I've tried, I can't get DMA to enable.

```
[    2.232392] ata3.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.02, max UDMA/66
[    2.232407] ata3.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    2.232409] ata3.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    2.248338] ata3.00: configured for UDMA/66

```

---

### Post by mc4man on 2009-05-18
rmbell

Why don't you ck. and see what hdparm reports

Assumming /dev/sr0 for that drive (if not try /dev/sr1
```
sudo hdparm -i /dev/sr0
```

lines 2 and 3 are actually 1 line (put them together, tells how to enable ( though doesn't seem needed in this case

ATAPI DMA disabled for reliablity issues.  It can be enabled via pata_ali.atapi_dma modparam or corresponding sysfs node.

But line 4 suggests that dma has been enabled (udma4 - highest mode for dvd drives)

---

### Post by rmbell on 2009-05-20
```
rob@rob-desktop:~$ sudo hdparm -i /dev/sr0

/dev/sr0:

 Model=HL-DT-STDVD-RAM GH22NP20                , FwRev=1.02    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6

 * signifies the current active mode

```

odd, it says its in DMA, yet I can't achieve any burn speeds higher then 1.0x, and it entirely bogs my CPU down.

---

### Post by gbugher on 2009-05-22
I have the same problem as Rmbell... hdparm shows I'm in udma4, there are no DMA errors in dmesg, video playback of files (mpeg, avi, etc.) is great, but playback of DVDs is extremely choppy (video-wise; the sound is fine.)  This is true regardless of application (I've tried Totem, Xine, and even XBMC.)  I'm using Intel GMA 945 graphics.

---

### Post by quickk on 2009-05-23
I have the exact same problem.  It looks like DMA is not enabled since I can't burn dvds at more than 1.5X.  With ubuntu 8.10 this was not a problem: the slowness only appeared with 9.04.

---

### Post by rmbell on 2009-05-23
> **quickk said:**
> I have the exact same problem.  It looks like DMA is not enabled since I can't burn dvds at more than 1.5X.  With ubuntu 8.10 this was not a problem: the slowness only appeared with 9.04.


The problem also only appeared with the upgrade from 8.10 to 9.04 for me as well.

---

### Post by monkiki on 2009-05-23
Any tip?

---

### Post by gandaran on 2009-05-23
> **monkiki said:**
> Any tip?
yes, change the video output driver in vlc or mplayer video preferences to xv or x11 or any other that works.

---

### Post by rmbell on 2009-05-23
> **gandaran said:**
> yes, change the video output driver in vlc or mplayer video preferences to xv or x11 or any other that works.

...what about burning discs?

---

### Post by quickk on 2009-05-25
I found a solution.  See my post (#17) in [this thread]("http://ubuntuforums.org/showthread.php?p=7341658#post7341658").

---

