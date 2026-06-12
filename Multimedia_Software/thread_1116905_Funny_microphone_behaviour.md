---
title: "Funny microphone behaviour"
date: 2009-04-05
forum: Multimedia Software
---

### Post by deflagrator on 2009-04-05
I am running Ubuntu 8.04.2. I cannot get my microphone to work properly though. When I have it plugged in and tap it with my finger, I can hear that on my speakers. When I blow gently into my microphone, I can hear that too on my speakers. However, no speech gets amplified unless I get so close to the mic that it is virtually in my mouth.

What is ridiculous is that this behaviour occurs irrespective of what the volume settings are. i.e. whether the Master, PCM, Front, Front Mic are turned on or off. In fact, I get the above sounds (tapping, blowing and talking really close to the mic) from my speakers even when they are muted!

I am running the Alsa mixer. I haven't been able to figure out what's going on. Someone please throw light. I want to use my mic for recording sound into wav files using Audacity, and for using Skype. These haven't been possible yet.

I have this problem while using two Logitech microphones, both of which work fine on Windows XP. So I know that my microphone is not the problem. I have the sound card that came with my Intel D945GCPE mother board. The manual describes it as having a Realtek ALC662 audio codec.

dsv

---

### Post by ongun.kanat on 2009-04-05
did you try the speaker icon at the panel?
double click it and select your sound device.check the microphone is not mute and volume isn't 0.

---

### Post by tripolitan on 2009-04-05
Assuming that alsa-base and alsa-utils are installed. In terminal, type alsamixer then hit F5. 

Using the arrow and spacebar keys, select mic boost then activate it using m key (m toggles mute). Adjust mic volume to your liking then do ctrl-c then type

sudo alsactl store
(this stores your soundcard settings so you wont have to go through the setup again).

p.s. Skype, depending on your setup, could override these settings every time it is started, please make sure that skype is not running, or not even in the system notification area while running this test.

---

