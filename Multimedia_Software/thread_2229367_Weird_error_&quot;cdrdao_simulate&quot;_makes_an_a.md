---
title: "Weird error: &quot;cdrdao simulate&quot; makes an audio CD unplayable"
date: 2014-06-12
forum: Multimedia Software
---

### Post by George Heine on 2014-06-12
Have been running cdrdao for years to created audio CDs, never had a problem until yesterday.
Using cdrdao 1.2.3 on Ubuntu 12.04 LTS.
Inserted the disk into the writer (/dev/sr1).  Here is the command and the resulting console output:

```
$ sudo cdrdao simulate --eject --device /dev/sr1 --driver generic-mmc-raw --overburn toc.txt

Cdrdao version 1.2.3 - (C) Andreas Mueller <andreas@daneb.de>
/dev/sr1: HL-DT-ST DVDRAM GE24LU20      Rev: OL00
Using driver: Generic SCSI-3/MMC (raw writing) - Version 2.0 (options 0x0000)

Starting write simulation at speed 48...
Pausing 10 seconds - hit CTRL-C to abort.
Process can be aborted with QUIT signal (usually CTRL-\).
Turning BURN-Proof on
Using 16 byte P-Q sub-channel data mode.
Writing lead-in and gap...
Writing track 01 (mode AUDIO/AUDIO )...
Writing track 02 (mode AUDIO/AUDIO )....
Wrote 579 of 579 MB (Buffers 100%  97%).
Wrote 258387 blocks. Buffer fill min 75%/max 100%.
Writing lead-out...
Wrote 15 of 15 MB.
Flushing cache...
Simulation finished successfully.

```

Command is my usual syntax.  I use "generic-mmc-raw" in order to get  CD-text, and "--overburn" in  case the audio files are slighly larger  than the rated disk capacity.   Neither of these applies here.

The result is a disk that is now unreadable on any CD player that I have.   Trying to run the same command, on the same disc, with "write" instead of simulate now gives repeated messages

```
WARNING: Unit not ready, still trying...

```

Trying to run the same command, on a fresh disc, with "write" instead of "simulate", gives the same result as above, i.e., an unplayable disc.

Here is the "table of contents" file
```
$ cat toc.txt
TRACK AUDIO COPY
 PREGAP 0:2:0
 FILE "track1.wav" 0 0
TRACK AUDIO COPY
 PREGAP 0:2:0
 FILE "track2.wav" 0 0

```
  

Is this a sudden hardware failure?  The disc writer is an LG External Super Multi DVD Rewriter, November 2011, connected to a USB port.  Note that it is still able to read and play other CD audio discs. I also have, until now, written many DVDs on this unit, one as recently as last week.

Output from "sudo lshw" :
```
$ sudo lshw
     *-scsi:0
          physical id: 1
          bus info: usb@1:8.3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GE24LU20
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/sr1
             version: OL00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=nodisc

```
Note the last line reports "nodisc" even though there is in fact a disc in the unit.


Any help would be much appreciated !

---

### Post by George Heine on 2014-06-18
Tried using wodim to write a set of ten audio files to CD on the same writer.  Tracks 1-8 seemed to burn normally,  then:

```
$ wodim -dev=/dev/sr1 -v -audio -pad *.wav
...
Starting new track at sector: 140549
Track 09:    0 of   40 MB written.Errno: 5 (Input/output error), write_g1 scsi sendcmd: retryable error
CDB:  2A 00 00 02 26 B5 00 00 1B 00
status: 0x0 (GOOD STATUS)
resid: 61456
cmd finished after 42.107s timeout 40s

write track data: error after 1016064 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 02 00 BB 80 A0 80 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0xA0 Qual 0x80 (vendor unique sense code 0xA0) [No matching qualifier] Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 23.049s timeout 120s
Trouble flushing the cache
Writing  time:  211.785s
Average write speed  11.2x.
Min drive buffer fill was 93%
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 3C 30 00 80 02 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x02 Qual 0x00 (no seek complete) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.002s timeout 480s
cmd finished after 0.002s timeout 480s
wodim: Cannot fixate disk.
Fixating time:    0.004s
wodim: fifo had 5372 puts and 5181 gets.
wodim: fifo was 0 times empty and 4165 times full, min fill was 94%.

```

After that, I tried a replacement drive, on which both wodim and cdrdao produced readable CDs.  So it does appear to be a hardware failure.  At least in this case, the error reporting capabilities of wodim seem superior to those of cdrdao.  It bothers me in particular that "cdrdao simulate" would actually do something to the disk.

---

### Post by tgalati4 on 2014-06-18
The laser diodes on CD/DVD burners have a habit of breaking down.  These diodes are separate from the read diodes, so reading is generally not affected.  Do a search on your particular model, there are probably others that have the same problem with that unit.  I know Sony had a bad batch of lasers on several models of CD/DVD writers.

I agree that simulate should not trash a disk, but it's possible that the CD writer attempts a write test from firmware to determine the type of disk inserted and the energy level required.  This would trash a disk if the level is too high and bleeds into adjacent tracks.  Try the simulate switch with a known, working cd writer and see if the disks are clean and usable afterward.  It's possible that it is a bug in *cdrdao*, but I am inclined to think a hardware problem is the issue.

---

### Post by George Heine on 2014-06-20
Thank you for your reply.  It was especially useful to get confirmation that the reading function and the burning function are separate, and
that one may work even if the other doesn't.  I will keep the drive and give it to my wife, who has a laptop without a disk reader.

The unit is listed as  HL-DT-ST DVDRAM GE24xxxx, but it is sold under the "LG" label.
A quick web search turned up very little information on this particular model.
However, LG does maintain a product support page, and gives tech support phone numbers at,
[http://answers.lg.com/answers/7676/product/MD00001193/lg-electronics-ge24lu20-questions-answers/questions.htm](http://answers.lg.com/answers/7676/product/MD00001193/lg-electronics-ge24lu20-questions-answers/questions.htm)

One thought: do the laser diode burners just break down after a lot of use ?  
I have burned dozens, if not hundreds, of CDs and DVDs with this unit.

---

### Post by tgalati4 on 2014-06-20
Sometimes it is just corrosion inside the diode.  I've had a few LG's replaced under warranty and some Sony's crapped out after warranty.  Certainly long burn hours would affect life, but many fail before the designed lifetime (50,000 hours or so).

---

