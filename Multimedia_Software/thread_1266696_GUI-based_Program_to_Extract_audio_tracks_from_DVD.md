---
title: "GUI-based Program to Extract audio tracks from DVD"
date: 2009-09-14
forum: Multimedia Software
---

### Post by kendoori on 2009-09-14
I have instructional DVDs that I would like to extra the audio tracks for practice purposes. I installed Handbrake, DVDRip, and OGMrip, but it doesn't appear that you can extra the audio only cleanly. Anyone with any experience on this?

---

### Post by andrew.46 on 2009-09-15
Hi kendoori,

> **kendoori said:**
> I have instructional DVDs that I would like to extra the audio tracks for practice purposes. I installed Handbrake, DVDRip, and OGMrip, but it doesn't appear that you can extra the audio only cleanly. Anyone with any experience on this?

I believe that the best utility or this purpose may well *not* be gui based. I refer to Transcode which has a nice dvd import module that would be exactly what you need.

An example that I have used myself is the following that extracts the James Brown cameo from the Blues Brothers DVD and converts it to ogg:

```
transcode -x dvd -i /dev/dvd -T 1,3,1 -a 0 -y null,ogg \
-b 192 -E 44100,16,2 -o $HOME/Desktop/james_brown.ogg
```

It is not as painful as it looks:

[LIST=1]
[*]**-x dvd:** Use the dvd import module
[*]**-i /dev/dvd:** Input is my dvd drive
[*]**-T 1,3,1:** track 1, chapter 3, angle 1
[*]**-a 0:** audio track 0  
[*]**-y null,ogg:** Don't export video, export audio using the ogg module
[*]**-b 192:** audio bitrate
[*]**-E 44100,16,2:** Audio output sample-rate, bits per sample, channels
[*]**-o $HOME/Desktop/james_brown.ogg:** Output file
[/LIST]

It does not exactly flow naturally from the keyboard but it works well and something similar would work well for your needs.

Andrew

---

