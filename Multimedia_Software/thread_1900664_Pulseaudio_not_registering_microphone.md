---
title: "Pulseaudio not registering microphone"
date: 2011-12-26
forum: Multimedia Software
---

### Post by johnmic on 2011-12-26
Hi,

I'll try to be brief - I'm using an Acer Aspire One D255E netbook, which I have managed to install Ubuntu 11.10. Everything is running fine...apart from the microphone with Pulseaudio.

The sound is picked up perfectly well when I use Sound Recorder, but it seems that Pulseaudio just refuses to acknowledge that I have a microphone. I've used 'paman' to increase the pick-up on the audio to ~400%, but that just increases the level of white noise I receive.

As far as I can tell, this is a Pulseaudio problem, but I've been Googling for 2 hours to no avail on how to get Pulseaudio to speak with the rest of my computer.

Any help is greatly appreciated - let me know if more info is needed.

---

### Post by inobe on 2011-12-26
yeah, pulse is being a prick, the gui part at least, it likes to hide stuff to a point where it's becoming irritating.

you can do two things.. install pavucontrol, you can run alsamixer in terminal.

i bet it's muted, or the level is way down, another possible reason, smart 5.1 is enabled, if that applies to your setup* not sure on that.

---

### Post by johnmic on 2011-12-27
Thanks for the rapid reply. Unfortunately, I don't think either of those are the solution - alsamixer already has everything up to maximum, and auto-mute disabled just for good measure. However, as far as pavucontrol goes, it's all set up appropriately, but it doesn't seem to register any input from the microphone (on either the Analogue Microphone or Analogue Input setting - checked both for good measure).

From this, it looks like Pulsaaudio just isn't recognising the microphone, whereas other, non-pulseaudio, mechanisms, are. Is there a way to change this?

---

