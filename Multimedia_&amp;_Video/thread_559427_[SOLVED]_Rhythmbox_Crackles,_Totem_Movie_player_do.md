---
title: "[SOLVED] Rhythmbox Crackles, Totem Movie player does not?"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by jusmurph on 2007-09-25
Why when i listen to mp3's in Rhythmbox it crackles... however that same mp3 it plays fine under totem movie player?

What is the difference between the two?

---

### Post by jusmurph on 2007-09-26
So is there any way to get Rythymbox to use the xine back end?

---

### Post by rsambuca on 2007-09-26
They both use the gStreamer backend (at least by default), so I can't imagine why this would happen.  You can install totem-xine or totem-gstreamer, but rhythmbox is gstreamer only.

---

### Post by jusmurph on 2007-09-26
Anyone know of any Gstreamer repos witht he current version?

---

### Post by gwon on 2007-09-30
Bumping to report the exact same issue. Rythmbox has a weird annoying crackle, but Totem playing the same file is fine.

---

### Post by rsambuca on 2007-09-30
Maybe one of you can report a bug at launchpad.

---

### Post by jusmurph on 2007-10-02
> **rsambuca said:**
> Maybe one of you can report a bug at launchpad.

Excuse my ignorance, however where would it be approriate to report it?

---

### Post by rsambuca on 2007-10-02
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by jusmurph on 2007-10-02
[https://bugs.launchpad.net/ubuntu/+bug/148351](https://bugs.launchpad.net/ubuntu/+bug/148351)

---

### Post by jusmurph on 2007-10-04
Enabling Crossfade solved this:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/116990](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/116990)

---

