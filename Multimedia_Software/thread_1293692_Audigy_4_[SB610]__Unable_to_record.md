---
title: "Audigy 4 [SB610]  Unable to record"
date: 2009-10-17
forum: Multimedia Software
---

### Post by lennyw on 2009-10-17
I am trying to get basic audio recording going from the line-in port of the Audigy 4 sound card but with no luck so far.

I checked some of the previous threads on this subject but was unable to get it going. I'm using Jaunty. 

I have the headphone output from a personal cd player patched into the line-in port of the Audigy 4 card.

My gnome mixer (e.g. click the speaker icon on the panel and then click the volume control button) has the following device selections: 1. Audigy 4(Alsoa Mixer), 
2. Sigmatel STAC9750,51 (OSS Mixer), 
3. Playback:Audigy 4 ADC Capture Standard PCM Playback (PulseAudio Mixer), 
4. Capture: Monitor of Audigy 4 .... PuseAudio Mixer, 
5. Capture: Audigy 4  ....(PulseAudio Mixer)

Only Devices 1 and 2 (above) have preferences for Line-in. The Audigy mixer has the line-in disabled,the oss mixer has it enabled. When I use the basic sound recorder applet that comes with Ubuntu, on playback I get a constant tone (around 600 Hz) on the externally connected speakers. Curiously, the gnome mixer will accept a mouse click to enable line-in on the audigy (device 1 above) mixer and disable the line-in on the oss (device 2 above) mixer, but when I re-open the gnome mixer the states have reverted to oss enabled and audigy disabled.

This is all confusing and  frustrating.

Obviously I'm interested in doing more than using the recording applet. In fact I intend to use a small stand alone web server app called WebSDR to serve an external software defined radio's audio on the Internet. This well debugged and stable program needs OSS (either through the oss-compat package or by being launched through aoss) for it to work correctly. 

But first things first. How do I make line-in record a simple external audio feed on the Audigy 4 sound card???

Any help will be much appreciated!

--Lenny Wintfeld
NJ USA

---

### Post by ene_dene on 2009-11-07
Yes, I agree, this is really irritating. On Ubuntu 9.04 to have sound you had to check the digital jack for audigy 4, and on 9.10 you need to select "Digital Stereo Duplex". But as for recording, I haven't found the solution anywhere.

---

