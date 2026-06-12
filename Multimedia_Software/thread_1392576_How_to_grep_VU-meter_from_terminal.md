---
title: "How to grep VU-meter from terminal?"
date: 2010-01-28
forum: Multimedia Software
---

### Post by produnis on 2010-01-28
Hi folks,

Question:  Is there any way to get information about whether something is currently played via the speakers?

Is there an app that "scans" the VU-meter (e.g. pavumeter) in a terminal and prints out any information about the current "sound-volume" that goes out?


I'd like to create a script that prevents my Ubuntu to suspend while something (e.g. music) is played... I know that e.g. Rhythmbox has a plugin for that, but I'd like to use SongBird...

---

### Post by produnis on 2010-01-29
bump

---

### Post by tgalati4 on 2010-01-29
Write a script that creates a "lock" file.  For example, songbird_is_running.  Add a file detection routine in the system sleep script.

---

### Post by produnis on 2010-01-29
> **tgalati4 said:**
> Write a script that creates a "lock" file.  For example, songbird_is_running.  Add a file detection routine in the system sleep script.
Thanks for your suggestion, but:
I don't want to prevent Suspend if SongBird is running, but only if SongBird is playing Music!

---

### Post by monraaf on 2010-01-29
pactl is probably what you need.

e.g.
```

pactl list | grep RUNNING

```

See the man page of pactl or the full output of pactl list for more info.

---

### Post by produnis on 2010-01-30
> **monraaf said:**
> pactl is probably what you need.

e.g.
```

pactl list | grep RUNNING

```See the man page of pactl or the full output of pactl list for more info.

YEEEEEEHAAAAAAAA

Thank you so much,
this was exactly I was searching for!!!!

THANK YOU!

---

