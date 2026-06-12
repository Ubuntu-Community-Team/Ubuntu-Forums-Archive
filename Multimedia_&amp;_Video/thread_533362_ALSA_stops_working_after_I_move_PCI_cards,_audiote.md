---
title: "ALSA stops working after I move PCI cards, audiotestsrc wave=sine freq=512 ! audiocon"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by tlevine on 2007-08-23
ALSA stopped working after I moved some PCI cards around, among other things.  I get this error when I test ALSA devices in the Sound window in Preferences:> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.OSS still works.  Does anyone have any ideas of what's wrong?

I fixed it by removing ~/.asoundrc*.

---

### Post by mynis on 2007-10-14
> I fixed it by removing ~/.asoundrc*. 

explain this please? i'm a linux newb. perhaps this can fix the problem im having

---

### Post by shazkho on 2008-07-08
I think he means this command:

```
$ sudo rm ~/.asoundrc*
```

---

