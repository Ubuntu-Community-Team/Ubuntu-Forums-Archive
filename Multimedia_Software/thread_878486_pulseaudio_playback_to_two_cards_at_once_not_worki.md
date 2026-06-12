---
title: "pulseaudio playback to two cards at once not working"
date: 2008-08-02
forum: Multimedia Software
---

### Post by &#12465;&#12452;&#12488; on 2008-08-02
I just installed an old Soundblaster card in my box today, for use with headphones to get some serious volume. The motherboard has an integrated Intel HDA audio controller which I use with speakers.

Playback to both devices at once should work. Both show up in the pulseaudio manager application, but looking at the volume meter, only front:1 is getting some playback here. Soundblaster became hw:0 in alsa, while intel hda is hw:1. In PulseAudio manager, the soundblaster shows up as "ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA". While "Multichannel Playback" in System &#8594; Preferences &#8594; Sound produces sound on the Soundblaster only.

ADC Capture/Standard PCM Playback in Sound Preferences gives me "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback." I assume that's why it doesn't produce sound with pulse either. Does anyone have some ideas about what's wrong with this?

---

