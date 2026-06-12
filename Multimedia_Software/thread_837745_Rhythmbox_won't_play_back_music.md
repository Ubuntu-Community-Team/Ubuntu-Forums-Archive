---
title: "Rhythmbox won't play back music"
date: 2008-06-22
forum: Multimedia Software
---

### Post by bigplrbear on 2008-06-22
I have a strange problem- Rhythmbox won't play music. 
My sound card (an ATI IXP) works fine. Totem plays music just fine. It's just Rhythmbox. Any idea what's going on?

---

### Post by bigplrbear on 2008-06-22
Sorry for the double post. Just an update- here's the error I'm getting when i try to play music-

Failed to connect stream: Invalid argument

---

### Post by bigplrbear on 2008-06-23
Ok, with a little research, I managed to figure it out. It seems that Pulseaudio is really buggy, so I just deleted it. When I reboot the computer, it fell back to ALSA, and sound worked again! :D

So um yeah....

---

