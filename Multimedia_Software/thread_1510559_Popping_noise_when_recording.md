---
title: "Popping noise when recording"
date: 2010-06-15
forum: Multimedia Software
---

### Post by Joshun on 2010-06-15
Hello,
                                          
This isn't serious, but I am involved in film production, and this can be very annoying at times. I've found that when you record something (mic, line in, anything, regardless of whether anything is actually plugged into it or not), they'll be a pop at the beginning, and at the end, when i've stopped recording. The sound quality of the recorded content is good, but there is a pop at the beginning and the end, and in a film, with sfx etc, this is really quite annoying. I've noticed this doesn't happen on my netbooks intel sound card, only on the main pc's nvidia sound card. Changing device settings in audacity helped a little, but didn't solve the problem completely. I've tried other programs but it still produces a similar popping noise.

Please could somebody help with this

Joshua

---

### Post by Joshun on 2010-06-15
Bump

---

### Post by Rumpty on 2010-06-16
Could it relate to this discussion?
[http://newyork.ubuntuforums.org/showthread.php?t=1308954](http://newyork.ubuntuforums.org/showthread.php?t=1308954)

---

### Post by Joshun on 2010-06-16
@Rumpty: That may be what's causing the problem. It usually happens only during recording though. The ubuntu version is Lucid, so it may be a different problem all together. I'll try out the suggestion on the linked thread.

Here is a sample of the popping noise, an ogg in a zip file. It happens regardless of whether there is actually anything plugged into the input port.

lscpi gives:
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)

---

### Post by Joshun on 2010-06-17
I've tried the suggestion from the link but it doesn't make any difference, the popping is still there.

---

### Post by Joshun on 2010-06-18
Strangely enough, the popping only happens when doing a stereo recording, and doesn't happen on mono. The card supports stereo recording well however, so i'm not sure what is causing this.

---

### Post by cchhrriiss121212 on 2010-06-18
I've heard pulse can cause these types of defects, so try switching to ALSA in audacity.

---

