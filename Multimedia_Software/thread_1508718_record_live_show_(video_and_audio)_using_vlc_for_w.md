---
title: "record live show (video and audio) using vlc for website"
date: 2010-06-13
forum: Multimedia Software
---

### Post by superfrogman94 on 2010-06-13
i am wondering how i would do this using VLC (i want both video and audio to be recored),
i see this RTSP Protocol people use but no idea how to use this for a website thats going to have a live show on.

By the way the thing i want to record will be here [http://e3.nintendo.com]("http://e3.nintendo.com/").

Would it be rtsp://e3.nintendo.com?
hopefully thats a link that can be recorded...right?

the reason i want to record this is because i got a test i have to take... i gotta stay for like 2 hours... :(

using Ubuntu 10.04 64 Bit

EDIT: Also does recording work when its not on yet, or already over? i want to start recording before i leave and stop when i get home. 

please help

---

### Post by superfrogman94 on 2010-06-13
BUMP

does using http ([http://e3.nintendo.com/](http://e3.nintendo.com/)) work for streaming on vlc?

---

### Post by superfrogman94 on 2010-06-13
BUMP

sorry i guess i am a little impatient...

---

### Post by superfrogman94 on 2010-06-13
help?

---

### Post by superfrogman94 on 2010-06-14
guys...

i just want to know how to use rtsp so i can record. can anyone please tell me how to do this? (or if rtsp://e3.nintendo.com is correct?) or should i just use http and it will work? :confused:

please help :(

i need to know before it starts tomorrow!

---

### Post by superfrogman94 on 2010-06-14
well i think ill just use http and be able to figure it out and record it... oh well

---

### Post by mocha on 2010-06-15
Do a web search for a program called "msdl", you can also try mplayer like this:

```
mplayer -noframedrop -cache 1024 -dumpstream "rtsp://www.url.to.stream.file/etc/etc" -dumpfile /home/user/file.xxx
```

```
msdl -o output.xxx  rtsp://<URL>
```  Double check my syntax on this.

---

