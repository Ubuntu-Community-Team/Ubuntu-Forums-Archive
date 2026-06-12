---
title: "Linux Audio Record/Capture Program?"
date: 2008-01-23
forum: Multimedia Production
---

### Post by OvenMitt Bandit on 2008-01-23
Is there a Linux program that records/captures sound that is currently coming through your speaker and saves it to a file? So if I have, lets say, a streaming video or something, I can just capture the audio for a certain amount of time. Kinda like Sound Recorder for Windows, I guess.

---

### Post by logos34 on 2008-01-23
There's Audacity (>use 'Vol' for input).  Or gnome-sound-recorder ('mix', IIRC).  (not sure about gui for kde, though)

---

### Post by asmiller-ke6seh on 2008-01-23
Audacity does a great job.

---

### Post by eye208 on 2008-01-24
> **OvenMitt Bandit said:**
> Is there a Linux program that records/captures sound that is currently coming through your speaker and saves it to a file?
It depends on your soundcard. Some cards do not support loopback recording with ALSA. Check the sources tab in the volume control application. The loopback source is usually called "Mix".

If you want to record particular streams there may be a better solution: You can use VLC to open the stream and save it to disc. If you save as "raw input" there will be no quality loss at all.

---

