---
title: "I think I screwed up, badly."
date: 2009-09-10
forum: Multimedia Software
---

### Post by MetroidJunkie2008 on 2009-09-10
I was messing around with alsa-conf files as someone instructed on a post to get my headphones to work by defaulting to it and I think, in the process, I caused it to stop detecting my computer's soundcard. Typing in alsamixer in terminal results in "alsamixer: function snd_ctl_open failed for default: No such device" and asoundconf list doesn't show anything, going to volume control returns null output. and trying to goto asoundconf-gtk results in "You need at least one ALSA sound card for this to work!
". Is there a way to default Ubuntu to the same audio detections as it had when it was installed, outside of reinstalling?

---

### Post by wojox on 2009-09-10
Open a terminal:

```
sudo asoundconf set-default-card
```

May work ?

---

### Post by MetroidJunkie2008 on 2009-09-10
I need something to default it to for that to work and, since asoundconf list came up dry... :(

Edit: I just tried reinstalling all the alsa peripherals but it still says no module, what should I do?

---

### Post by fh_scott on 2009-09-10
what does 'aplay -l' show for your cards?

---

### Post by MetroidJunkie2008 on 2009-09-10
"aplay: device_list:217: no soundcards found..."


I don't know what happened, guess attempting to make it default to headphones f-ed up its soundcard detection. Is there a way to non-destructively revert Ubuntu's audio detection to what it came with? I have the disc but I have many programs installed that I'd rather not lose.

---

### Post by mhgsys on 2009-09-10
Have a look here;

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

This will get back ubuntu's default settings for your soundcard for sure.

---

### Post by MetroidJunkie2008 on 2009-09-10
Success! After I specifically installed the intel8x0 module and rebooted, sound started flooding through the speakers. Thank you! :guitar:

---

### Post by mhgsys on 2009-09-10
Nice, 

Enjoy your sound!

---

