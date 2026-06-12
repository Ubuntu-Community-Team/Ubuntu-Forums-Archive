---
title: "Use headphones when available, otherwise speakers?"
date: 2008-05-21
forum: Multimedia Software
---

### Post by noerrorsfound on 2008-05-21
When I want to start using my USB headset for audio playback, I have to go to the sound options and select it. Then, when I'm done, I have to go back to the sound options and change it back. How can I just use the USB headset when it's available (plugged in) and use the speakers when it's not?

---

### Post by Xiong Chiamiov on 2008-05-23
With your headset plugged in, running
```

asoundconf list

```
should give you something like this:
```

Names of available sound cards:
Headset
CA0106

```
You can then set the default card to be the headset by
```

asoundconf set-default-card Headset

```
However, this seems to not quite be perfect for me.  For whatever reason, amarok is the only app that actually plays through my speakers when the headset's not plugged in; nothing else seems to want to fall back to my sound card.  At the moment, I'm just happy I can use them at all, but let me know if you find a better solution.

---

### Post by noerrorsfound on 2008-06-24
> **Xiong Chiamiov said:**
> With your headset plugged in, running
```

asoundconf list

```
should give you something like this:
```

Names of available sound cards:
Headset
CA0106

```
It lists the following:
> Names of available sound cards:
CK804
default

---

### Post by Xiong Chiamiov on 2008-06-26
My memory's a bit faint, but I seem to remember that there's some file somewhere where you can change the name of soundcards, and I also seem to remember that some guide somewhere told me to change the card I wanted as default to be named "default", so I'm guessing that's what happened to you.  Have you tried 
```

asoundconf set-default-card default

```
?

---

### Post by noerrorsfound on 2008-07-16
Unfortunately that doesn't work for me.

---

### Post by noerrorsfound on 2008-12-21
When I actually get Ubuntu to output sound to my headset again (apparently the switch to PulseAudio screwed things up) it would be nice to have this basic functionality.

---

