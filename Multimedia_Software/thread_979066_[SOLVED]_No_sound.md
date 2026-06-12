---
title: "[SOLVED] No sound"
date: 2008-11-11
forum: Multimedia Software
---

### Post by ellalan on 2008-11-11
Hi
I tried some tweaking in FF3 and it broke the sound, now there is no sound in my Ubuntu 8.10. I have revert back to default the settings in FF3 but still no sound.
Could some one give me a hand to fix this please. TIA.

---

### Post by ellalan on 2008-11-11
Its OK, I have found the solution from this post:
Quote:
Originally Posted by psyke83 View Post
You're probably suffering from an ALSA bug where your PCM or Master mixer gets muted or set to 0% (it seems a common problem for many on Intrepid).

Check the volume levels via:

Code:

$ alsamixer -Dhw

You should also follow steps 2-5 of this guide.

---

### Post by psyke83 on 2008-11-11
> **ellalan said:**
> Hi
I tried some tweaking in FF3 and it broke the sound, now there is no sound in my Ubuntu 8.10. I have revert back to default the settings in FF3 but still no sound.
Could some one give me a hand to fix this please. TIA.

Your PCM volume is set to 0%...

---

