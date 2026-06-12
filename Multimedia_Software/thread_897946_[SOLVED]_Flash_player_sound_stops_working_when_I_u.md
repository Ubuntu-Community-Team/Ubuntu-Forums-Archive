---
title: "[SOLVED] Flash player sound stops working when I use VLC"
date: 2008-08-22
forum: Multimedia Software
---

### Post by BrendanM on 2008-08-22
Whenever I start using VLC to watch a video or listen to music, it breaks the sound on any flash content. Even if I pause VLC, or stop it, or even completely close VLC, there's no sound on any flash content. The only way to get it back is to close VLC and then completely restart Firefox.

Does anyone have any suggestions?

---

### Post by ubuntu-freak on 2008-08-22
Which version of Flash Player do you have installed? I recommend you give v10 RC a try. Installation instructions are in the troubleshooting section of my [howto](ubuntuforums.org/showthread.php?t=766683).
 
Alternatively, or in conjunction, you could revert from PulseAudio to ALSA, by taking a look at the following [howto](http://ubuntuforums.org/showthread.php?t=885437).

---

### Post by BrendanM on 2008-08-22
Sweet, thanks. Those both look like very promising suggestions and I will try them. When was this PulseAudio thing added?

---

### Post by BrendanM on 2008-08-22
Sweet, I followed the guide to switch back to ALSA and it worked great. Thanks for the help.

---

### Post by ubuntu-freak on 2008-08-22
> **BrendanM said:**
> Sweet, I followed the guide to switch back to ALSA and it worked great. Thanks for the help.

 
You're welcome. :)

---

