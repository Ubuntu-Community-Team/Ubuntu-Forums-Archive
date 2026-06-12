---
title: "Pulse audio yet another problem"
date: 2008-10-22
forum: Multimedia Software
---

### Post by demonskier on 2008-10-22
I can't run the volume control or any of the other pulse services it says connection failed connection refused.  I can't get pulseaudio to run even with the pulseaudio -D command it just says Daemon Startup Failed.  However when I start it with root privileges as sudo pulseaudio -D --system I think it starts but the services give me the message connection failed access denied


anybody have any suggestions?? Please

---

### Post by patrickballeux on 2008-10-22
Do you have any software running at the same time like a browser with Flash, a music player, a video player?

They could lock the sound card, preventing pulseaudio to have access..


If you don't find anything, reboot the computer to start clean...

---

### Post by demonskier on 2008-10-22
I have tried rebooting and still no results.

---

