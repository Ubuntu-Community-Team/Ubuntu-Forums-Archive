---
title: "No luck implimenting Pulse Audio system wide equalizer"
date: 2008-12-23
forum: Multimedia Software
---

### Post by sofasurfer on 2008-12-23
I followed the "HOWTO: PulseAudio Fixes & System-Wide Equalizer Support" instructions".

I followed parts A&C and then followed appendix D to add the equalizer.

I do not have an equalizer that I can see. Where do I find it if it exists? If it does not exist as of yet on my system, how do I find out where I screwed up. I have tried to do this 3 times and have had no luck.
 
Back in my Hardy 8.04 days I think this was the same thread I followed and at that time I did have a system wide equalizer. Is there a known problem getting the equalizer working in Intrepid?

Hmmmmm?

---

### Post by sofasurfer on 2008-12-24
Bump?

---

### Post by kostkon on 2008-12-24
I think (actually not even 10% sure) that you should see the plugins as output device(s) (sinks) in the *PulseAudio* volume control.

Thus, run the volume control and check if you can see device(s) named like *ladspa_out* or something similar in the *Output Devices* tab. If that's the case, you can then move any audio stream to one of this/these device(s) to apply the plugin that corresponds to this device.

The audio streams of the various applications running (only the ones that produce audio, of course) are in the *Playback* tab. Right-click on the one you want and select *Move Stream...* and in the list that appears you should see the device(s) for the plugins and any other hardware audio devices that you may have (e.g. soundcard, USB headset, etc).

I may be wrong, veeery wrong about this, so please, be kind to me... [-o<:oops::cry:

---

### Post by sofasurfer on 2008-12-24
I'll take it easy with you because you were kind enough to reply and give it your best shot. I appreciate it.

Under the volume control, under the "input device" and the "output device", each one has the following... "ALSA PCM on front:0 (ALC883 Analog) via DMA". Under this text there are a left and right volume (?) slider controls. When I start a audio stream, sliders also appear under the "playback" tab, along with "ALSA plug-in (firefox)): ALSA Playback".

I see where you say to right click to move the stream. But I do not understand what is meant to "move" a stream. I can play audio streams of any kind with out even knowing about this information. I haven't a clue what the purpose of this stuff is.
Am I missing a point or what?
Also, there is nothing resembling a equalizer anywhere.

As I stated earlier, at an earlier time, with 8.04, I had an equalizer and it showed up under applications>sound and video. All you had to do was click on it and the equalizer opened.

---

### Post by wolfen69 on 2008-12-24
is there a reason you are no longer using 8.04? if it is that important to you to have a working equalizer, perhaps go back to 8.04? btw, 8.04.2 comes out in 7 days. it will have all updates included and support for newer hardware. and if you need newer apps, you could always compile your own or enable the backports repos.

---

