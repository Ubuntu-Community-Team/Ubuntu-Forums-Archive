---
title: "Steinberg UR28M Reverb/echo Effect?"
date: 2019-02-12
forum: Multimedia Software
---

### Post by bass+weaver on 2019-02-12
Hey there, I'm looking for help getting my Steinberg UR28M working on Ubuntu [FONT=Verdana][COLOR=#000000]18.04.1 LTS 64 bit ([/COLOR][/FONT]AMD® A6-7400k radeon r5, 6 compute cores 2c+4g × 2).
For the most part the interface works as intended out of the box, but I'm having issues with playback being very echo-y, any help with this would be appreciated.

---

### Post by Autodave on 2019-02-13
Since no one else has jumped in........are you sure that the reverb isn't coming from the unit instead of being caused by your PC?  How are you connecting to the PC: what kind of cables?

---

### Post by bass+weaver on 2019-02-13
I'm using all the cables that come with it, and the interface works fine when not connected to the computer or on a windows device. I'm nearly positive it's not coming from the interface, as I recorded some audio (via audacity) and exported it to mp3 and it played back fine on other devices. Also the reverby sound is clippy and not at all like the in the box effects that generally require the app to work.

What I think (as such take this with a grain of salt) the issue is Ubuntu is expecting a 5.1 audio setup when the interface only takes a stereo output, based off of the number of channels in the sound test Ubuntu sound settings. It's probably caused because the interface has different outputs for different mixes, set up in stereo pairs, essentially. Is there any way to change the number of channels Ubuntu/ALSA/Pulseaudio is outputting to for a particular device?

---

### Post by Autodave on 2019-02-13
Help me to understand.  Are you hearing this choppiness when playing back?  Playing back what?  Are you going PC -> Steinberg -> speakers?

Please tell me what cables you are using: USB, RCA, 1/4", etc.

I have no guarantee that I can help, but I do a lot of stuff with audio recording (18 channels through Allen & Heath digital mixer) so I have a little knowledge.

---

