---
title: "create virtual capture device in PA with extra boost?"
date: 2008-12-15
forum: Multimedia Software
---

### Post by threetimes on 2008-12-15
Is it possible to create a virtual sound capture device in PulseAudio with extra boost?
I want this because I almost can't hear myself if I record my voice, and the default +20dB doesn't seem to be enough.
A strange thing is that I can hear myself loud enough when I just talk into the microphone, but not when recording.
I don't care much about qualtiy or noise.

---

### Post by markbuntu on 2008-12-15
Do you have the capture sliders turned up?
Some card/drivers also have a mic boost capture slider that needs to be turned up.

Mic sliders in the Playback section of your mixer have nothing to do with recording, they are for playing your mic in your speakers. You need to use the capture sliders for recording.

---

### Post by markbuntu on 2008-12-15
sorry, dp.

---

### Post by threetimes on 2008-12-16
> **markbuntu said:**
> Do you have the capture sliders turned up?
Some card/drivers also have a mic boost capture slider that needs to be turned up.

Mic sliders in the Playback section of your mixer have nothing to do with recording, they are for playing your mic in your speakers. You need to use the capture sliders for recording.

All sliders are already up, see the screenshots [here]("http://peter-server.homelinux.net/sound/").

---

