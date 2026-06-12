---
title: "DVD play back problems"
date: 2008-12-31
forum: Multimedia Software
---

### Post by b3n0 on 2008-12-31
It seems so long ago since I did this on my laptop. Now that I've installed interpid on my desktop, I'm trying to get DVD playback working. I'm failing to remember to process I followed last time.
By memory (and google) I need to install the dvd codecs and then. Run this in terminal.
```
sudo apt-get install ubuntu-restricted-extras
```
DVD play back is still not working....
Have I missed a step, its driving me nuts.

---

### Post by mc4man on 2009-01-01
Assuming you have libdvdread3 and libdvdnav4 installed then probably at this point just libdvdcss2

Direct download and install from here

[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

or run (same thing

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

If you have a xine engine player make sure you also have

libxine1-ffmpeg

---

### Post by 2hot6ft2 on 2009-01-01
You still need libdvdcss2 which you can get from here [http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

---

### Post by b3n0 on 2009-01-01
I honestly could marry this forum right now.
Thanks heaps... +1s for all!

---

