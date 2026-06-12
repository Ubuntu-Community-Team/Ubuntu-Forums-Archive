---
title: "amarok skips a second or two into track :S"
date: 2008-06-10
forum: Multimedia Software
---

### Post by Gizmo89 on 2008-06-10
hi, anyone know if there's a way to stop amarok music player from skipping a couple of seconds into each track?

---

### Post by psyke83 on 2008-06-11
> **Gizmo89 said:**
> hi, anyone know if there's a way to stop amarok music player from skipping a couple of seconds into each track?

If you are running Hardy and experience skipping, perform this simple test:

1. Ensure Amarok is not running
2. Kill the PulseAudio server:
```
$ pkill pulseaudio
```
3. Open Amarok, play a song and listen for any skipping

If skipping was eliminated from this simple test, then your problem is with PulseAudio's buffering. See my guide here (Part A & C): [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

