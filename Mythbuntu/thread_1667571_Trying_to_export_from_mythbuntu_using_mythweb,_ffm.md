---
title: "Trying to export from mythbuntu using mythweb, ffmpeg"
date: 2011-01-15
forum: Mythbuntu
---

### Post by vancheese on 2011-01-15
Hi people

I've a nice functioning lucid mythbuntu (0.23+fixes setup using a  PVR250. I've very happy with the whole setup but I would like to export some of the recording to other formats. My first problem is that I can't find any nuv recordings - my system seems to record in the pure mpg format(It is understandable as the Tv card can encode this video). My question is there a way to make mythweb show what the real filename of the recording is?

I am quite happy to use ffmpeg to convert videos but I dont want to search all my fiels to see which on correlated to the mpg of choice.

Thanks for your help

Andy

---

### Post by BicyclerBoy on 2011-01-15
DVB tuner cards output mpeg2-ts container/files.

The video capture cards (for STBs) use the above.
The video format can be MPEG-2 or MPEG-4 (HD).

The dvb files use MPEG-4/10 H264AVC video & AAC &/or AC3 audio.

To find the real filename just browse the "Watch recordings" & hit <i> key twice.
Scroll down & the name is shown.

The naming convention is quite straight forward..

Ubuntu repos ffmpeg version may not up to the task..

---

### Post by Archmage on 2011-01-15
I would suggesting an user-job for this. It must be enter in the mythbackend-setup up acording to this:

[http://www.mythtv.org/wiki/User_job](http://www.mythtv.org/wiki/User_job)

E.g. an basic thing that you could enter there would be:

```
cp %DIR%/%FILE% /path/to/output-dir/%TITLE% \-
\%PROGSTARTISO%.mpg
```

(Keep in mind that the user mythtv must have acces to the output-dir folder.)

This would simply copy the mpg-file to an different location and rename it to Title + Starttime. Change it your encoder and parameter and you are nearly there.

There is a problem with the titles, if there are blank characters in it.

---

