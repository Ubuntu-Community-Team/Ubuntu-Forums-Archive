---
title: "Logitech cam works in cheese but not skype"
date: 2012-03-30
forum: Multimedia Software
---

### Post by Bob Denzel on 2012-03-30
Hi, I am a newbie to kubuntu but like what I have seen so far. I have  11.10 32bit installed. I have managed to get everything working "except"  my webcam in skyp. It's a Logitech quick communiate stx. Strange thing  is it works in cheese, but in skype in options it shows a webcam but  when I press test nothing happens, screen stays black! I have searched  the forums but no topics seem to match my problem. Thankfull for any  assistance.:D

Cheers
Bob

---

### Post by mörgæs on 2012-03-30
Does this work?

```
env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

More info here:
[http://ubuntuforums.org/showthread.php?t=1899379](http://ubuntuforums.org/showthread.php?t=1899379)

---

### Post by Bob Denzel on 2012-03-30
Yep that worked thanks :D

Is that now a permanent fix? 
Ah I see only video when I give the command in the terminal. 

Cheers
Bob

---

### Post by mörgæs on 2012-03-30
It is not permanent, unfortunately. Maybe if you give it a push in Launchpad it will be.

---

