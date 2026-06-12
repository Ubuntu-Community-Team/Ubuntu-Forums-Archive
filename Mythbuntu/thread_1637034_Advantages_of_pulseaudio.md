---
title: "Advantages of pulseaudio"
date: 2010-12-03
forum: Mythbuntu
---

### Post by azmyth on 2010-12-03
I've been using Myth for years and always have used ALSA. Is there a real advantage to switch to pulse. I'm just running the audio out from the MB to my PC Bose speakers. I also run my TV sound output through ladspa to normalize the volumes across all the tuners. The problem is this means mute doesn't work in mythtv so I have to use irexec and I wrote a script to mute my sound which I don't like since I no longer get the popup that says mute on or off. Would going to pulse fix the volume so I wouldn't need ladspa.

Thanks

---

### Post by nickrout on 2010-12-03
> **azmyth said:**
> I've been using Myth for years and always have used ALSA. Is there a real advantage to switch to pulse. I'm just running the audio out from the MB to my PC Bose speakers. I also run my TV sound output through ladspa to normalize the volumes across all the tuners. The problem is this means mute doesn't work in mythtv so I have to use irexec and I wrote a script to mute my sound which I don't like since I no longer get the popup that says mute on or off. Would going to pulse fix the volume so I wouldn't need ladspa.

Thanks

are you using 0.24?

---

### Post by azmyth on 2010-12-03
Yes, 0.24.

---

### Post by nickrout on 2010-12-03
pulse should work fine for you then, and in any event it is easy to change back and forth.

---

### Post by azmyth on 2010-12-05
Do you know which one I need to use ALSA:pulse or pulseaudio:default? The first one works the second one doesn't. I looked at the FE log on the second run and it didn't give me any type of errors except for a few audio underuns.

---

### Post by LowSky on 2010-12-05
i tried using pulse and the audio was delayed by a few seconds and made a hiss occasionally. Staying with Alsa is just easier.

---

### Post by nickrout on 2010-12-05
> **azmyth said:**
> Do you know which one I need to use ALSA:pulse or pulseaudio:default? The first one works the second one doesn't. I looked at the FE log on the second run and it didn't give me any type of errors except for a few audio underuns.

If one works and the other doesn't, why are you asking which one to use?

---

### Post by azmyth on 2010-12-05
Guess I'm just trying to figure out what the difference is between the two and if they're the same why does two different audio devices show up.

---

