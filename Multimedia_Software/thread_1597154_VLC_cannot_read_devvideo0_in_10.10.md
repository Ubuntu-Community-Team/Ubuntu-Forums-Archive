---
title: "VLC cannot read /dev/video0 in 10.10"
date: 2010-10-15
forum: Multimedia Software
---

### Post by GWBouge on 2010-10-15
I've been using VLC to view my Hauppauge 1600 without any real issues until I upgraded to Ubuntu 10.10.  Totem and mplayer can open the stream, however VLC keeps giving me the following errors:

```
libdvdnav: Can't seek to block 32
libdvdnav: Unable to find map file '/home/bummer/.dvdnav/.map'
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[0x7f34e0009660] main access error: Read error: Device or resource busy
[0x7f34e0009660] filesystem access error: failed to read (Device or resource busy)
[0x2a9fa60] main stream error: cannot pre fill buffer
```

... any ideas?

---

### Post by GWBouge on 2010-10-15
Ok, today it decided it wanted to work the first time I opened it.  I had VLC up streaming TV for a couple hours.  I closed it, waited about 10 minutes, started it again and it's giving me the same error ...

I found that if I close the error box that pops up in VLC (which says "File reading failed: VLC could not read the file."), and press the Play button, it works fine.  So ... it's not a show stopper, just slightly annoying, lol.

Any clue as to why it does that, and hopefully how to stop it?

---

