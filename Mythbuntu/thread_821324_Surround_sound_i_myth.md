---
title: "Surround sound i myth"
date: 2008-06-07
forum: Mythbuntu
---

### Post by malaTG on 2008-06-07
Hi

Is there a good guide on how to set the sound correct in mythtv on Hardy Heron (8.04)? I suck at sound configuration and was wondering how it works for myth? Is pulseaudio used or does mythtv connect directly to alsa? 

I have a 5.1 sound projector and a spdif optical connection to it from my motherboard. Is there a way to see within ubuntu if it is sending a 5.1 signal? I have sound but since I have a sound projector I am unsure if it sends a 5.1 signal...

Thx in advance!

/Marcus

---

### Post by misterspider on 2008-06-17
Can you do a simple physical test? By that i mean play a dvd that you know has some easily detectable 5.1 sound. Like at the start of lots of movies they do a simple demonstration of Dolby Digital? 

In the frontend setup there is an option for audio: I chose

alsa:spdif

And then somthing like 

Maximum speakers: 2 Stereo  or 5.1

I have mine on 2 stereo but when i play a dvd in Myth, my Home Theatre receiver says the signal arriving is Dolby digital and the sound is definitely surround.

---

### Post by Lindsay.Mathieson on 2008-06-18
> **malaTG said:**
> Hi

Is there a good guide on how to set the sound correct in mythtv on Hardy Heron (8.04)? I suck at sound configuration and was wondering how it works for myth? Is pulseaudio used or does mythtv connect directly to alsa? 

I have a 5.1 sound projector and a spdif optical connection to it from my motherboard. Is there a way to see within ubuntu if it is sending a 5.1 signal? I have sound but since I have a sound projector I am unsure if it sends a 5.1 signal...

Thx in advance!

/Marcus

I've just been working with this :) I have 5.1 surround working with videos and DVD's in Myth.

First off forget myth for the moment, get 5.1 (6 channel) sound working with ALSA.

Fire up alsamixer, check which channels are present - you should have (from memory) Front, Center and LFE. If so, set the levels on them  to max. Also scroll to the right in alsamixer, there should be a numeric "channels" setting (probably 2). Set it to 6.

do ```
alsactl store
``` to save the settings.

A simple sound out test:

```
speaker-test -Dplug:surround51 -c 6 -t wav
```

Will test each 6 channels in turn, speaking the channel as it goes, .ie "Left Front", "Right Front" etc.

If the channels aren't present then we need to check your sound modules. What sound chip are you using? alsamixer should list it at the top left.

---

### Post by malaTG on 2008-06-18
Hi

Thank you for answering

I fired up the alsamixer and increased center and LFE volume, the channels were already set at 6 and then storedthe settings.

After that I ran

> speaker-test -Dplug:surround51 -c 6 -t wav


which gave me no sound at all. If I instead ran 

> speaker-test -c 6 -t wav


I get sound in the left and right front channel. Now I don't know what to do next?

Could it have something to do with the optical cable that I am using?

/mala

---

### Post by Lindsay.Mathieson on 2008-06-18
Forgot you were using spdif :(

try

speaker-test -Dplug:spdif -c 6 -t wav

---

### Post by malaTG on 2008-06-19
Hi

> speaker-test -Dplug:spdif -c 6 -t wav 

This solves the no sound issue but I still get sound only on my left and right front speaker i.e. stereo sound

/mala

---

### Post by Lindsay.Mathieson on 2008-06-19
> **malaTG said:**
> Hi



This solves the no sound issue but I still get sound only on my left and right front speaker i.e. stereo sound

/mala

Might be worth checking the setting and connections on your projector to check they are all set for 5.1

---

### Post by fenian on 2008-06-19
Have a look at the documentation [here]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF") I've used this method to get spdif working.

---

### Post by malaTG on 2008-06-20
> **Lindsay.Mathieson said:**
> Might be worth checking the setting and connections on your projector to check they are all set for 5.1

I've checked this and I am pretty sure that everything is correct, the decoder indicates that it gets a pcm-signal and I have the decoder in "5-beam" mode(I have a soundprojector).

---

### Post by tedkel on 2008-06-24
I have been playing around with getting sound working on my mythbox for about 3 weeks now and need some help please.

I have worked through everything including getting the remote working perfectly however sound is driving me insane.

I have onboard ALC889A realtek sound on a Gigabyte GA-MA78GM-S2H MB. I have the video out using HDMI but have a normal stereo out cable carrying the sound as I have read that HDMI audio is almost impossible to setup in Hardy.

ALSA recognises my sound as ALC885 but have read in my searches that this should be OK. In aplay it shows as an ALC882

I have installed ALSA and set all the settings to ALSA:default and Default within the myth frontend general setup, and sound out is set to stereo as I am outputting to a LCD TV.

When I play a DVD (using the internal player) I get low sound that causes the video to be jumpy, same in digital TV. In analogue TV I get no sound at all.

I can play DVD's in VLC perfectly fine so general audio seems OK.

My Sound devices in aplay -l are;

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help or point in the right direction would be much appreciated.

Thanks.

---

