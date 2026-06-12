---
title: "How do I set the microphone volume?"
date: 2012-09-27
forum: Multimedia Software
---

### Post by zerubbabel on 2012-09-27
How does one set the microphone volume in Kubuntu? I tried Phonon, but there doesn't seem to be any mechanism there to set the volume. What am I missing?

(I'm running Kubuntu 12.04, 64-bit)

---

### Post by ajgreeny on 2012-09-27
Does Kubuntu use pulseaudio?  If it does you need to open pulseaudio volume control and set the microphone volume there, and also possibly the capture level.

Alsamixer in terminal may also help, but again, I am not sure how Kubuntu differs from ubuntu.

---

### Post by zerubbabel on 2012-09-27
Ah! I found the controls, finally. You have to click the "Mixer" button on the pop-up speaker volume control in the system tray.

---

