---
title: "libdvdread / can't read/watch DVDs"
date: 2009-06-20
forum: Multimedia Software
---

### Post by -spellweaver- on 2009-06-20
hi all,

sorry to open just another DVD thread, but this problem really bugs me. I read alot about this issue (it seems many other people got it as well), but I still can't solve it. So I need to know if any reliable solution exists.

My problem: I can't read/watch any encrypted/protected DVD.

Example:
# lsdvd
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
Can't open main ifo!

My environment:
Dell Latitude E6400
Jaunty, all updates applied

# dpkg -l | grep -i dvd
ii  dvd+rw-tools                               7.1-4
ii  dvdrip                                     1:0.98.9-0.0ubuntu1transcode and ffmpeg
ii  dvdrip-doc                                 20030223-0.1
ii  libdvdcss2                                 1.2.10-0.2medibuntu1
ii  libdvdnav4                                 4.1.3-3
rc  libdvdread3                                0.9.7-11ubuntu2
ii  libdvdread4                                4.1.3-4ubuntu2
ii  lsdvd                                      0.16-3ubuntu1

I also installed ubuntu-restricted-extras.

I would greatly appreciate any suggestions/help.

Many thanks in advance!
Kai

---

### Post by -spellweaver- on 2009-06-20
hi all,

it seems I solved it. Presumably the error was due to my dvd drive which is a MATSHITA. It seems that you indeed have to set the damn region code with those type of drive. The drive was configured region free and I wanted to play a region 2 dvd. I now used "regionset" to set the region code on the drive (dammit! I sooo did NOT want to do that!). Anyhow, after setting the region code, I once again reinstalled   libdvdcss2, libdvdread4 and ubuntu-restricted-extras (I think in that order). I still had to reboot until it worked.

Have a great day all.
Kai

---

