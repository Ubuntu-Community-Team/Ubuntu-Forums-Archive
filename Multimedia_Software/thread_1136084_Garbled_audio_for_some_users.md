---
title: "Garbled audio for some users"
date: 2009-04-24
forum: Multimedia Software
---

### Post by sstakes1 on 2009-04-24
OS: Ubuntu Jaunty Jackelope x86 Desktop.
I have a problem when I run supertuxkart. The audio is garbled and running it in the console I see 
[FONT="Courier New"]WARNING: Music not playing when it should be. Source state: 4116[/FONT] 
repeated many times. However, this problem only happens for the accounts I set up for my kids. My primary account does not have this problem.

groups for my kids shows:
kidname audio

Other programs like gcompris etc. have no problems when running from my kids account. 

Any help will be appreciated.

Thanks

Update: All user accounts suffer from the same issue which happens intermittently. It just was coincidental that it seemed to happen when logged in from the kids account as opposed to mine. I also found this [thread]("http://ubuntuforums.org/showthread.php?p=7070087") that may be relevant

---

### Post by sstakes1 on 2009-04-25
Okay here is a possible solution that works for me. I created a file named 
**.alsoftrc** whose contents are listed below

```
drivers = oss
```

---

