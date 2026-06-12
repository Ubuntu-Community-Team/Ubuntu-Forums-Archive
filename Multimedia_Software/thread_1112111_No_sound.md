---
title: "No sound???"
date: 2009-03-31
forum: Multimedia Software
---

### Post by Ratscallion on 2009-03-31
Hi, I am using Ubuntu 8.10 on a HP laptop, I have autodetect selected in the Multimedia Systems Selector. When I try and play ANY sound, including Twitter updates and YouTube videos. It just comes up with some error message 
> Autodetect: Failed to connect to the stream: Invalid argument.Please help me here, thanks.

---

### Post by wolfen69 on 2009-03-31
go to system>preferences>sound and switch everything from auto detect to alsa. hope it helps.

---

### Post by Ratscallion on 2009-03-31
> **wolfen69 said:**
> go to system>preferences>sound and switch everything from auto detect to alsa. hope it helps.
On output, I have two Alsa's, which one do I want, the analog or digital versions?

---

### Post by Ratscallion on 2009-03-31
Neither of the two worked! When I press the test button I get this:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

---

### Post by markbuntu on 2009-03-31
Go here to get that all fixed up


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

