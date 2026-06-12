---
title: "Selective or no audio in PulseAudio (Jaunty)"
date: 2009-04-25
forum: Multimedia Software
---

### Post by Aikon- on 2009-04-25
Today I upgraded from 8.10 to 9.04 and ran into a somewhat strange -- but predictable -- problem with PulseAudio.

I can selectively make PulseAudio select "Null Output" as the output device, effectively disabling all desktop audio.

Steps to reproduce:
 1. Start an audio file playing in MPD.
 2. Reboot your system.
 3. When the system comes back up, note that the audio file continues playing in MPD from where it left off.
 4. Note that when the login screen is ready, there are no bongos. Furthermore, there is no login sound when you login.
 5. Note that PulseAudio is set to "Null Output" and no desktop audio makes it to the speakers.

Steps to correct:
 1. Stop MPD
 2. Reboot the system
 3. Note that bongos, login sound, and all desktop audio (including MPD) works properly and that PulseAudio output device is set properly.

Suggestions?

-Aikon

---

### Post by Aikon- on 2009-04-26
I have found a solution for this problem. In ```
/etc/mpd.conf
```, add an audio output section, as follows:

```
audio_output {
  type     "pulse"
  name     "PulseAudio (local"
}
```

This forces MPD to wait until a Pulse server is up (i.e. when you start your session). If you don't have this in mpd.conf (as Jaunty ships by default), then on startup, MPD automatically picks an audio output (in my case, it chooses ALSA) which seems to lock out Pulse.

Regards,
-Aikon

---

### Post by justynbutler on 2009-09-16
> **Aikon- said:**
> I have found a solution for this problem. In ```
/etc/mpd.conf
```, add an audio output section, as follows:

```
audio_output {
  type     "pulse"
  name     "PulseAudio (local"
}
```

This forces MPD to wait until a Pulse server is up (i.e. when you start your session). If you don't have this in mpd.conf (as Jaunty ships by default), then on startup, MPD automatically picks an audio output (in my case, it chooses ALSA) which seems to lock out Pulse.

Regards,
-Aikon

Ahhh! Thank you, you solved my problem!

I couldn't work out why audio had stopped working when it had been fine before. I didn't remember changing anything. I tried so many things to get it going again.

Then when I read this post I realised I installed mpd to have a play around. I hadn't even considered that it could be causing the problem.

Uninstalled mpd, everything works again!

---

