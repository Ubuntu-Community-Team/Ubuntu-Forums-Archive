---
title: "HTPC/Digital audio problems"
date: 2011-06-27
forum: Multimedia Software
---

### Post by GravityGilly on 2011-06-27
I recently built an HTPC using a Sandy Bridge Intel Core i3, running 11.04. I'm using HDMI to output both sound and video from XBMC, and streaming video/audio to the machine via DLNA/UPnP from another machine on my local network.

This all works fine, but there's a weird quirk: if I'm playing media that has "digital" audio (i.e. 5.1 surround sources, e.g. DTS, DD, AC3 etc.) I have to switch to the "Analogue 5.1 surround" output option in Pulse in order to get sound. If, however, I'm playing something that only has stereo sound (e.g. an MP3, or a movie that has stereo sound) I have to switch to the "HDMI digital stereo" option in Pulse in order to get sound.

This obviously isn't ideal (I want to get to the point where I'm exclusively running XBMC, let alone fiddling around with the audio settings in Linux every other file) and I have no idea why I should have to make these switches in the first place. Any ideas?

---

### Post by thaelim on 2011-08-25
You have probably resolved your issue by now, but in the interests of helping others with the same setup, here are the settings that worked for me (on identical hardware):

In XBMC Audio settings, I set the output mode to Optical/Coax. Speakers is set to 5.1. I then set a custom audio device and enter 'hdmi' (without quotes). Same for passthrough device - set custom and enter hdmi. This then works perfectly for any audio source I've been able to test (stereo PCM, DTS, DD5.1 etc etc).

Edit: I should add that I don't touch PulseAudio's settings at all. In fact PA does not even recognise that I have an HDMI audio output available.

---

