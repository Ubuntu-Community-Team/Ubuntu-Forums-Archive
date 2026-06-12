---
title: "problem with playing/shrinking a DVD"
date: 2007-01-09
forum: Multimedia &amp; Video
---

### Post by foxy123 on 2007-01-09
I have a DVD ripped on the hard drive, which I need to shrink to DVD5 and burn. I tried k9copy, my favourite tool but it gives me an error:
```
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).

```

I tried to watch it with mplayer, which produced a similar error:
```
Playing dvd://1.
libdvdread: Couldn't find device name.
Reading disc structure, please wait...
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
Can't open VMG info!
File not found: '1'
Failed to open dvd://1.

```
I only managed to open and play it with VLC. Any idea why neither k9copy nor mplayer cannot open it? I can play and open a couple of other DVDs with them without any problem.

---

### Post by pay on 2007-01-09
You need dvd decoders.```
sudo aptitude install libdvdread3
sudo  /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install libdvdcss2
```

---

### Post by foxy123 on 2007-01-13
> **pay said:**
> You need dvd decoders.```
sudo aptitude install libdvdread3
sudo  /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install libdvdcss2
```

I have both packages installed and I can read and play other DVDs. But for some reason I can neither play nor shrink this particular DVD.

---

