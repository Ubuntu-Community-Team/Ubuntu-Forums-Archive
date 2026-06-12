---
title: "Audio Panel &amp; other tips&amp;tricks"
date: 2010-05-06
forum: Mythbuntu
---

### Post by K4rn4K on 2010-05-06
Hi all,

I'm new in Mythbuntu, I have some problem with my audio. When I have installed Ubuntu LL I went in the audio panel to change the audio configuration, and after this thing the audio worked.

Now in in Mythbuntu, how can I change the audio configuration ?


Also, can I have some tips&tricks in Mythbuntu ? For example where is the Ubuntu 
Software Center ? I find only the Sinaptic Center and Update Center.

Also again, in the Ubuntu LL version there are various panel for the system, in Mythbuntu there aren't. I understand the reason, but I like very much these panel, how can I install it ?

Thanks to all.

---

### Post by K4rn4K on 2010-05-07
anybody can help me ?

---

### Post by larsolav on 2010-05-07
I think that one reason that Mythbuntu does not include the sound setting panels you see in "normal" Ubuntu installations is that those applications may rely on Pulse audio. See for example [http://ubuntuforums.org/showthread.php?t=1473951](http://ubuntuforums.org/showthread.php?t=1473951). Pulse does not play well with MythTV.
What are you trying to do with the audio? Digital or analog? We can probably get your sound working if you tell us what you want to do. 

In a terminal, type
```
alsamixer
```
here you can unmute your sound options

also give the result from typing in a terminal:
```
aplay -l
```

---

