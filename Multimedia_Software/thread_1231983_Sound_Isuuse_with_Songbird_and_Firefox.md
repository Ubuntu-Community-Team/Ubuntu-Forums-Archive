---
title: "Sound Isuuse with Songbird and Firefox"
date: 2009-08-05
forum: Multimedia Software
---

### Post by Dai777 on 2009-08-05
Can you tell me why I loose sound in firefox when using songbird is running, even if I'm not playing any sound in songbird firefox has no sound. I have to shut both songbird and firefox down and re-start firefox to get any sound running why is this?

---

### Post by prshah on 2009-08-05
> **Dai777 said:**
> why I loose sound in firefox when using songbird is running, 

Your pulseaudio configuration may be wrong, or the pulseaudio daemon may not be running. 

To check if pulseaudio is running, give the below command in the terminal (Applications-Accessories-Terminal) ```
ps -e| grep pulse
``` If you get blank output, then you need to start the pulseaudio server by pressing Alt+F2 and giving the command```
pulseaudio
``` 

If you still face problems, give the above command in the terminal and post back the output.

---

