---
title: "Cannot play back encrypted DVDs AT ALL"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by DevilInPgh on 2008-03-31
I cannot play encrypted DVDs at all, even with libdvdcss2 and associated packages installed.  Can someone help me?

---

### Post by DevilInPgh on 2008-04-01
OK, now I have a new question.  It turns out that I can play encrypted DVDs in the DVD+/-RW drive I just bought, but not in my built-in DVD-ROM.  Why is that?

---

### Post by mc4man on 2008-04-01
If the built-in drive hasn't had a dvd region set it won't play commercial disks> Install regionset> run sudo regionset from terminal and if no region is set set it to yours.  N. America - 1, europe - 2 ect. 
Ck. here if unclear
[http://ubuntuforums.org/showthread.php?t=712164&highlight=regionset](http://ubuntuforums.org/showthread.php?t=712164&highlight=regionset)

what an unset drive will show
```
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF
```

---

