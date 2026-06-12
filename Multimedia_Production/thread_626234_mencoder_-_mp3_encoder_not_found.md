---
title: "mencoder - mp3 encoder not found"
date: 2007-11-28
forum: Multimedia Production
---

### Post by skynexus on 2007-11-28
I have tried to convert a macromedia flash video to mpeg4 using mencoder in Gutsy. I have used the following command:

```
mencoder input.flv -ofps 15 -vf scale=300:-2 -oac lavc -ovc lavc -lavcopts vcodec=msmpeg4v2:acodec=mp3:abitrate=64 -o output.avi

```

This worked fine in Feisty, but in Gutsy it now fails with the following error message:

```
Audio LAVC, couldn't find encoder for codec mp3.
```

Yes, I do have lame installed on my system. I have also checked the forum for anything similar without success. The closest thing to this problem I was able to find on the web was this:

[http://lists.freshrpms.net/pipermail/freshrpms-list/2007-October/014939.html]("http://lists.freshrpms.net/pipermail/freshrpms-list/2007-October/014939.html")

According to the linked article, something appears to have changed in mplayer/mencoder to cause the exact same problem that I am seeing right now. Is anyone working on a fix? Am I the only one seeing this on Ubuntu?

---

### Post by Creative2 on 2007-11-29
well i know something is changed .... -.-' but i have still mencoder 2006 so...i think you have mencoder 2007. ..

you are using lavc codec to encode your movie, so that codec" is a part of ffmpeg"   ....well explained this 

1 install mencoder and ffmpeg from medibuntu repo ... i hope what i mean 
2 try again 
3 if doesnt work you probably must replace mp3 with libmp3lame 

see here [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html)

---

### Post by eye208 on 2007-11-29
> **Creative2 said:**
> 1 install mencoder and ffmpeg from medibuntu repo ... i hope what i mean 
2 try again 
3 if doesnt work you probably must replace mp3 with libmp3lame
Why not start with step 3?

---

### Post by Creative2 on 2007-11-29
-.-'

a i don't know what kind of mencoder \ ffmpeg he has

b i don't remember very well the issue of lavc codec because if i was him i just use mp3lame codec istead lavc and then lilibmp3lame...and then there is a problem, in fact  seems mencoder use a library of ffmpeg which use libcodec instead ffmpeg (medibuntu repo) can use instead of  libmp3lame  mp3

c the most of the time people have not medibuntu repo turned on....and they say command line doen't work...until they turn on medibuntu repo...

---

### Post by skynexus on 2007-11-29
Thank you very much for your help! Indeed, I replaced mp3 with libmp3lame and that solved the problem. Apparently there was a change to the audio codec name and I didn't realize it. It would be very helpful if the mencoder programmers could get into the habit of providing informative error messages when they deliberately change names in this manner (I assume it is their doing).

Interestingly, I now discovered new problems with the resulting video. It turns out that when skipping forward or backward, the audio automatically resets to the beginning of the track (while the video will not). After trying several different video codecs and videos to confirm the problem, I finally decided to use LAME with the mp3lame option instead.

```
mencoder input.flv -ofps 15 -vf scale=300:-2 -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4 -o output.avi
```

This helped, and when skipping forward or backward in the video, the audio will also skip accordingly. Though I am very close to a solution, a final problem remains - the video and audio are out of sync. I believe the video is going faster than the audio, or audio going slower than the video, or they are not starting at the same time. I am not sure yet, will need to look into this further. I should also point out that I have had the Medibuntu repository activated all along; the lame package is version 3.97-0.0 (gutsy repository) and ffmpeg is version 3:0.cvs20070307-5ubuntu4+medibuntu2.

---

### Post by Creative2 on 2007-11-29
problem with syncro audio video....
solution
while encoding =
```
mencoder -idx  input.flv -ofps 15 -vf scale=300:-2 -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4 -o output.avi
```

after encoding
```

mencoder INPUT -ovc copy -oac copy -forceidx -o OUTPUT
```

---

