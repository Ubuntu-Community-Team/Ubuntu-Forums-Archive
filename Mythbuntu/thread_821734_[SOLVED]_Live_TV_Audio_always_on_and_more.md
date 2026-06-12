---
title: "[SOLVED] Live TV Audio always on and more"
date: 2008-06-07
forum: Mythbuntu
---

### Post by mark467 on 2008-06-07
Forgive me in advance for possible dumbness ;)
I am a newb to linux and am having some issues with Mybuntu 8.04
I have solved most of them with this great forum and all the great posts. 
The few remaining issues are 

Live tv sound is always on and when you select watch live tv you get the audio twice (one delayed) 

Not the greatest picture quality and a funny line across top



Any help would be great

---

### Post by tgm4883 on 2008-06-07
Take a look here  [http://mythtv.org/wiki/index.php/Sound_Troubleshooting](http://mythtv.org/wiki/index.php/Sound_Troubleshooting)

It's cause you have a software encoder card.

---

### Post by mark467 on 2008-06-07
What they suggest dosent seem to be the problem with the audio:

 Echo on audio input

For the VIA 8237 chipset used on the Biostar PT880 Pro-A7C motherboard (and probably others), the audio external line input can produce an echo effect if the "Duplicate Front" mixer channel is enabled. This channel is easily disabled via alsamixer. Be sure to mute the channel, not just turn down the gain on it. For Yamaha DS-1 (YMF724F) you have to mute audio recording from "Wave Capture". 

Mine is already muted in alsamixer

---

### Post by mark467 on 2008-06-07
What they suggest dosent seem to be the problem with the audio:

Echo on audio input

For the VIA 8237 chipset used on the Biostar PT880 Pro-A7C motherboard (and probably others), the audio external line input can produce an echo effect if the "Duplicate Front" mixer channel is enabled. This channel is easily disabled via alsamixer. Be sure to mute the channel, not just turn down the gain on it. For Yamaha DS-1 (YMF724F) you have to mute audio recording from "Wave Capture".

Mine is already muted in alsamixer

---

### Post by mark467 on 2008-06-07
BTW I also have a pinnacle remote kit for windows if anyone knows how to get that one working

---

### Post by tgm4883 on 2008-06-07
What tuner do you have?

---

### Post by mark467 on 2008-06-07
I have a tv wonder pro with the 1/8th inch mini plugged into the line in on my mb audio

---

### Post by KillerKiwi on 2008-06-08
You need to mute the line in....

I have a similar setup and if the line in is not muted you can hear the tv tuner sound when its recording

---

