---
title: "No sound at all anymore"
date: 2012-06-12
forum: Multimedia Software
---

### Post by samwillc on 2012-06-12
Hi everyone,

Yesterday, I had sound, today I don't!

I have installed moonlight add on for firefox, and installed the restricted extras pack in the software centre. That prompted me to remove a few libav packages which I did.

Would that have stopped my sound? I can hear the slight hiss turning the speakers up all the way so they are connected. Nothing is muted. Pulseaudio is running, my sound card is recognised.

What would have stopped it literally overnight?! I don't fancy doing a reinstall just to get my sound back.

Thanks.

Sam.

Tried reinstalling alas/pulseaudio
Alsamixer levels are fine
Nothing muted

Sound > test sound (fron left/right), no sound from live cd either.

ubuntu@ubuntu:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The card is detected.

Don't know what else to do?! Just stopped working :(

---

### Post by samwillc on 2012-06-12
Did fresh install but still no sound?!

Very confused as to how the test front left/right works sometimes. It has worked on another fresh install using the same dvd. Not working this time though.

Something very weird is going on, I've had nothing but sound problems since using ubuntu. Everything else is great.

Would buying a sound card be a better option as maybe its a problem with the onboard. If so, does anyone have any suggestions for a cheap one that works? It's only for music/video/youtube so doesn't need to be top of the range.

Sam.

Here is the alsa script upload if that helps:

[http://www.alsa-project.org/db/?f=f106a8dc4d74b93bd91b71fa3e0f69f5be39b526](http://www.alsa-project.org/db/?f=f106a8dc4d74b93bd91b71fa3e0f69f5be39b526)

---

### Post by samwillc on 2012-06-13
After numerous restarts last night, sound not working.

On turning it on this morning, sounds does work?! This is like a gamble whether it's going to work or not!

Sam.

---

### Post by samwillc on 2012-06-13
Given up, reinstalled win7.

I'll reinstall ubuntu on a partition but regretfully, it's just not good enough to replace windows full time for me. Once the obvious sound issues are ironed out then I will give it another shot, was lovely to use compared to windows but I'll always go back to reliability in the end.

Sam.

---

