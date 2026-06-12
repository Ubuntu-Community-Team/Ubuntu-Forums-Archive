---
title: "Digital audio output startup hiccup"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by eb710 on 2008-02-07
I am using the S/PDIF coaxial digital audio output on my HP Pavilion M8187C desktop PC. In Windows Vista, when the machine boots there is a little "welcome" sound while the Windows icon waves in a a little circle. I noticed that there is a little hiccup in the sound when it starts. You can hear a quiet click, then a second or so of silence, then the sound itself, already in progress. So, the start of the audio gets cut off for a second or so. This would be unacceptable, except that it only happens once when the operating system is booting. After that, sounds play perfectly.

Here's the problem: In Linux, the same hiccup occurs every time a sound is played. This makes it impossible to use, as every sound has the beginning cut off. My guess is that Windows turns the audio interface on once at startup, then leaves it on, while Linux is somehow turning on the interface and shutting it off after every use. So I guess I'd like to know if there's a workaround that will force the audio interface to stay on permanently after the first sound.

The sound driver is snd-hda-intel, with option model=6stack-dig

In my search for a solution to this problem, I've actually gone as far as installing the new Hardy Alpha release and then installing the latest (1.0.16) release of Alsa drivers on top of that. So this is the absolute latest, fresh off the presses version. I don't think this problem is specific to this version, however.

---

