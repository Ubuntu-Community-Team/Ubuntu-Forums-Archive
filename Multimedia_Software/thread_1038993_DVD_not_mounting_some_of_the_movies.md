---
title: "DVD not mounting some of the movies"
date: 2009-01-14
forum: Multimedia Software
---

### Post by Berduchwal on 2009-01-14
Hi
Recently I got my hands on 2 DVD that I can not play:
Rambo – 2007 version
Merlin -vol.1 disc 1
both of those dvd do not even mount when I put them into the drive!

I have followed following links and installed all of the plugins and libraries as well as run the scripts.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")


More specific I do have libdvdread3 and I run: 
```

sudo /usr/share/doc/libdvdread3/install-css.sh


```

All other DVD's play fine.

Can someone please tell me what diagnostics can I run to discover what it does not mount?

---

### Post by Berduchwal on 2009-01-15
I have just discovered that sometimes it does mount one of the above films:

Merlin

If it mounts them it work straight away on other occasion it does not.

It appears that reboot changes something as after the reboot they might not work again!

If it does not work DVD rom makes different noise as well kind of trying noise like little bit scratchy :)

If it was unable to mount move at the first attempt and I tried 10 more times it did not mount it 10th time either.

Will try rebooting few times and see if this does anything.

---

### Post by johnjohn2 on 2009-01-15
From experience it sounds like the dvd lens needs cleaning!

Do you have another drive you can try.

Canyou copy the disk to the hard drive using brasero?

:guitar:

---

### Post by Berduchwal on 2009-01-15
Thanks for your help!

This is new DVD drive just about 3 months old in total I probably watched 10-12 DVD on it never had any issues till now.

Brasero say no available media when I select copy DVD. I do not think it can copy something that it is not mounted?

I have checked the lens and it is crystal clean.

I have just tried:
```
username@pcname:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom0/
mount: No medium found

```

do not know if this helps but:

```

username@pcname:~$ hdparm -i /dev/scd0

/dev/scd0:

 Model=HL-DT-ST DVDRAM GSA-T20N                , FwRev=WP03    , SerialNo=M3381AK5814         
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode
```






-----------------------

cleaning the lens helped in the end :)

---

