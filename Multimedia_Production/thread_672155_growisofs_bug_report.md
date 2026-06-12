---
title: "growisofs bug report"
date: 2008-01-19
forum: Multimedia Production
---

### Post by phill0 on 2008-01-19
I've been recording with growisofs for many months now, but today I have encountered a bug, which seems to be dependent on the file names that are being recorded, here's the output that I get:

> 
vi@compy:~$ growisofs -dvd-compat -Z /dev/dvd -J -R /home/vi/dvd6
Executing 'genisoimage -J -R /home/vi/dvd6 | builtin_dd of=/dev/dvd obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using THE_D000.AVI;1 for  /the.daily.show.01.14.08.dsr.xvid-crimson.[VTV].avi (the.daily.show.01.16.08.dsr.xvid-0tv.[VTV].avi)
Using THE_C000.AVI;1 for  /the.colbert.report.01.14.08.dsr.xvid-crimson.[VTV].avi (the.colbert.report.01.15.08.dsr.xvid-crimson.[VTV].avi)
Using JERIC000.XVI for  /Jericho.S02E01.READNFO.DVDSCR.XviD-BSGTV (Jericho.S02E02.PROPER.DVDSCR.XviD-BSGTV)
Using JERIC001.XVI for  /Jericho.S02E02.PROPER.DVDSCR.XviD-BSGTV (Jericho.S02E03.PROPER.DVDSCR.XviD-BSGTV)
genisoimage: Unexpected joliet directory length 2044 expected: 2174 ''
*** glibc detected *** genisoimage: double free or corruption (!prev): 0x00000000009f7210 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b4e319f4b0a]
/lib/libc.so.6(cfree+0x8c)[0x2b4e319f86fc]
genisoimage[0x41a886]
genisoimage[0x41aa43]
genisoimage(main+0x1a16)[0x40ebf6]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b4e319a0b44]
genisoimage[0x40cb29]
======= Memory map: ========
00400000-00466000 r-xp 00000000 08:02 29016770                           /usr/bin/genisoimage
00666000-0068d000 rw-p 00066000 08:02 29016770                           /usr/bin/genisoimage
0068d000-00a04000 rw-p 0068d000 00:00 0                                  [heap]
2b4e31553000-2b4e31570000 r-xp 00000000 08:02 19054611                   /lib/ld-2.6.1.so
2b4e31570000-2b4e31573000 rw-p 2b4e31570000 00:00 0
2b4e31573000-2b4e315b2000 r--p 00000000 08:02 4440072                    /usr/lib/locale/ru_RU.utf8/LC_CTYPE
2b4e315b2000-2b4e315b9000 r--s 00000000 08:02 29020279                   /usr/lib/gconv/gconv-modules.cache
2b4e315b9000-2b4e315ba000 rw-p 2b4e315b9000 00:00 0
2b4e3176f000-2b4e31771000 rw-p 0001c000 08:02 19054611                   /lib/ld-2.6.1.so
2b4e31771000-2b4e31782000 r-xp 00000000 08:02 29016244                   /usr/lib/libmagic.so.1.0.0
2b4e31782000-2b4e31981000 ---p 00011000 08:02 29016244                   /usr/lib/libmagic.so.1.0.0
2b4e31981000-2b4e31982000 rw-p 00010000 08:02 29016244                   /usr/lib/libmagic.so.1.0.0
2b4e31982000-2b4e31983000 rw-p 2b4e31982000 00:00 0
2b4e31983000-2b4e31ad5000 r-xp 00000000 08:02 21970957                   /lib/libc-2.6.1.so
2b4e31ad5000-2b4e31cd4000 ---p 00152000 08:02 21970957                   /lib/libc-2.6.1.so
2b4e31cd4000-2b4e31cd7000 r--p 00151000 08:02 21970957                   /lib/libc-2.6.1.so
2b4e31cd7000-2b4e31cd9000 rw-p 00154000 08:02 21970957                   /lib/libc-2.6.1.so
2b4e31cd9000-2b4e31cde000 rw-p 2b4e31cd9000 00:00 0
2b4e31cde000-2b4e31cf4000 r-xp 00000000 08:02 29019008                   /usr/lib/libz.so.1.2.3.3
2b4e31cf4000-2b4e31ef4000 ---p 00016000 08:02 29019008                   /usr/lib/libz.so.1.2.3.3
2b4e31ef4000-2b4e31ef5000 rw-p 00016000 08:02 29019008                   /usr/lib/libz.so.1.2.3.3
2b4e31ef5000-2b4e31ef7000 rw-p 2b4e31ef5000 00:00 0
2b4e31ef7000-2b4e31f04000 r-xp 00000000 08:02 19054613                   /lib/libgcc_s.so.1
2b4e31f04000-2b4e32104000 ---p 0000d000 08:02 19054613                   /lib/libgcc_s.so.1
2b4e32104000-2b4e32105000 rw-p 0000d000 08:02 19054613                   /lib/libgcc_s.so.1
2b4e34000000-2b4e34021000 rw-p 2b4e34000000 00:00 0
2b4e34021000-2b4e38000000 ---p 2b4e34021000 00:00 0
7fff79542000-7fff79557000 rw-p 7fff79542000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
/dev/dvd: "Current Write Speed" is 18.4x1352KBps.
builtin_dd: 48*2KB out @ average 0.0x1352KBps
/dev/dvd: flushing cache
/dev/dvd: closing track
/dev/dvd: closing disc


