---
title: "No Sound except for login/logout"
date: 2010-01-19
forum: Multimedia Software
---

### Post by daboo911 on 2010-01-19
I have a fresh install of kubuntu 9.10 which only seems to play the start up and shut down noise.  Audio from games, flash videos, and other sources do not appear to work.  

I've been searching around, and while there seem to be a few threads on this topic, none have solutions.  Where should I begin?

---

### Post by daboo911 on 2010-01-19
Of course, it would be something obvious.  I had actually checked the alsamixer before posting this, and it looked fine, but apparently the issue is that the digital output was not muted and the analog output was.  Turning up the analog output (labeled IEC958 in alsamixer) gives me audio in all applications.  Hope this helps someone.

---

