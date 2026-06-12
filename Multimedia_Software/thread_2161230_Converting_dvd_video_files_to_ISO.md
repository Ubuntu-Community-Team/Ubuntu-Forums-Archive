---
title: "Converting dvd video files to ISO"
date: 2013-07-09
forum: Multimedia Software
---

### Post by pikman on 2013-07-09
I have converted a few avi files to dvd format, (audio/video sub folders), and am looking for the best software to convert it to iso format.

---

### Post by GrouchyGaijin on 2013-07-09
How about from the command line run
```

mkisofs -dvd-video -o dvd.iso dvd/

```

---

### Post by pikman on 2013-07-09
I'm looking for more in the lines of a program. Easier that way. still learning terminal. :)

---

### Post by GrouchyGaijin on 2013-07-09
Well, this isn't what you are looking for then, but you might want to give it a try:

[http://www.davidgrant.ca/create_iso_and_dvd_video_ts_folder_linux](http://www.davidgrant.ca/create_iso_and_dvd_video_ts_folder_linux)

Or here are my notes on going from a raw video file to DVD:

```


1. Convert videos to proper mpeg format.


./ffmpeg -i video_file -aspect 4:3 -target pal-dvd dvd.mpg


2. Add the mpeg to the DVD project using dvdauthor - add multiple files after each file name


dvdauthor -o dvd/ -t dvd.mpg




3. Make .iso file


mkisofs -dvd-video -o dvd.iso dvd/


4. Burn ISO


growisofs -speed=2 -dvd-compat -Z /dev/dvdrw=dvd.iso




```

I burn at -speed=2 because my laptop is old, with 2 gigs of ram and I know I won't get an error at this speed.
You can probably go faster.

---

