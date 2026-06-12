---
title: "Separating front and back audio inputs/outputs"
date: 2011-01-02
forum: Multimedia Software
---

### Post by supernicko on 2011-01-02
Hi all,

I've been running my current system on Windows 7 for the last year and a bit. In Windows 7, I could use my headphone jacks on the front of the machine separately to the main inputs on the back of my machine. Under Ubuntu so far I have not been able to get this working.

I most need this for Skype. I like to have it ring on the speakers but then communicate through my headset. There are other things I do where this is useful too, including some podcasting that I do.

lspci reports the following as my soundcard:
```

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller

```

It's an onboard sound card so maybe I'll need to get hold of something new but I'd prefer to get this working like it was under windows.

Cheers,
Nick

---

### Post by supernicko on 2011-01-02
Some further information/thought.

In Skype the only input/output option I'm provided with is "Pulseaudio". Is there any way I can access the ALSA input/outputs directly? Perhaps that would work?

It's really disappointing that I haven't gotten this to work so far. Need to record an interview for a podcast next week so would like to get it up and running by then.

---

