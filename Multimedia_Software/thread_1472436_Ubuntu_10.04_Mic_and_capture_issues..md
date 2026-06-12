---
title: "Ubuntu 10.04 Mic and capture issues."
date: 2010-05-04
forum: Multimedia Software
---

### Post by chrispche on 2010-05-04
I need to use Skype to contact my kids in South Africa. I live in the UK. This is very important for me. Surely there must be a fix by now on 64bit 10.04 to use mic capture or a workaround. Please does anyone know anything??? This is the only bug causing problems for me. It's quite a major thing.

---

### Post by chrispche on 2010-05-04
Maybe there is a way to get ALSA up and running so I can choose it in Skype.

---

### Post by n3had on 2010-05-04
If your microphone input doesn't work try adding  ```
options snd-hda-intel position_fix=1
``` to alsa-base.conf and here's a how to

[http://www.youtube.com/watch?v=vcAvz9fOEDo](http://www.youtube.com/watch?v=vcAvz9fOEDo)

---

### Post by chrispche on 2010-05-04
Didn't work. :-(

---

### Post by chrispche on 2010-05-04
Is there anyway to get ALSA working in Skype. I have no choice but damn pulseaudio.

---

### Post by n3had on 2010-05-08
> **chrispche said:**
> Didn't work. :-(

FYI it worked for me for realtek audio.

---

### Post by chrispche on 2010-05-08
I solved this in another thread.

---

### Post by stanz on 2010-10-12
> **chrispche said:**
> I solved this in another thread.
Share the thread link?
:)

---

