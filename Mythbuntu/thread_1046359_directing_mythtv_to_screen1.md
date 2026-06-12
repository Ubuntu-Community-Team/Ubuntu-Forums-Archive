---
title: "directing mythtv to screen1?"
date: 2009-01-21
forum: Mythbuntu
---

### Post by mathog on 2009-01-21
mythbuntu 8.10, nvidia proprietary driver.

There are two screens on the system, screen0 is the monitor at 1280 x 1024, and screen1 is TV-OUT at 640x480.  I want mythtv to come up ONLY on screen1.  (Normally there will be nothing attached for screen0, it is just there so that I can do administrative tasks if need be, and screen1 will go to a TV so that the system will work as a DVR.)  Currently mythtv comes up on screen0.  Is there some simple way to direct it to use screen1 instead?  Also, where in mythbuntu is the code which actually starts the myth frontend?  I looked in /etc/init.d and didn't see anything that looked relevant.  Is it coded into xfce somehow?

Thanks.

---

### Post by My Name on 2009-01-21
Can you set screen1 to "main screen" or something along those lines?

---

### Post by fenx7 on 2009-01-21
I used MYTHFRONTEND_OPTS="-display :0.1" in  /etc/mythtv/session-settings

This worked for me. I was troubled to find other ways.

---

### Post by mathog on 2009-01-22
> **fenx7 said:**
> I used MYTHFRONTEND_OPTS="-display :0.1" in  /etc/mythtv/session-settings

This worked for me. 

Me too.

Thanks.

---

