---
title: "Playing CSSed DVD works as root but not as restricted user"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by mks99 on 2007-07-23
Hello!

I'm trying to play the Shrek (1) DVD. This works for me as root but not under my restricted user account.
My system:
- Thinkpad T60
- Feisty amd64
- libdvdcss from medibuntu.org installed.

This is what I get when running xine as restricted user and starting DVD playback:
mks@balrog:~$ xine
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000002d4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0002d6a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00078e0f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x002974dd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002974e2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00309e9a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00309e9f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00317070
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00317075
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0032233d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00322342
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00323d97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00323d9c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00323eb5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00323eba
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0033d7a3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0033d7a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0033d8be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0033d8c3
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 0

All is fine (DVD menu is shown etc.) until the main movie starts. Then xine aborts playback showing an error dialog which says:
"The source seems encrypted and can't be read.
Your DVD is propably encryped. According to your country laws, you
can or can't install/use libdvdcss to be able to read this disc, which
you bought. (Media stream scrambled/encrypted)"

If I start xine as root, I get the same output on the console. The only difference is that instead of the error message, xine shows the main movie just fine.
There obviously seems to be some kind of permission problem. But I can't seem to find /which/ permission is wrong, since this

mks@balrog:/dev$ ll cdrom cdrw dvd dvdrw scd0 sr0
lrwxrwxrwx 1 root root      4 2007-07-19 11:52 cdrom -> scd0
lrwxrwxrwx 1 root root      4 2007-07-19 11:52 cdrw -> scd0
lrwxrwxrwx 1 root root      4 2007-07-19 11:52 dvd -> scd0
lrwxrwxrwx 1 root root      4 2007-07-19 11:52 dvdrw -> scd0
brw-rw---- 1 root cdrom 11, 0 2007-07-19 11:51 scd0
lrwxrwxrwx 1 root root      4 2007-07-19 11:52 sr0 -> scd0

in combination with

mks@balrog:/dev$ LC_ALL=C id
uid=1000(mks) gid=1000(mks)
groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(mks)

looks good to me.

Am I missing something obvious or what else should I check?

Regards
  mks

---

