---
title: "Video Transcoder and Mp3 Converter?"
date: 2011-06-19
forum: Multimedia Software
---

### Post by xcommunistx on 2011-06-19
I search for a Video Transcoder (neither ''Arista'' nor ''Transmagedon'') which can Recode a Video with my OWN options (like width: 640 high: 360)! And i need also (and this is more important) an Video to Mp3 Converter ( not WinFF, because i get an Error: libmp3lame unknown  ) which i can convert many FIles at the same time, can you help me?

---

### Post by ron999 on 2011-06-19
> **xcommunistx said:**
> can you help me?
Show the output from this command:-
```
cat /etc/issue
```

---

### Post by xcommunistx on 2011-06-19
```
Ubuntu 11.04 \n \l

```

So?

---

### Post by andrew.46 on 2011-06-19
> **xcommunistx said:**
> [...] not WinFF, because i get an Error: libmp3lame unknown [...] 

Have a look here to reclaim libmp3lame:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by xcommunistx on 2011-06-20
[QUOTE]Have a look here to reclaim libmp3lame:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283[]("http://ubuntuforums.org/showthread.php?t=1117283")/QUOTE]
 
But this is for Maverick, Lucid and Karmic Koala, not for my Natty Narwahl...
Anyway, i tried it and it deletes some codecs which i need like AAC Encoding, Libavcodec50...
It made also last time my System Fail (which is nearly unpossible for Ubuntu)

---

### Post by xcommunistx on 2011-06-20
Oh, sorry, i looked again and it works, Thank you Soooo Much!
I searched for this like 3 Months and now i got an Simple answer which actually solved my problem!
I can't also call this thread SOLVED because i still search for a Transcoder with Own High-Width Option!

---

### Post by FakeOutdoorsman on 2011-06-20
> **xcommunistx said:**
> I search for a Video Transcoder (neither ''Arista'' nor ''Transmagedon'') which can Recode a Video with my OWN options (like width: 640 high: 360)!
FFmpeg is does this. If you tell me any requirements and what output format(s) you want I can give you a basic example to start with.

> **xcommunistx said:**
> And i need also (and this is more important) an Video to Mp3 Converter...which i can convert many FIles at the same time, can you help me?
You can use a bash "for loop". This example converts all mkv files to mp3:
```
for input in *.mkv; do ffmpeg -i "$input" -acodec libmp3lame -aq 5 "${input%.mkv}.mp3"; done
```

> **xcommunistx said:**
> But this is for Maverick, Lucid and Karmic Koala, not for my Natty Narwahl...
Yeah, I need to update that guide.

---

### Post by andrew.46 on 2011-06-20
> **xcommunistx said:**
> Oh, sorry, i looked again and it works, Thank you Soooo Much!
I searched for this like 3 Months and now i got an Simple answer which actually solved my problem!

Thanks to FakeOutdoorsman who took the time to provide this very useful guide :).

---

### Post by anur.bhargav on 2011-09-04
> **FakeOutdoorsman said:**
> FFmpeg is does this. If you tell me any requirements and what output format(s) you want I can give you a basic example to start with.


You can use a bash "for loop". This example converts all mkv files to mp3:
```
for input in *.mkv; do ffmpeg -i "$input" -acodec libmp3lame -aq 5 "${input%.mkv}.mp3"; done
```


Yeah, I need to update that guide.

Ur the King..:P:KS:popcorn:

---

