---
title: "Need help with mencoder and audio"
date: 2008-05-29
forum: Multimedia Software
---

### Post by jakev383 on 2008-05-29
I have a bunch of VOB files that I ripped from a DVD to my HD of old TV shows.  I want to recode them to take up less disk space, and have successfully done so using this command:
```

nice -n 19 mencoder Episode\ 6\ -\ Past\ Sim.vob -ovc xvid -oac mp3lame -xvidencopts bitrate=2000 -o xvid-2000.avi

```
The problem is that it gives me the Spanish audio track instead of the English one.  When I just watch the VOB file I get the audio in English, but if I recode it I get the audio in Spanish.
Can someone tell me where I went wrong?  I like the size compression - a 2G file is reduced to 680M and the quality stays as well.
Thanks in advance!

---

### Post by recrispi on 2008-05-29
I'm not sure, but maybe using the "-aid #" option, where # is the number of the audio track.
I hope that helps.

---

### Post by andrew.46 on 2008-05-30
Hi:

> **jakev383 said:**
> 
The problem is that it gives me the Spanish audio track instead of the English one.  When I just watch the VOB file I get the audio in English, but if I recode it I get the audio in Spanish.


You could try adding 

```
-alang en
```

to your encoding string. BTW you might be able to drop your bitrate a little and not notice any degradation of the image.

        Andrew.

---

### Post by disturbedite on 2008-05-30
i recommend ogg theora for video & ogg for audio.  there are programs to do specifically this in the repo.

---

### Post by jakev383 on 2008-05-30
> **andrew.46 said:**
> Hi:



You could try adding 

```
-alang en
```

to your encoding string. BTW you might be able to drop your bitrate a little and not notice any degradation of the image.

        Andrew.


Thanks, but the one didn't work.
I had the bitrate at 1000 and it didn't look that hot to me. I just jumped to 2000 instead of trying something like 1500 because I was impatient. Once I get the audio thing worked out I'll play with the bitrates some.  I'm trying the "-aid 1" method now. Wish me luck!

---

### Post by jakev383 on 2008-05-30
This ended up working for me:
```

nice -n 19 mencoder Episode\ 6\ -\ Past\ Sim.vob -ovc xvid -oac mp3lame -aid 128 -xvidencopts bitrate=2000 -o xvid-2000.avi

```
Thanks!

---

