---
title: "How can I tell from CLI if audio is playing?"
date: 2011-01-18
forum: Multimedia Software
---

### Post by roobarb! on 2011-01-18
Hi all,

I have a little touchscreen device that runs Ubuntu 10.10 (Desktop) and some music playback software called SqueezePlay. After some time idle, SqueezePlay's sound output becomes unreliable and the software needs restarting. I'd like to do this from a cron job, and have done so in the past, but occasionally it will quit the software even if I'm using it at the time.

So, my question is how can I detect whether audio is being played back in a way that I can make use of in a cron job? All I'm looking for is, every 4 hours, "If SqueezePlay is running and there's audio playing, do nothing. If SqueezePlay is running and there's no audio playing, quit and relaunch SqueezePlay".

Any help greatly appreciated! :)

   Andy.

---

### Post by roobarb! on 2011-01-24
Sorry to bump, but does anyone have any clues on this?

---

### Post by Cheesehead on 2011-01-24
Does Squeezeplay feed audio through, say, pulseaudio (or another audio system)? If so, does that audio process end when Squeezeplay flakes out? Tracking that audio process would be a simple method.

---

### Post by roobarb! on 2011-01-31
It all goes through ALSA, so far as I can tell. I know it has 'disagreements' with PulseAudio...

How would I go about tracking it in ALSA? I'm afraid I know very little about the audio internals of Ubuntu!

---

