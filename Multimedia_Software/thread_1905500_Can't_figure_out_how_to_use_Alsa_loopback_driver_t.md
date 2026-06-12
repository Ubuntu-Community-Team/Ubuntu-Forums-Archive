---
title: "Can't figure out how to use Alsa loopback driver to record audio"
date: 2012-01-07
forum: Multimedia Software
---

### Post by someitalian123 on 2012-01-07
I'm trying to record the audio that comes from my speakers but my sound card doesn't have the "Stereo Mix" Option. So I was told I could accomplish this with the Alsa Loopback driver, but I don't know how to get it to work. I loaded it with sudo modprobe snd-aloop
but I don't know what to do after that. When I try testing it with audacity I can't get it to record any audio. and when I try to configure loopback in alsa mixer it says "This sound device does not have any controls."

---

### Post by b0b138 on 2012-01-07
Try this  [http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html](http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html)

---

### Post by someitalian123 on 2012-01-07
> **b0b138 said:**
> Try this  [http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html](http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html)

That didn't work, also I want to be able to use the audio input for streaming audio live from my computer with flash in a web browser, not just for recording audio files.

---

