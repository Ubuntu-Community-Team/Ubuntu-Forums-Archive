---
title: "Convert kaffeine channels.dvb to mplayer channels.conf"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by Pigeon. on 2008-01-15
How do I convert kaffeine's channels.dvb to a channels.conf?

I have found loads of references to doing it the other way round, but this is less than useful...

/usr/share/doc/dvb-utils/examples/scan/dvb-t/ contains no suitable initial tuning files for my local transmitters so I cannot generate a channels.conf using scan in the normal way. kaffeine is capable of scanning without any such kickstart being necessary, however, and has generated a channels.dvb containing the channels I need.

Unfortunately mplayer doesn't understand the format so ATM I can only watch TV using kaffeine; I want to use mplayer and mencoder to watch/record from the command line.

---

### Post by Pigeon. on 2008-01-15
Hah.

I *may* have found the answer...

w_scan (download: "http://free.pages.at/wirbel4vdr/w_scan/w_scan-20070909.tar.bz2") seems to be capable of scanning without kickstart data and generating channels.conf output.

Am just trying it out... don't know if it works yet.

---

### Post by szag001 on 2008-02-22
Hi

I have the same problem. Does this utility work?

Thanks

S

---

### Post by Pigeon. on 2008-02-22
It doesn't seem to pick up every channel every time, even ones like BBC1 that you'd expect to be always detectable, I had to run it several times at different times of day and merge the results (uniq) but yeah, basically it works :) sorry I didn't post the result sooner...

---

