---
title: "Sound super quiet for speakers"
date: 2008-11-18
forum: Multimedia Software
---

### Post by qwark1 on 2008-11-18
I just intalled 8.10 and everything works exept my logitech x-240 speakers.  If I unplugg the speakers and listen throguh the built-in laptop speakers it sounds fine but when plug in the speakers i can barely hear it.  I have tried to turn everything up including pcm,master, front, and have used alsamixer.  When i open alsamixer there is supposed to be many controls but for me there is only one(master).  It says that my card is pulseaudio and i think this may be part of the problem.  If anyone could help it would be much appreciated.

---

### Post by kostkon on 2008-11-18
> **qwark1 said:**
> I just intalled 8.10 and everything works exept my logitech x-240 speakers.  If I unplugg the speakers and listen throguh the built-in laptop speakers it sounds fine but when plug in the speakers i can barely hear it.  I have tried to turn everything up including pcm,master, front, and have used alsamixer.  When i open alsamixer there is supposed to be many controls but for me there is only one(master).  It says that my card is pulseaudio and i think this may be part of the problem.  If anyone could help it would be much appreciated.
Yes, the *alsamixer* utility does not work as is supposed to anymore, since all of the *ALSA* audio is passing through *PulseAudio* in 8.10

To access your volumes use the gnome volume control utility, i.e. right click on the speaker in your taskbar and select *Open Volume Control*.

---

### Post by qwark1 on 2008-11-18
thanks for your help.  The controls in that were turned up too but it led me to mess around more and it turns out that I had to plug it in to a different jack on my laptop.  I don't know why this is because with vista the sound output only worked through the one it was initially in.

---

