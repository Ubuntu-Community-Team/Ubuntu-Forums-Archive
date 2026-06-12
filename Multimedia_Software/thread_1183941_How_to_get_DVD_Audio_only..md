---
title: "How to get DVD Audio only."
date: 2009-06-10
forum: Multimedia Software
---

### Post by dunbrokin on 2009-06-10
Is there a way for me to only rip the audio portion of a DVD?

---

### Post by dunbrokin on 2009-06-12
Bump!

---

### Post by jerrrys on 2009-06-12
i don't do that, but if i wanted to, i would go here...

[http://www.google.com/search?q=rip+the+audio+portion+of+a+DVD+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=rip+the+audio+portion+of+a+DVD+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by andrew.46 on 2009-06-12
Hi dunbrokin,

> **dunbrokin said:**
> Is there a way for me to only rip the audio portion of a DVD?

This can be done with Transcode but I will freely acknowledge that this program is for commandline fans only :-). I use:

```
andrew@skamandros~$ transcode --version
transcode v1.1.2 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
```

The DVD import module is what you are after and for example if you wished to rip the first audio track from Title 1, chapter 3, angle 1 and subsequently transcode to mp3 you would use:

```
transcode -x null,dvd -i /dev/dvd -T 1,3,1 -a 0 -y null,tcaud \
--lame_preset standard -E 44100,16,2 -m $HOME/Desktop/output.mp3
```

This syntax has worked flawlessly for me for some time. Just be a little aware of version changes with Transcode as the command line has been in flux just recently.

All the best,

Andrew

---

### Post by dunbrokin on 2009-06-16
Thanks, that worked a treat....

---

### Post by raymondvillain on 2009-07-15
If I open a terminal and type:

man transcode

I get 2600+ lines of manual.  Transcode is a formidable looking tool, for a beginner.

Is there an easier way?  Will VLC do it (rip the audio only from a DVD)?

---

