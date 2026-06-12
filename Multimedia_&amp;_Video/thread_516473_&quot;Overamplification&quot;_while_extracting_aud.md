---
title: "&quot;Overamplification&quot; while extracting audio form flash file"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by schlesix on 2007-08-03
Hi,

I'm not very familiar with sound things an have a problem while extracting audio from a flash file.

I've downloaded this flash file from youtube [http://www.youtube.com/watch?v=dySZpw4JJC4]("http://www.youtube.com/watch?v=dySZpw4JJC4") and converted it to a wav file with mplayer:

```
mplayer Nu2kjCrIQv8.flv -novideo -ao pcm:waveheader -ao pcm:file=Gregorian_Sound_of_Silence.wav
```

The encoding as a wav file did work, but when I play it, it sound "overamplified" from 2:06min. When I play the flash with the flash-plugin in firefox, it sounds "regular".

Can anybody tell me, how to "fix" this? Is there an alternative software to extract the audio out of a flash file?

Thanks,
Thomas

---

### Post by schlesix on 2007-08-03
After fiddling around with vlc's audio export and getting the same result, I've found out, that it's a hardware problem. My earphones are causing this problem.

So I've wasted some hours with this problem. *Sigh*

---

