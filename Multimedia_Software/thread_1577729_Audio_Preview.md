---
title: "Audio Preview"
date: 2010-09-19
forum: Multimedia Software
---

### Post by ArbiterOfTruth on 2010-09-19
Good day,

Ubuntu has a feature where you can just place the cursor over an audio file & it plays. When I installed the netbook remix onto my netbook, no audio or video could be played. I installed vlc & I can play audio & video now but I still can't get the audio preview. What do I need to do to enable it? If a thread has already been dedicated to this topic & I have missed it, I apologize & would ask to be redirected to said thread.


Thanks in advance,
ArbiterOfTruth

---

### Post by cgroza on 2010-09-19
Did you installed the ubuntu-restricted-extras?

---

### Post by ArbiterOfTruth on 2010-09-19
How do I do that?

---

### Post by mc4man on 2010-09-19
The audio preview by default uses totem, try installing  these 3 gstreamer plugins

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly 
```

If you need some slightly better enabled plugins then add the ppa in my sig to your sources and update, lucid only

---

### Post by ArbiterOfTruth on 2010-09-21
Hey I got it solved from advice from a solved thread. Had to right click the file & select Open With RhythmBox which then prompted me to install the 3 gstreamer things I needed. It works now.

---

