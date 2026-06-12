---
title: "PulseAudio, routing of audio to loudspeakers"
date: 2010-08-24
forum: Multimedia Software
---

### Post by kim_t on 2010-08-24
Hi,
 
I have made a LADSPA plugin that I want to apply for the PC loudspeakers only. I do not want to pass the audio through the LADSPA plugin when listening through headphones.
How do I accomplish that?
 
Normally when I load the plugin for testing I just use a command like this:
load-module module-ladspa-sink sink_name=ladspa_out master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=myplugin control=1...
 
If I could just enter a "master" that only pointed to the headphones it would solve my problem.
 
If it is not possible then how do I detect in my LADSPA plugin if the headphones are connected? I assume there is some API that I can use?

I have also sent an email with this question to:
	  [EMAIL="pulseaudio-discuss@mail.0pointer.de"]pulseaudio-discuss@mail.0pointer.de[/EMAIL]
 
/Kim

---

