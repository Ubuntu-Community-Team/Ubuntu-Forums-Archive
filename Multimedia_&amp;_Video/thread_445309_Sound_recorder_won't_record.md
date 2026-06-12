---
title: "Sound recorder won't record"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by Doughy on 2007-05-15
I can't get the sound recorder to record from my microphone input.  I have searched all over the web and nothing seems to fix it.  I tried re-installing alsa drivers, and now my alsamixer won't run.  I'm trying to use the sound card on my intel 965 motherboard.

Any ideas?

Sometimes I hate linux.

---

### Post by Dekunuts on 2007-05-16
if you change your audio drivers from also to oss, it will probably work, given you have not left anything muted.

---

### Post by Doughy on 2007-05-16
How do I change my drivers to OSS?

---

### Post by dabl on 2007-05-16
Right click the little "speaker" icon in the upper right of your desktop.  I'm currently stuck  at a stupid Winbloze machine so I'm working from a senile memory here, but I think you choose "preferences", and then look for "output device".  If that's not right, try "open volume control" and see if that provides a mixer with a bunch of format and device choices.

HTH!

---

### Post by xjgnsdof on 2007-11-20
Eh, I have ALSA instead of OSS on my laptop, and I record sound just fine. I can't record sound, however, on my desktop that also runs ALSA, so I think the problem lies in the settings themselves. I'm going to compare and contrast settings and see what I find.

---

