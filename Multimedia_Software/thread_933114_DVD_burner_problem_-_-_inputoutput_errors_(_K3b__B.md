---
title: "DVD burner problem - - input/output errors ( K3b / Brasero)"
date: 2008-09-29
forum: Multimedia Software
---

### Post by Steve H on 2008-09-29
Can someone help me with a problem I'm having with my LITEON DVD burner. I am trying to burn an iso image containg video(made in Devede) but it is not happening at all. It will burn at lower speeds (4x and below) but then still hangs at the "Updating RMA..." part of the process.

I already posted [this]("http://ubuntuforums.org/showthread.php?t=932271") as a reply to someone else getting the same error, but there is no help coming...boo!

I have tried both Brasero and K3b, but both are giving the same error in the debug output :

```
:-[ WRITE@LBA=1d0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: updating RMA
/dev/scd0: closing disc
```

Has anyone any ideas what is causing this and more importantly any idea how I can fix it?

I've read so much about this now it's making my head spin!!

 I did read something about it may be to do with the DMA settings or the IDE driver, but I have no idea how to check either.

---

### Post by Steve H on 2008-09-29
The full debug output from K3b looks like this (if it helps):

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
LITE-ON DVDRW LH-20A1P KL0G (/dev/scd0, /dev/sg2) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 16.4x1352KBps.
     950272/1440417792 ( 0.1%) @0.0x, remaining 151:28 RBU 100.0% UBU   9.7%
     950272/1440417792 ( 0.1%) @0.0x, remaining 227:13 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 302:57 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 403:56 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 479:41 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 555:25 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 656:24 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 732:09 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 807:53 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 908:52 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 984:37 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1060:21 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1161:20 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1237:04 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1312:49 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1413:48 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1489:32 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1565:17 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1666:16 RBU 100.0% UBU 100.0%
     950272/1440417792 ( 0.1%) @0.0x, remaining 1742:00 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=1d0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: updating RMA
/dev/scd0: closing disc

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:703329 -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m
```

---

### Post by Steve H on 2008-09-29
UPDATE: Still happening in ALL burning apps (Brasero, k3b, Gnomebaker). They are all using growisofs 7.0.1.

They can all burn iso images for CD no problem whatsoever!

I've got a LITE-ON DVDRW LH-20A1P that seems supported in all the device managers in Ubuntu...

:(

---

### Post by Steve H on 2008-09-29
FINALLY...

I can finally write DVD iso files to disc. After much testing of various media it seems a couple of things were going on here:

1, Some of the DVD-R discs were coasters before I got to them (wouldn't mount and give icon on desktop)

2.Could read DVD discs as data but not Play them.

3.Ubuntu's little "in built" CD/DVD Creator software was cocking everything up!! (more later)

I tried everything to get this working, even installing all the [DVD codecs]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron"), which allowed me to at least play some DVDs if not burn them. I finally found that Ubuntu comes ready with the capability to Burn iso images to disc......right click "write to disc" and hey presto!! bos your uncle...fannies your aunt, the bloody thing worked!!!

I wish someone had mentioned this at some point, I wouldn't have had to trawl the net looking for answers to something that wasn't a problem.

Does anyone know if this little "module" thats the CD/DVD Creator interfers in any way with higher level GUIs? Would that account for the input-output errors, if the control of that function lies with the Ubuntu system?

Anyway I've successfully burned the iso image (i tested it!) now so calm can return to my little corner of the world!!

:D

---

### Post by Ev1L on 2008-10-10
> **Steve H said:**
> FINALLY...

I can finally write DVD iso files to disc. After much testing of various media it seems a couple of things were going on here:

1, Some of the DVD-R discs were coasters before I got to them (wouldn't mount and give icon on desktop)

2.Could read DVD discs as data but not Play them.

3.Ubuntu's little "in built" CD/DVD Creator software was cocking everything up!! (more later)

I tried everything to get this working, even installing all the [DVD codecs]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_install_multimedia_support_on_Hardy_Heron"), which allowed me to at least play some DVDs if not burn them. I finally found that Ubuntu comes ready with the capability to Burn iso images to disc......right click "write to disc" and hey presto!! bos your uncle...fannies your aunt, the bloody thing worked!!!

I wish someone had mentioned this at some point, I wouldn't have had to trawl the net looking for answers to something that wasn't a problem.

Does anyone know if this little "module" thats the CD/DVD Creator interfers in any way with higher level GUIs? Would that account for the input-output errors, if the control of that function lies with the Ubuntu system?

Anyway I've successfully burned the iso image (i tested it!) now so calm can return to my little corner of the world!!

:D

i missed the point:
how did you managed it? with the ubuntu integrated burner?
then it doens't solve the problem in general, because i am trying to burn ISO with specific parameters (for XBOX)

apparently these problems didn't happen with Gutsy or Windows, so it must be something in Hardy. i am wasting a lot of expensive Verbatim :\

---

### Post by Victor Rossetti on 2008-10-13
Hi to everybody...

I had the same problem when burning dvd iso images with k3b. At some point (usually near the 50%) the burning was interrupted, and for some time  I tought I had to put my half burned dvd's into the trash bin.....BUT NO..

I digged into the internet and I found something interesting: k3b (in fact the backend growisofs) given some parameters breaks the image in two large pieces, same size each one, and writes each piece in a different layer, but for some reason unknown to me, after burning the first half, it gives an error in some burners and quits. What I didn't know is that in DVD's the burning process is quite different from CD's and in some cases you can RESUME the burning process. So I put back my half burned disk,opened a terminal window and wrote: 

```
'growisofs -dvd-compat -Z /dev/scd0=my_image_name_here.iso'
```

At first it gave the impression that it was starting from the very beginning of the image, but when arrived to the 50% it reported the same error k3b gave at first...but after that IT CONTINUED TILL THE END and burned a good usable DVD.

I will like to know more about the internals of the DVD burning process in order to fully understand what I did almost by luck.

Bye!

Victor Rossetti, M.D.
Caracas Venezuela

---

### Post by Ev1L on 2008-10-13
> **Victor Rossetti said:**
> Hi to everybody...

I had the same problem when burning dvd iso images with k3b. At some point (usually near the 50%) the burning was interrupted, and for some time  I tought I had to put my half burned dvd's into the trash bin.....BUT NO..

I digged into the internet and I found something interesting: k3b (in fact the backend growisofs) given some parameters breaks the image in two large pieces, same size each one, and writes each piece in a different layer, but for some reason unknown to me, after burning the first half, it gives an error in some burners and quits. What I didn't know is that in DVD's the burning process is quite different from CD's and in some cases you can RESUME the burning process. So I put back my half burned disk,opened a terminal window and wrote: 

```
'growisofs -dvd-compat -Z /dev/scd0=my_image_name_here.iso'
```

At first it gave the impression that it was starting from the very beginning of the image, but when arrived to the 50% it reported the same error k3b gave at first...but after that IT CONTINUED TILL THE END and burned a good usable DVD.

I will like to know more about the internals of the DVD burning process in order to fully understand what I did almost by luck.

Bye!

Victor Rossetti, M.D.
Caracas Venezuela
I expect this to be a quite limited case (I already threw away my trash with A LOT of partially burned DVDs, so i can't try).
I experienced the problem with different OSs, SWs, speeds, and at different percentages, always using Verbatim, which should be the top media (quite some money into the trash too...).
Only at the very beginning, on Vista, it never screwed any DVD, but I tried to reinstall it last weekend and now it's not working even there :(

Furthermore, since I am burning XBOX360 games, which are very sensible to block size, I doubt that a resume could produce a working game.

Anyway good to know this chance for future reference

---

### Post by wsellars on 2010-01-18
did all of the previously specified with the terminal code but when i enter this (and i did change the name) it says "previous "session" device is not specified, do use -M or -Z option"

---

### Post by ravidborse on 2011-12-29
Hi All(Solved in my case)

  - To Resolve Below Error related to my Sony DVD-RW Just Remove your DVD-RW player 
  -  Open it with the screwdriver(Its very Easy). Now you can see the Reader-Writer Lense . 
  - Take any solution(Prefer Alcoholic or the solution you use it to clean LCD) and cotton. 
  -[B] Use a cotton swab and something like alcoholic solution(small) to gently wipe the lens. Just a quick scrub will do. 
  - Dry the laser pickup lens with the other end of the swab.Keep it 10-15 Mins to dry that lens. [/B]
  - Do this carefully Please. I have done it on my own risk. you can also. below is the error

```

DVD-RW Sequential

Devices
-----------------------
SONY DVD RW AW-G170A 1.74 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.5.5 (KDE 4.5.5)
QT Version:  4.6.3
Kernel:      2.6.33.3-85.fc13.i686.PAE

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 2.0x1352KBps.
          0/669122560 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
=== last message repeated 20 times. ===
:-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=4gms -use-the-force-luke=tracksize:326720 -dvd-compat -speed=2 -use-the-force-luke=bufsize:32m
```

---

### Post by overdrank on 2011-12-29
Hi and welcome, please view the date of the thread. Old thread = Closed thread.

---

