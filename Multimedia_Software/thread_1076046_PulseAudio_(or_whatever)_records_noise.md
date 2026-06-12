---
title: "PulseAudio (or whatever) records noise"
date: 2009-02-20
forum: Multimedia Software
---

### Post by mriedel on 2009-02-20
When I turn my microphone off (hardware switch) or even physically pull the cable, no sound is recorded for 1-2 seconds, but then "it" (pulse or alsa) starts recording random noise. It can be observed by looking at the PA volume meter or recording the noise with the sound recorder.

As soon as I turn my microphone in again, the noise disappears. After a delay of 1-2 seconds, alsa/pulse starts recording sound again, the random noise is not there any more. In fact, the minimal background noise picked up by my microphone is much lower in volume than the random noise.

Any ideas what that might be? It's a real problem when I want to use Skype/Mumble/Teamspeak.

---

### Post by mriedel on 2009-03-01
bump

---

### Post by mriedel on 2009-03-03
bump

---

### Post by markbuntu on 2009-03-03
Do you have any other "capture" settings turned on in the mixer?

---

### Post by mriedel on 2009-03-03
Thanks for your reply.

No, everything else is off, only Microphone is on (although there are 3 of them and they all do the same thing).

---

