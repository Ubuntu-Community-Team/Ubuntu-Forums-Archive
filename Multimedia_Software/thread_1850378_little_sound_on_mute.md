---
title: "little sound on mute"
date: 2011-09-26
forum: Multimedia Software
---

### Post by ciscoboy on 2011-09-26
My sound applet is set on mute, and it says "mute all" in a way where  it's locked (so I can't change it), and there's no way that I can  increase the volume except on whatever I'm using (i.e.: youtube,  internet video, video player...). But the thing is, the volume is set  low; i can still hear what someone is saying if someone's talking.
I also tried to access the sound preferences (from the upper bar and from the preferences menu), without success.

Any advice?

Ciscoboy

---

### Post by lidex on 2011-09-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

