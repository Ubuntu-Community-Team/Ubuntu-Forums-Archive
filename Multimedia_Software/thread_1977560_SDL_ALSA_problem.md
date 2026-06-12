---
title: "SDL ALSA problem"
date: 2012-05-10
forum: Multimedia Software
---

### Post by bluearcus on 2012-05-10
I have been trying to get KDEnlive to run under Lubuntu 12.04, but have come up against a problem with sound support.

KDEnlive by default forces an installation of pulseaudio, which I have subsequently removed. 

Now all apps are working fine again with sound except KDEnlive, which, when ALSA output is configured, throws an error message claiming

"SDL Failed to open audio: No available audio device"

Searching for this problem suggests that it's because the SDL library versions installed are pulseaudio ones, not ALSA ones, and that installing

libsdl1.2debian-alsa 

Should sort out the problem.

However, libsdl.2debain-alsa has been removed from Precise.

Any ideas how I might go about sorting this? I'd rather not build the SDL libs from source if I can help it!!!

Regards,

Mike Miller

---

