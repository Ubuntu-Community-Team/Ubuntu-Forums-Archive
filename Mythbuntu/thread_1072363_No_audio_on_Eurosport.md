---
title: "No audio on Eurosport"
date: 2009-02-17
forum: Mythbuntu
---

### Post by ikke2808 on 2009-02-17
Hi all,

As I am trying to get all working properly I am stuck now with my audio. 

almost all channels work and audio is available except some like Eurosport, Animal Planet and Euronews.

The message I get in mythfrontend.log is:
Opening audio device 'default'. ch 1(1) sr 48000
Opening ALSA audio device 'default'.
AudioOutput Error: Channels count (1) not available: Invalid argument
Unable to set ALSA parameters
NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!

The last line I get numerous times until I switch channel. 

For channels that work the difference is Opening audio device 'default'. ch 2(2) sr 48000 against Opening audio device 'default'. ch 1(1) sr 48000.

Has anybody any idea, cause I tried a lot of settings where the only consistent situation is no audio for all...

Cheers

---

