---
title: "PySolFC and Pulse Audio don't cooperate"
date: 2009-12-06
forum: Multimedia Software
---

### Post by jimdb on 2009-12-06
I did a full install of Karmic a few weeks ago and this is my first issue. 

I installed PySolFC (solitaire game) and the sound plays on the on-board sound card on my laptop instead of using the Audigy card and external speakers which are my normal defaults when at my desk. 

I installed the padevchooser package and it is completely unaware of PySolFC when it is running. I assume PySolFC is an OSS application because it does uses ossaudiodev.open ('w') (Python program).

The padsp wrapper doesn't work. Neither does the oss-compat package, which was suggested in another thread.

The only other clue I have is that when Rythmbox is running, I get the error Device or resource busy: "/dev/dsp".

Does anyone have any suggestions? I have no idea if this is problem is PySolFC, Pulse, Python or Ubuntu. For now I can use PySolFC with the sound muted, but I would like a real solution.

Thanks.

Jim

---

### Post by ibuclaw on 2009-12-06
Two suggestions:

1) Start PySolFC with the oss-wrapper for ALSA.
```
aoss PySolFC
```
2) Tell pulseaudio to suspend so PySolFC is allowed to have direct access to /dev/dsp
```
pasuspender PySolFC
```

Regards
Iain

---

### Post by jimdb on 2009-12-06
Thanks for your reply. I tried both suggestions, but neither suggestion fixes everything.

aoss allows PySolFC to run without errors, until I open the PulseAudio Applet to use the volume control. Then I see the /dev/dsp busy error. I also have no way to control the volume.

pasuspend allows PySolFC to run but shuts down all other audio as expected. The sound is still on the wrong audio device.

Neither approach allows me to grab the PySolFC audio and run it through my Audigy card where it belongs. I get PySolFC audio on the built-in speakers and other audio (eg Rythmbox) on my Audigy card and external speakers.

I think I will run PySolFC with the sound muted for now. I have PySolFC, Rythmbox and the Pulse volume control running with no funny errors as long as I keep PySolFC muted.

It doesn't appear that Python supports PulseAudio directly so there is no easy fix for the application.

Jim

---

### Post by Yellow Pasque on 2009-12-06
Are you using v2.0? (just came out a couple days ago)

python-pygame uses SDL for audio, and you can install the libsdl1.2debian-pulseaudio package and force SDL to use Pulse.

---

### Post by jimdb on 2009-12-06
The problem is fixed.

I installed libsdl1.2debian-pulseaudio, which uninstalls libsdl1.2debian-alsa (hope nothing else breaks).

I installed python-pygame and started pysol with the option --sound-mod=pygame.

Now when I start pysol, I see a new volume control slider for "python: Simple DirectMedia Layer on Audigy2 ..." on the Volume Control Playback tab. The audio is routed to the Audigy card and the external speakers by default.

The PySolFC version is 2.0.

Thanks.

Jim

---

