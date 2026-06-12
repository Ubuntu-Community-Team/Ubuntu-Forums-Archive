---
title: "[SOLVED] Weird sound problem"
date: 2008-08-20
forum: Multimedia Software
---

### Post by Farajamo on 2008-08-20
It's not necessarily that I don't get sound, but it seems to only work for one thing.  For example, if the first thing I do when my computer boots is watch a video on youtube, then the sound on rhythm box might not work, and vice versa. So far the only way I've been fixing it is restarting my computer, which is kind of a nuisance. Is this a common problem? Thanks.

---

### Post by prshah on 2008-08-20
> **Farajamo said:**
> For example, if the first thing I do when my computer boots is watch a video on youtube, then the sound on rhythm box might not work, and vice versa. 

I had similar problems until I setup pulse audio properly, using this guide:
[How To: The (almost) Perfect Pulse Audio Setup]("http://ubuntuforums.org/showthread.php?t=776739")

Now everything works great!

---

### Post by eye208 on 2008-08-20
I had similar problems. Here's my guide:

[How to fix all PulseAudio-related issues in 2 minutes](http://ubuntuforums.org/showthread.php?t=885437)

Now everything works great.

---

### Post by Rickles65 on 2008-08-20
Heh, I gave up on pulse. I was having a lot of the same issues and tried several different "fixes" for Pulse none of which fully worked.

I switched to ALSA and the problems dissapeared.

---

### Post by prshah on 2008-08-20
> **Rickles65 said:**
> 
I switched to ALSA and the problems disappeared.

Except that you can't have sound in more than one application simultaneously, if you use ALSA.

---

### Post by Farajamo on 2008-08-20
So far everything seems to be working. Thanks guys!

---

### Post by eye208 on 2008-08-20
> **prshah said:**
> Except that you can't have sound in more than one application simultaneously, if you use ALSA.
Of course I can.

---

