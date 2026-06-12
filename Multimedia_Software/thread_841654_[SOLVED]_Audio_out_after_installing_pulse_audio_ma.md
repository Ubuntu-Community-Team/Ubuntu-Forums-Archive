---
title: "[SOLVED] Audio out after installing pulse audio manually."
date: 2008-06-26
forum: Multimedia Software
---

### Post by diwas on 2008-06-26
I installed pulse audio from add/remove manually. Iam using 7.10 version of ubuntu. After installing, the audio was out and after i typed fretsonfire in the terminal following error comes up(see attachment).

Thank you in advance.

---

### Post by diwas on 2008-06-30
Any suggestions please?

---

### Post by Bentai on 2008-06-30
I'm not an expert by any means, but I think PulseAudio is a different sound server than ALSA. "fretsonfire" is trying to hook into the ALSA sound server which is not active or not configured, and so it's kicking back all sorts of errors.

Try and see if you can configure the program to use the PulseAudio server, or change 7.10 to use the ALSA server and see if that works.

---

### Post by diwas on 2008-06-30
Yes, I want to roll back to ALSA...but no idea how to do it.

---

### Post by Bentai on 2008-06-30
Go to System -> Preferences -> Sound
And you should be able to change from PulseAudio to ALSA for the output.

---

### Post by Bentai on 2008-07-01
So it worked then? :)

---

### Post by diwas on 2008-07-02
Im sorry but i had to format my drive. And i installed latest version. I couldnt check it out, but probably it wud have worked. Sorry but the format was to be done.

---

