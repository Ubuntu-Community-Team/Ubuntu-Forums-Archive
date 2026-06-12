---
title: "Multithreaded Video Encoding"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by VincentVX73 on 2007-06-19
I've been searching around for a good video encoding program and I found Avidemux.  It works great but from what I can tell it does not support multithreaded processing.  Since I have a quad core chip, I'd really like to take advantage of all the cores to reduce encoding time.  I'm primarily converting divx and xvid files to mpegs for burning to dvd.  Can anyone suggest a good program?

---

### Post by Major_Kong on 2007-06-20
Mencoder can do that, but you'll  have to get dirty and use the command line.

---

### Post by VincentVX73 on 2007-06-21
Thanks, I'll give mencoder a try, and don't worry, the command line doesn't scare me! Besides, I'm assuming it should be fairly easy to find a guide for mencoder.

---

### Post by finite9 on 2007-06-21
```
ffmpeg -i infile.xvid.avi -threads 4 -mbd rd -flags +trell -cmp 2 -subcmp 2 -g 100 -pass 1/2 -target pal-dvd /tmp/outfile.mpg
```

ffmpeg is better (ie easier) for converting to mpeg.  threads=x sets threads for multicore.  do not set to auto.

Mencoder is best for encoding x264 or xvid...yes it can do most anything, but in case of mmpeg i find it easier to use...less options.  here is a mencoder example using threads=auto...

```
mencoder $infile -o /tmp/"$infile2"h264 \
-ovc x264 -vf harddup -of rawvideo \
-x264encopts subq=6:partitions=all:me=umh:bitrate=3000:frameref=5:threads=auto:pass=1 \
-nosound
```

---

### Post by david_2001 on 2007-06-21
Avidemux 2.3 - available in feisty - supports multi-threaded encoding (Edit | Preferences | MultiThread).

---

### Post by VincentVX73 on 2007-06-22
oh sweet! that's awesome news about avidemux!  that was always my first choice for encoding anyway.  thanks!

---

### Post by Vivaldi Gloria on 2008-02-17
Someone said in Cowon D2 forums:

"mencoder (the Ubuntu version) is compiled with a libxvid version that does not support multithreaded encoding"

and my results confirm this. I have a quadcore and if I increase the threads to 4 in avidemux then the processor usage does NOT increase. 

Am I missing something?

Does anybody know how to do multithreaded encoding?

---

### Post by Rizla on 2008-02-28
**This post could be related to an Ubuntu bug filed at**: rizla [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Vivaldi Gloria said:**
> Someone said in Cowon D2 forums:

"mencoder (the Ubuntu version) is compiled with a libxvid version that does not support multithreaded encoding"

and my results confirm this. I have a quadcore and if I increase the threads to 4 in avidemux then the processor usage does NOT increase. 

Am I missing something?

Does anybody know how to do multithreaded encoding?

bump.  In the same boat.. i'm looking for x264 encoding though (from what i've read mencoder is the way to go..)  I wish someone had a thorough guide for creating DVD quality rips using x264

---

