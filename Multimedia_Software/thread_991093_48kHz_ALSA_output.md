---
title: "48kHz ALSA output?"
date: 2008-11-23
forum: Multimedia Software
---

### Post by Epicurious on 2008-11-23
I just installed Ubuntu and eventually got my external sound card working - kinda. My USB sound card expects sound in 48kHz but ALSA is sending it 44.1kHz sound. So my question is: how do I configure ALSA to convert all outgoing sound to a 48000Hz rate?

---

### Post by psyke83 on 2008-11-23
> **Epicurious said:**
> I just installed Ubuntu and eventually got my external sound card working - kinda. My USB sound card expects sound in 48kHz but ALSA is sending it 44.1kHz sound. So my question is: how do I configure ALSA to convert all outgoing sound to a 48000Hz rate?

If you're using Hardy or Intrepid, you shouldn't be using the ALSA dmix device - PulseAudio is used by default.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Once you have PulseAudio configured, edit /etc/pulse/daemon.conf. You can manually specify the rate of the PulseAudio server (it defaults to 44100Hz). I don't believe this is a necessary step, however, as different bitrates will always get resampled automatically.

---

### Post by BlueSkyNIS on 2008-11-23
Wow psyke83, you resolved one more issue regarding audio for me. Finally, I can put my speaker tweeters up to the test. :)

---

### Post by Epicurious on 2008-11-24
thanks psyke83! Editing /etc/pulse/daemon.conf worked like a charm :D

---