One thing that I don't understand is: why close the disk if nothing was recorded?! :(

The file names in that directory are (listed with ls -R1):
> 
dvd6:
Comedy.Central.Presents.Kyle.Grooms.DSR.XviD-KYR.avi
CSI.Miami.S06E13.HDTV.XviD-LOL.avi
Family.Guy.S06E08.HR.PDTV.x264-CTU
Jay.Leno.2008.01.14.Marilu.Henner.HDTV.XviD-FQM
Jericho.S02E01.READNFO.DVDSCR.XviD-BSGTV
Jericho.S02E02.PROPER.DVDSCR.XviD-BSGTV
Jericho.S02E03.PROPER.DVDSCR.XviD-BSGTV
Prison.Break.S03E09.HDTV.XviD-NoTV.avi
Psych.S02E11.HDTV.XviD-0TV.avi
Terminator.The.Sarah.Connor.Chronicles.S01E01.HDTV.XviD-0TV
Terminator.The.Sarah.Connor.Chronicles.S01E02.HDTV.XviD-NoTV.avi
the.colbert.report.01.14.08.dsr.xvid-crimson.[VTV].avi
the.colbert.report.01.15.08.dsr.xvid-crimson.[VTV].avi
the.daily.show.01.14.08.dsr.xvid-crimson.[VTV].avi
The.Daily.Show.01.15.08.DSR.XviD-SYS
the.daily.show.01.16.08.dsr.xvid-0tv.[VTV].avi

dvd6/Family.Guy.S06E08.HR.PDTV.x264-CTU:
family.guy.s06e08.hr.pdtv.x264-ctu.mkv
family.guy.s06e08.hr.pdtv.x264-ctu.nfo

dvd6/Jay.Leno.2008.01.14.Marilu.Henner.HDTV.XviD-FQM:
jay.leno.2008.01.14.hdtv.xvid-fqm.avi
jay.leno.2008.01.14.hdtv.xvid-fqm.nfo

dvd6/Jericho.S02E01.READNFO.DVDSCR.XviD-BSGTV:
jericho.201.dvdscr.xvid-bsgtv.avi
jericho.201.dvdscr.xvid-bsgtv.nfo

dvd6/Jericho.S02E02.PROPER.DVDSCR.XviD-BSGTV:
jericho.202.dvdscr.xvid-bsgtv.avi
jericho.202.dvdscr.xvid-bsgtv.nfo

dvd6/Jericho.S02E03.PROPER.DVDSCR.XviD-BSGTV:
jericho.203.dvdscr.xvid-bsgtv.avi
jericho.203.dvdscr.xvid-bsgtv.nfo

dvd6/Terminator.The.Sarah.Connor.Chronicles.S01E01.HDTV.XviD-0TV:
terminator.the.sarah.connor.chronicles.s01e01.hdtv.xvid-0tv.avi
terminator.the.sarah.connor.chronicles.s01e01.hdtv.xvid-0tv.nfo

dvd6/The.Daily.Show.01.15.08.DSR.XviD-SYS:
the.daily.show.01.15.08.dsr.xvid-sys.avi
the.daily.show.01.15.08.dsr.xvid-sys.nfo


The bug repeats every time when I try to record that directory. I'm gonna try renaming Jericho's and see if bug repeats.

---

### Post by disturbed1 on 2008-01-19
Try using mkisofs to make the image first. Genisoimage has a ***few*** bugs ;)

[http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=genisoimage;dist=unstable](http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=genisoimage;dist=unstable)

---

### Post by phill0 on 2008-01-19
Thank you, **disturbed1** for quick reply. I wasn't creating image first because I don't always have enough space on hard drive, but that's not a big problem. I was wondering maybe using k3b will be a better/safer alternative to growisofs, or is it essentially the same thing?

---

### Post by disturbed1 on 2008-01-19
K3b is only a gui to growisofs and wodim/cdrecord/cdrdao.

Run growisofs from a terminal with the -version command.

Here's what I get :D

> 
:~$ growisofs -version
* growisofs by <appro@fy.chalmers.se>, version 7.0.1,
  front-ending to genisoimage: mkisofs 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1993-1997 Eric Youngdale (C) 1997-2007 J&#65533;rg SchillingI deleted the wodim and genisoimage binaries and copied/renamed cdrecord/mkisofs to overcome the stupid errors present in these 2 packages.

Wodim and Genisoimage are a Debian fork of cdrecord and mkisofs, the commands are exactly the same. Only wodim and genisoimage are based on 4 year old code with little to know development presently going on.

---

### Post by phill0 on 2008-01-19
I get the following output from "growisofs -version":
> 
* growisofs by <appro@fy.chalmers.se>, version 7.0.1,
  front-ending to genisoimage: genisoimage 1.1.6 (Linux)



> **disturbed1 said:**
> K3b is only a gui to growisofs and wodim/cdrecord/cdrdao.

Run growisofs from a terminal with the -version command.

Here's what I get :D

I deleted the wodim and genisoimage binaries and copied/renamed cdrecord/mkisofs to overcome the stupid errors present in these 2 packages.

Wodim and Genisoimage are a Debian fork of cdrecord and mkisofs, the commands are exactly the same. Only wodim and genisoimage are based on 4 year old code with little to know development presently going on.

---

