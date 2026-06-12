---
title: "Is this normal for spdif output?"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by exactopposite on 2008-01-06
Let me start by saying that I have sound going to the receiver, but i'm just trying to make sure it's working properly.  I'd be content to leave it as it is either way for now, but i'm curious.  This is the first time i have used spdif from a computer, so i don't have any other expeience to compare this to.

I have a pc connected to my reciever via spdif for listening to music over my surround sound system.  I get sound output to the receiver but it seems that none of the settings in alsa mixer do anything. in  the alsa mixer i only get sound out from the spdif when i check of the box for iec958 on the switches tab AND mute  the slider for "IEC958 Playback AC97-SPSA".  Other than those 2 settings nothing else in alsa mixer changes anything. However if  i adjust the volume in amarok, the volume changes. If i change the settings in alsa and/or the amarok xine settings to 6 channel or stereo there is no change.  I'm not sure if this is becasue i'm just using mp3's or what. 

As it is, it serves my purpose, but i'm not sure if this is normal. I control the pc remotely and use it to play music, no video. It's only used for that and as a server for my lan so i don't have any speakers connected to it. I only use the spdif out. 



Gutsy 32
mobo:
Epox 9npa+ Ultra (i think that's right, it's been a long time since i bought it)
nforce4 ultra chipset
audio devices:
nvidia ck804
iec958

---

### Post by Yellow Pasque on 2008-01-06
mp3's aren't encoded with surround, so unless you run some kind of stereo-cloning config, you won't get surround sound.

---

### Post by exactopposite on 2008-01-06
> **Temüjin said:**
> mp3's aren't encoded with surround, so unless you run some kind of stereo-cloning config, you won't get surround sound.

yeah that's no biggie as the reciever will encode it. is it normal that none of the other settings in the alsa mixer do anything?

---

