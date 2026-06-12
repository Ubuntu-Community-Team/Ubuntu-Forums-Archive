---
title: "kmix does not load"
date: 2009-04-30
forum: Multimedia Software
---

### Post by sagara on 2009-04-30
I have a fresh install of kubuntu jaunty.  I noticed that my taskbar **lacked a volume icon** albeit sound is working.  After reading online a bit it seems I need to run **kmix** in order to get it.

I tried running it from the command line but once the command returns I still dont get any volume icon nor do I see any error messages.

If i try to run it from the kick off app launcher, I see the kmix task in the taskbar but I never get to see the app.  Eventually the task dissapears and no kmix is actually loaded.

Running
```
ps -ef | grep kmix
```

Proves that a session of kmix is indeed running.  Any thoughts?

---

### Post by sagara on 2009-05-03
Solved the problem.  It turns out I had removed the **System Tray widget** from the panel bar.  In this widget is where the volume icon resides.

After adding the widget again, the volume icon was there.

---

### Post by holzfreiweiss on 2011-07-08
for me it did not work. (not even adding the widget back)
The solution was **synaptic: mark "kmix" for reinstallation** + apply. Then everything was ok.

---

