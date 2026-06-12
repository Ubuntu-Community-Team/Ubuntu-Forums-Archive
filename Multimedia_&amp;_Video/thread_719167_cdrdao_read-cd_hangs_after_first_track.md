---
title: "cdrdao read-cd hangs after first track"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by Cold Day on 2008-03-08
Hello,

I have a problem with cdrdao on Dell Inspiron 5100 after switching to Ubuntu 7.10 (from 7.04). cdrdao read-cd hangs on first track, like this:

$ sudo cdrdao read-cd --device 0,0,0 --speed 24 --eject -v 2 s.toc
...
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

0,0,0: HL-DT-ST RW/DVD GCC-4240N        Rev: D110
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Reading toc and track data...

Track   Mode    Flags  Start                Length
------------------------------------------------------------
 1      AUDIO   0      00:00:33(    33)     03:18:50( 14900)
 2      AUDIO   0      03:19:08( 14933)     03:28:70( 15670)
 3      AUDIO   0      06:48:03( 30603)     01:13:05(  5480)
 4      AUDIO   0      08:01:08( 36083)     03:54:22( 17572)
 5      AUDIO   0      11:55:30( 53655)     01:52:33(  8433)
 6      AUDIO   0      13:47:63( 62088)     00:39:57(  2982)
 7      AUDIO   0      14:27:45( 65070)     00:25:43(  1918)
 8      AUDIO   0      14:53:13( 66988)     01:14:20(  5570)
 9      AUDIO   0      16:07:33( 72558)     04:25:27( 19902)
10      AUDIO   0      20:32:60( 92460)     03:25:20( 15395)
11      AUDIO   0      23:58:05(107855)     01:33:33(  7008)
12      AUDIO   0      25:31:38(114863)     00:43:67(  3292)
13      AUDIO   0      26:15:30(118155)     03:34:30( 16080)
14      AUDIO   0      29:49:60(134235)     04:52:48( 21948)
15      AUDIO   0      34:42:33(156183)     04:36:37( 20737)
16      AUDIO   0      39:18:70(176920)     03:06:70( 14020)
17      AUDIO   0      42:25:65(190940)     05:03:30( 22755)
18      AUDIO   0      47:29:20(213695)     01:33:00(  6975)
19      AUDIO   0      49:02:20(220670)     01:17:70(  5845)
20      AUDIO   0      50:20:15(226515)     02:14:23( 10073)
21      AUDIO   0      52:34:38(236588)     02:32:05( 11405)
22      AUDIO   0      55:06:43(247993)     04:22:22( 19672)
23      AUDIO   0      59:28:65(267665)     03:36:25( 16225)
24      AUDIO   0      63:05:15(283890)     03:47:65( 17090)
Leadout AUDIO   0      66:53:05(300980)

PQ sub-channel reading (audio track) is supported, data format is BCD.
Copying audio tracks 1-24: start 00:00:00, length 66:53:05 to "data.bin"...
Track 1...
Found ISRC code.
[ ... and than hangs forever.... with sporadic nasty sounds from the drive ... ]

The drive is here:
$ sudo cdrdao scanbus
......
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

0,0,0 : HL-DT-ST, RW/DVD GCC-4240N, D110

Relevant dmesg piece:
sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 0:0:0:0: Attached scsi CD-ROM sr0
sr 0:0:0:0: Attached scsi generic sg0 type 5

Burning data CDs works perfectly and audio CDs are *played* normally as well. I also tried with older versions of cdrdao (from 6.10 and 6.04 repositories), but nothing changed. So the problem is apparently not in cdrdao itself but somewhere else... Anybody else seeing something similar?

Thank you!

---

### Post by andrew.46 on 2008-04-14
Hi,

 I have an outside thought:

> **Cold Day said:**
> 

I have a problem with cdrdao on Dell Inspiron 5100 after switching to Ubuntu 7.10 (from 7.04). cdrdao read-cd hangs on first track, like this:

```
$ sudo cdrdao read-cd --device 0,0,0 --speed 24 --eject -v 2 s.toc
```



Ubuntu does a few odd things with identifying drives. You could perhaps try either of the following:

```
$ sudo cdrdao read-cd --device ATA:0,0,0 --speed 24 --eject -v 2 s.toc
$ sudo cdrdao read-cd --device ATAPI:0,0,0 --speed 24 --eject -v 2 s.toc
```

which would make more sense particularly if your device is not *really* a scsi device.

 Please let me know if any of this works :-)

    Andrew

---

### Post by Zippo-lino on 2008-05-06
Hello,
I have the same problem on an IBM thinkpad T30 with the same optical drive (RW/DVD GCC 4240N). Here my cdrdao output:

bino@bino3-ulx:~$ cdrdao copy
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

/dev/cdrw: HL-DT-ST RW/DVD GCC-4240N   Rev: 0213
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Starting CD copy at speed 24...

Track   Mode    Flags  Start                Length
------------------------------------------------------------
 1      AUDIO   0      00:00:00(     0)     03:04:01( 13801)
 2      AUDIO   0      03:04:01( 13801)     03:11:37( 14362)
 3      AUDIO   0      06:15:38( 28163)     03:33:31( 16006)
 4      AUDIO   0      09:48:69( 44169)     04:07:66( 18591)
 5      AUDIO   0      13:56:60( 62760)     04:06:07( 18457)
 6      AUDIO   0      18:02:67( 81217)     02:10:62(  9812)
 7      AUDIO   0      20:13:54( 91029)     03:07:46( 14071)
 8      AUDIO   0      23:21:25(105100)     03:01:37( 13612)
 9      AUDIO   0      26:22:62(118712)     02:44:24( 12324)
10      AUDIO   0      29:07:11(131036)     03:22:51( 15201)
11      AUDIO   0      32:29:62(146237)     02:27:65( 11090)
12      AUDIO   0      34:57:52(157327)     03:45:01( 16876)
Leadout AUDIO   0      38:42:53(174203)

PQ sub-channel reading (audio track) is supported, data format is BCD.
Copying audio tracks 1-12: start 00:00:00, length 38:42:53 to "cddata5874.bin"...
Track 1...
Found ISRC code.
Found 182894 Q sub-channels with CRC errors.
Please insert a recordable medium and hit enter.


Now my question is how can I determine the numerical parameters of my optical drive for the --device option ATA:x,y,z or ATAPI:x,y,z for the cdrdao command that Andrew suggested????

Thanks for any helpful reply
Zippo-lino

---

