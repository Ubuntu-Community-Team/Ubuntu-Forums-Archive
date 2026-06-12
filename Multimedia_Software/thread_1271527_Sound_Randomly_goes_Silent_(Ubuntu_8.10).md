---
title: "Sound Randomly goes Silent (Ubuntu 8.10)"
date: 2009-09-21
forum: Multimedia Software
---

### Post by NandoVilches on 2009-09-21
Hi! I have been having this problem with my computer... You see the sound randomly would go silent. However, if I restart the computer the sound would come back... Any idea what this may be?

Thank You!
-NandoVilches

---

### Post by raboofje on 2009-09-21
Perhaps something has taken exclusive control over your soundcard?

See [http://wiki.linuxaudio.org/wiki/troubleshooting_exclusive_sound_card_access](http://wiki.linuxaudio.org/wiki/troubleshooting_exclusive_sound_card_access) for how to check.

---

### Post by NandoVilches on 2009-09-21
> **raboofje said:**
> Perhaps something has taken exclusive control over your soundcard?

See [http://wiki.linuxaudio.org/wiki/troubleshooting_exclusive_sound_card_access](http://wiki.linuxaudio.org/wiki/troubleshooting_exclusive_sound_card_access) for how to check.

I Checked for ALSA with 
sudo fuser /dev/snd/pcm*

and it came back with this

/dev/snd/pcmC0D0p:    6161m

any idea what it means?

---

### Post by raboofje on 2009-09-21
> **NandoVilches said:**
> /dev/snd/pcmC0D0p:    6161m

This means the process with PID 6161m has opened the sound card for playback.

'ps aux | grep 6161' should tell you which program this PID belongs to.

---

