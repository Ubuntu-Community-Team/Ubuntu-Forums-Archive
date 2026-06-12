---
title: "Cannot read some CDS (protected ones ?)"
date: 2012-12-25
forum: Multimedia Software
---

### Post by bretonfou on 2012-12-25
I have a CD of Helene grimaud and Vladimir ashkenazy (rachmaninov teldec) 
and my PC is unable to see it. The CD is not broken or damaged, i indeed
downloaded the horrible Itune on my  Mac(the one that my compagny lend 
me). Even if the process was ridiculous and painfull, and even if itune 
managed to separate the CD into two albums this devil sofware designed 
by psychopaths managed to do the work.


When i run abcde -d /dev/sr0 -o flac on other CDS it works perfectly, 
but that one and a couple of others do fail. 

this is on a normal CD. 
```

speren@newbiak:~$ cd-discid  /dev/sr0
8f08290c 12 150 12167 22880 39525 53987 66323 79650 88125 101471 115226 130656 142555 2091

```
this is on that "protected "cd

```
 cd-discid  /dev/sr0
cd-discid: /dev/sr0: CDROMREADTOCHDR: No medium found

```

I can ensure you that the CD is inside. 



here is my cd reader : 
```

sudo hdparm -i /dev/sr0

/dev/sr0:

 Model=ATAPI   iHAS122, FwRev=ZL08, SerialNo=3522424 338049500584
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=unknown, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

```


Some more info on my hardware : 


```

 sudo lshw -C disk 
PCI (sysfs)  
  *-cdrom                 
       description: DVD-RAM writer
       product: iHAS122
       vendor: ATAPI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sr0
       version: ZL08
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/sr0
  *-disk
       description: ATA Disk
       product: ST9500420AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 0002
       serial: 5VJB5P6A
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=3981218b

```



As far as i remembered when i replaced linux mint (which had too many 
bugs) by ubuntu 12.04 (granted that switching back to gnome classic was 
possible) i think that i saw my broken CD mounted in the live CD ...


Here some more code , first one of those bad cds 
and then with a regular one. 
```

cdparanoia -sQ
cdparanoia III release 10.2 (September 11, 2008)

004: Unable to read table of contents header

Unable to open disc.  Is there an audio CD in the drive?

```

with oscar peterson CD. 
```
 
speren@newbiak:~$ cdparanoia -sQ
cdparanoia III release 10.2 (September 11, 2008)


Table of contents (audio tracks only):
track        length               begin        copy pre ch
===========================================================
  1.    12017 [02:40.17]        0 [00:00.00]    no   no  2
  2.    10713 [02:22.63]    12017 [02:40.17]    no   no  2
  3.    16645 [03:41.70]    22730 [05:03.05]    no   no  2
  4.    14462 [03:12.62]    39375 [08:45.00]    no   no  2
  5.    12336 [02:44.36]    53837 [11:57.62]    no   no  2
  6.    13327 [02:57.52]    66173 [14:42.23]    no   no  2
  7.     8475 [01:53.00]    79500 [17:40.00]    no   no  2
  8.    13346 [02:57.71]    87975 [19:33.00]    no   no  2
  9.    13755 [03:03.30]   101321 [22:30.71]    no   no  2
 10.    15430 [03:25.55]   115076 [25:34.26]    no   no  2
 11.    11899 [02:38.49]   130506 [29:00.06]    no   no  2
 12.    14329 [03:11.04]   142405 [31:38.55]    no   no  2
TOTAL  156734 [34:49.59]    (audio only)


```


I have the problem with at least one other CD, namely Vivaldi concerto for 
madoline by the giardino armonico. And i quite expect many of my CDs to be 
unreadable too.

I m currently moving all my CD into flac, till recently i was using mp3/ogg
due to spcae limitation. And i was quite surprised to find out that some 
of them cannot be read under linux while the Itune  abomination manage to 
read them.

---

