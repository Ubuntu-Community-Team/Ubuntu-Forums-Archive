---
title: "All of my video is going fast, and has no sound."
date: 2013-07-17
forum: Multimedia Software
---

### Post by Kaninepete on 2013-07-17
Movie Player, Blender, Youtube and Vimeo on chorme.
Everything I try to play on my system has this issue.

The videos play very fast, and have no sound at all.
I just did an update, can I undo it?
Should I?

Any advice or guidence would be greatly appreciated!

---

### Post by Kaninepete on 2013-07-17
UPDATE:
Even DVDs have the problem.

No idea what to do.

---

### Post by Yellow Pasque on 2013-07-18
> I just did an update, can I undo it?[
Do you know what was included in the update? Kernel update?
You can look at the end of the dpkg log if you're not sure:
```
tail -n 50 dpkg.log
```

You should grab alsa info while you're at it: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

