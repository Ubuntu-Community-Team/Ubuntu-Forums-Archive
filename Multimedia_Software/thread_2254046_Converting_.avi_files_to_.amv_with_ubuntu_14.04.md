---
title: "Converting .avi files to .amv with ubuntu 14.04"
date: 2014-11-24
forum: Multimedia Software
---

### Post by tim00p on 2014-11-24
[FONT=book antiqua]Hi i`ve been an avid ubuntu user on and off some a good while now and usually manage to find out what i need pretty easily thanks to the comprhensive forums however this time round i`ve hit a dead end. I`m looking to convert avi files and the like to .amv format so i can play them on the mp4 players of the household. I`ve read previously that the version of ubuntu i`m using (14.04) does not support ffmpeg but uses avconv instead but i`m struggling to find any commands to run this tool. Any help on this would be greatly appreciated.
[/FONT]

---

### Post by ron998 on 2014-11-24
> **tim00p said:**
> [FONT=book antiqua]... I`m looking to convert avi files and the like to .amv format so i can play them on the mp4 players of the household.[/FONT]


Hi
You probably need to use the patched FFmpeg "amv-codec-tools".
The windows version works OK with wine.

Check if the sample file "hole.amv" plays OK first.
From here ---> [https://code.google.com/p/amv-codec-tools/downloads/detail?name=hole.amv&can=2&q=](https://code.google.com/p/amv-codec-tools/downloads/detail?name=hole.amv&can=2&q=)

EDIT
The linux version works OK too when it's made executable -  change properties > permissions to "Allow this file to run as a  program".
:oops:

---

### Post by andrew.46 on 2014-11-25
Might be well worth your while to get a recent copy of FFmpeg which seems to produce a reasonable amv file without too many problems. Definitely not a polished effort but the following quickly cobbled together syntax (which could do with some adjustments):

```

ffmpeg -i Evanescence.My.Immortal.mp4 \
       -map_metadata -1 \
       -c:v amv -f avi -q:v 2 -vf scale="320:-16"  \
       -c:a libmp3lame -q:a 4 \
       test.amv.encode.amv

```

produced a reasonable offering (although a little overweight at 49mb) which I have placed here if you are interested:

[http://www.datafilehost.com/d/0748e671](http://www.datafilehost.com/d/0748e671)

Interesting to hear if it plays on your device, these little devices are notoriously fickle with their video and audio needs. Not sure if avconv can do something similar?

---

### Post by tim00p on 2014-11-25
> **ron998 said:**
> 

Check if the sample file "hole.amv" plays OK first.
From here ---> [https://code.google.com/p/amv-codec-tools/downloads/detail?name=hole.amv&can=2&q=](https://code.google.com/p/amv-codec-tools/downloads/detail?name=hole.amv&can=2&q=)



Tried this sample video, it played about 6 seconds and then stopped and displayed Format Error

Thanks for trying  ;)

---

### Post by tim00p on 2014-11-25
> **andrew.46 said:**
> 

```

ffmpeg -i Evanescence.My.Immortal.mp4 \
       -map_metadata -1 \
       -c:v amv -f avi -q:v 2 -vf scale="320:-16"  \
       -c:a libmp3lame -q:a 4 \
       test.amv.encode.amv

```

produced a reasonable offering (although a little overweight at 49mb) which I have placed here if you are interested:

[http://www.datafilehost.com/d/0748e671](http://www.datafilehost.com/d/0748e671)

Interesting to hear if it plays on your device, these little devices are notoriously fickle with their video and audio needs. Not sure if avconv can do something similar?


My mp4 player would not even entertain this sample :mad:   Just gave me a Format Error message and nothing else.


Thanks for the input guys

---

