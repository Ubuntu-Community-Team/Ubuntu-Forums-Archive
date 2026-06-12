---
title: "No sound with Realtek ALC880"
date: 2010-04-03
forum: Multimedia Software
---

### Post by godoakos on 2010-04-03
I can't get any sound to come out of my laptop through Kubuntu. Please help me by giving me step by step instructions, because I'm a total noob at such things. I've went through the Comprehensive guide as well - to no avail.

To sum it up:
Kubuntu 9.10
Realtek ALC880
No sound

Total noob step-by-step guide please.
Thank you in advance.

---

### Post by lidex on 2010-04-03
Check out this guide, except for the pulseaudio part:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

No joy? Try this:
[https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")

Keep us updated.

---

### Post by godoakos on 2010-04-04
mmmkay, I screwed up, somehow I managed to delete my soundcard...
now "aplay -l" says that "device_list:223: no soundcards found..."

EPIC FAIL on my part

UPDATE: reinstalled soundcard, going through the guide you provided, lidex - thanks for the quick reply

---

### Post by godoakos on 2010-04-05
I've had sound as long as the login sound. This is better than nothing? But when I went on youtube and started watching a video, the speakers made a bang and sound disappeared again.

Thinking of switching back to 8.04LTS, that worked great :(

---

### Post by godoakos on 2010-04-07
I'm pretty sure now that my sound card is being overwritten by application or whatever you say it when something gets bigger priority than your card. ie. I started unreal tournament 2004 and there was no sound. Sound disappears also when starting to watch a video on gametrailers so what the hell?

Any ideas???

EDIT: Checked with
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

and it seems that the only other program running is kmix...now really, i get a feeling that my system is screwing with me on purpose. Tomorrow it will go legs and go eat me :(

---

### Post by lidex on 2010-04-07
> **godoakos said:**
> I'm pretty sure now that my sound card is being overwritten by application or whatever you say it when something gets bigger priority than your card. ie. I started unreal tournament 2004 and there was no sound. Sound disappears also when starting to watch a video on gametrailers so what the hell?

Any ideas???

EDIT: Checked with
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

and it seems that the only other program running is kmix...now really, i get a feeling that my system is screwing with me on purpose. Tomorrow it will go legs and go eat me :(

What was the output of that command?

---

