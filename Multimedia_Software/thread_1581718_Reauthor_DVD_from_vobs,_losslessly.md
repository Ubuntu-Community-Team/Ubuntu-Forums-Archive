---
title: "Reauthor DVD from vobs, losslessly?"
date: 2010-09-25
forum: Multimedia Software
---

### Post by lonegroover on 2010-09-25
Hi.

I have a DVD of TV broadcasts made using a DVD recorder. I want to make a separate DVD, using just two of the 10 or 11 recordings on the original DVD.

So I've ripped the two recordings to VOBs. Is there a way to convert them to DVD-complaint MPEGs that can be passed to dvdauthor withour re-encoding,  so that the quality will remain the same? Or is there another way to reauthor a DVD using the VOBs?

Thanks for any guidance.

---

### Post by ron999 on 2010-09-25
Hi
Maybe they are already DVD-compliant.
Use a program such as MediaInfo to study the characteristics.
Then perhaps it might be necessary only to change the suffixes to mpg.

---

### Post by lonegroover on 2010-09-25
> **ron999 said:**
> Hi
Maybe they are already DVD-compliant.
Use a program such as MediaInfo to study the characteristics.
Then perhaps it might be necessary only to change the suffixes to mpg.

Hi,

No - I'm afraid that on attempting that, dvdauthor repeats the message

```
WARN: Skipping sector, waiting for first VOBU...
```

A few thousand times, then segfaults.

---

### Post by lonegroover on 2010-09-26
A bit more on this.

The vobs were extracted using (eg)

```
mplayer dvd://3 -dumpstream -dumpfile myvideo.vob
```

They can be played in myplayer, which reports:

```
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  7500.0 kbps (937.5 kbyte/s)
```

and

```
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
```

.. which ought to be DVD-compliant as far as I can tell, but I must be missing something. Files extracted from DVB broadcasts using ProjectX can be encoded quite happily, despite having essentially the same characteristics, ditto MPEGs created using transcode. What's wrong with these vobs, and how can I make them DVD-compliant losslessly?

---

### Post by lonegroover on 2010-09-26
OK. After a bit of googling and some experimentation, it seems that that in order to prepare a VOB extracted from a DVD so that it's ready to burn again, it needs to be demultiplexed, then remultiplexed. I don't know exactly why, but the following will do the job:

```
tcextract -i myvideo.vob -x mpeg2 > temp.m2v
tcextract -i myvideo.vob -a 0 -x ac3 -t vob > temp.ac3

mplex -f 8 -o fixedvob.mpg temp.m2v temp.ac3
```

.. worked for me! And I knocked up the following script (I called it 'vobfix') to save typing:

```

#!/bin/bash

vfile=$1

tcextract -i $vfile -t vob -x mpeg2 > temp$$.m2v
tcextract -i $vfile -a 0 -x ac3 -t vob > temp$$.ac3

mplex -f 8 -o dvd_${vfile/.vob/.mpg} temp$$.m2v temp$$.ac3 && rm -f temp$$.???

exit 0

```

---

