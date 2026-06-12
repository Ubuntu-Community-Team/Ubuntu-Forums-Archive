---
title: "F-Spot disappears - 9.10"
date: 2010-01-10
forum: Multimedia Software
---

### Post by azurehi on 2010-01-10
Whenever I access F-Spot, it appears and the, almost immediately, disappears.  Any suggestions?

---

### Post by howefield on 2010-01-10
Try running it from a terminal (Applications > Accessories > Terminal). Might give you some sort of clue where to start from the error.

```
f-spot
```

---

### Post by azurehi on 2010-01-10
after running f-spot in terminal, this message was at the end of the long output:
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.

---

### Post by howefield on 2010-01-10
Might be this bug

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/194864](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/194864)

---

### Post by azurehi on 2010-01-10
Thanks, I believe the link describes the bug.  I, do not, however, know what to do after reading the suggestions.  Maybe I will just reinstall 9.10.

---

### Post by TnTMike on 2010-01-23
There have been a number of posts about this problem. The same thing was happening to me, try thread [http://ubuntuforums.org/showthread.php?t=1307641&highlight=f-spot]("http://ubuntuforums.org/showthread.php?t=1307641&highlight=f-spot") suggests a fix that worked for me as well as a few others.
I simply changed my desktop theme to human from new wave.

---

