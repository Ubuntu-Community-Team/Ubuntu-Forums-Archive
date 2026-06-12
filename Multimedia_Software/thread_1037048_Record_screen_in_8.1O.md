---
title: "Record screen in 8.1O ?"
date: 2009-01-11
forum: Multimedia Software
---

### Post by Kiro42 on 2009-01-11
Hi

I've tried 3 screen recording softwares : recordMyDesktop, Xvidcap and Istanbul, but none work.

RecordMyDesktop crashes with a 768 error, and says it can't access my sound card. Sometimes it works, but when I stop recording, it tries to encode the video but is stuck at 0%.
Xvidcap crashes when I start recording.
And Istanbul freeze when I stop the recording.


And I've searched on google for 2 days, but the only thing I found is that a lot of people has those problems...

So is there a program that works on 8.10 ? Or do you know how to resolve the problems ?

Thanks in advance !

---

### Post by Kiro42 on 2009-01-12
Bump.

I really need help =)

---

### Post by cotcot on 2009-01-12
Maybe taksi. But this works only under windows, so maybe with wine.
By me the apps you mention work. I only do not get them above 10 fps.

---

### Post by Meelis on 2009-02-19
> **Kiro42 said:**
> Hi

I've tried 3 screen recording softwares : recordMyDesktop, Xvidcap and Istanbul, but none work.

RecordMyDesktop crashes with a 768 error, and says it can't access my sound card. Sometimes it works, but when I stop recording, it tries to encode the video but is stuck at 0%.
Xvidcap crashes when I start recording.
And Istanbul freeze when I stop the recording.


And I've searched on google for 2 days, but the only thing I found is that a lot of people has those problems...

So is there a program that works on 8.10 ? Or do you know how to resolve the problems ?

Thanks in advance !

Hi

Error 768 might be if you use jack audio (unselect it) because it refuses to record video if it can't record audio.

recordMyDesktop doesn't work with ATI video card**s (no --full**-shots even then poor fps).

Maybe istanbul starts encoding un/fast-compressed video. Is there HDD activity.

"stuck at 0%" Most times linux dont know how to calculate the %. it ends if it ends.

---

### Post by markbuntu on 2009-02-19
There is a thread here about using recordMyDesktop with jack


[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

---

