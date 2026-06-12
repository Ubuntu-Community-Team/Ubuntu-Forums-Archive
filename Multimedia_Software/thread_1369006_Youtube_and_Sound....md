---
title: "Youtube and Sound..."
date: 2009-12-31
forum: Multimedia Software
---

### Post by Taeyeon on 2009-12-31
Well, this happens to me quite a lot...
After surfing on the Internet, but mostly with Youtube for a period of time, usually 20-30 minutes my sound just randomly stops.
Sound comes out everywhere else, like the music player etc. etc.
Also, If I turn on Movie Player and play something and then I turn on Youtube then Youtube sound doesn't work.

---

### Post by Jenked on 2010-01-23
This happens to me too. The only solution I can find is to restart Ubuntu which obviously is not ideal.

Also, when this happens I have tried closing and reopening Firefox, but when trying to open it again it tells me the firefox is still running and to close its process before launching it again, except I have no idea how to close processes in Linux. Any (idiot proof) help would be great.

---

### Post by corncob on 2010-01-23
> **Jenked said:**
> This happens to me too. The only solution I can find is to restart Ubuntu which obviously is not ideal.

Also, when this happens I have tried closing and reopening Firefox, but when trying to open it again it tells me the firefox is still running and to close its process before launching it again, except I have no idea how to close processes in Linux. Any (idiot proof) help would be great.

I don't know what to tell you about youtube but to kill a process go to Applications > Accessories > Terminal and type in
```
top
```
Find out its process identification number (PID) and then open a second terminal (or hit [ALT][F2]) and enter
```
sudo kill 2980
```
Don't use that 2980 though.  Use your own.  Its my Firefox PID at the moment which I suspect is different for everybody.  I'm just using it as an example.

---

