---
title: "Cannot play audio cd in Hardy"
date: 2009-01-26
forum: Multimedia Software
---

### Post by wah fun on 2009-01-26
I cannot get ubuntu 8.04 (I installed 8.10 - same problem) to play audio cd. I have installed all the codecs (w32, libdvdcss2, libdvdread,etc) I know of and even installed vlc - no avail. Vlc plays dvd movies with sound very well. I have searched and have tried numerous suggestions and nothing has worked yet. I have also re-installed ubuntu. So, I turn to those of you who have been able to play audio cd's for help. I have tried several other distributions and this seems to be a common problem with linux systems. I hope someone can help me resolve this issue. I would really like to move ubuntu onto my production desktop machine but can't do that until I am sure everything works.

Looking forward to getting some help.

My system is a Dell 531, 2 Gig ram, AMD Athlon Dual core running at 2 Ghz.

---

### Post by Linuxdork on 2009-01-26
By chance have you tried this: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) ?

---

### Post by wah fun on 2009-01-28
Thank you for the suggestion. 
Yes, I have already tried that along with numerous other "so called fixes" and nothing! If dvd movies will play with sound, it would seem that playing an audio cd would follow without any problems.

This is the type of issue that prevents many from making the complete switch away from that "other" operating system.

I am not giving up however, since I have found that usually someone in the linux community has had the same problem and resolved it. So far, that is not the case, I have not found the resolution and that's why this has been so frustrating.

I love linux and the concept of FOSS but this audio cd thing, for me, is problematic and prevents me from going production with Linux.

Anyway, enough of the ranting. I will continue, for a while, to look for a solution to this problem and hope to hear from someone who can help.

---

### Post by Linuxdork on 2009-01-28
When you put a cd in what is the output of:

```
file /dev/scd0
```

---

