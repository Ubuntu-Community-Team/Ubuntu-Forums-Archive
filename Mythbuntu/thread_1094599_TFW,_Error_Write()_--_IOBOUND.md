---
title: "TFW, Error: Write() -- IOBOUND"
date: 2009-03-12
forum: Mythbuntu
---

### Post by Ryan-M- on 2009-03-12
Hi folks, im trying to track down the cause of this error, as its causing live tv to freeze on a regular basis now. 
I'm running 7.10 (I know its old hat now) but its been pretty solid until now. The problem appears to have started shortly after I upgraded the nvidia driver for my 9500GT but im fairly sure its a disk issue ? I have 2 sata samsung drives, one old 200gb which has the install on it and a newer 500gb one that live tv records to so im assuming that this is the drive thats causing the problem.
I ran hdparm -tT on both drives and the newer 500gb drive seems to be much slower than I would expect, unfortunately I dont know if this has always been the case so maybe im barking up the wrong tree here ?
 Anyway here is the error that appears to be freezing live tv

 TFW, Error: Write() -- IOBOUND begin cnt(9400) free(1139)
 TFW, Error: Write() -- IOBOUND end
 DevRdB(1) Error: Driver buffers overflowed

and here is the result of hdparm, sdb is the 500gb (livetv) drive

/dev/sda:
 Timing cached reads:   1032 MB in  2.00 seconds = 515.65 MB/sec
 Timing buffered disk reads:  186 MB in  3.02 seconds =  61.54 MB/sec 

/dev/sdb:
 Timing cached reads:   1034 MB in  2.00 seconds = 517.10 MB/sec
 Timing buffered disk reads:   54 MB in  4.49 seconds =  12.02 MB/sec

Any help is appreciated,

  Thanks in advance   :D

 Ryan

---

### Post by Ryan-M- on 2009-03-16
Figured I might as well reply to my own post, turns out the drive maybe on its way out. I ran the diagnostics on it and it fails the self test from seagate, so if anyone else gets this error then thats the direction to look in.

---

