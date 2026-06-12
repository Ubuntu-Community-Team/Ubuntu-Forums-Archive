---
title: "Youtube Microphone Issue"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by Syr0 on 2007-09-25
Hey everyone.

I'm having issues with my microphone. My sound card runs off the **snd-ak4531** driver, and when in **Sound Preferences**, I try and test **Sound Capture** with the ALSA, OSS and hardware drivers, but it fails, giving me this issue:

[HTML]gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.[/HTML]

Sometimes, selecting OSS as the microphone driver appears to work, I get a box with [OK] on it, and a half-filled meter bar. What's the deal?

Furthermore, when I try to use Quick Capture on youtube, my microphone doesn't register at all, although I can use Audacity to record off it, and the same with VLC (VLC also won't record off my webcam with any other brightness settings that the horrible murky default which i can't change :mad: )

In terminal, firefox and alsa give me this error message:

[HTML]ALSA lib pcm_dmix.c:803:(snd_pcm_dmix_open) The dmix plugin supports only playback stream[/HTML]

After changing or meddling with some of the settings in **Sound Preferences**, I get these messages in the terminal:

[HTML]- using device default
- using device default[/HTML]

[LIST]
[*]How can I make my microphone work on Sound Recorder
[*]How can I make it work with youtube's quick capture?
[*]What's the reason for the problem I'm getting when I try to configure it in Sound Preferences?
[/LIST]

My firefoxrc file uses " dsp="alsa" ", and quick capture still won't register my microphone if i change it to: "aoss".

Help?

---

