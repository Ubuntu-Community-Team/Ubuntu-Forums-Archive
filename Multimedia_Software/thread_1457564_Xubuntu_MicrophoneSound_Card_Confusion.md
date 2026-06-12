---
title: "Xubuntu Microphone/Sound Card Confusion"
date: 2010-04-18
forum: Multimedia Software
---

### Post by napecuas on 2010-04-18
I recently installed xubuntu 9.10 on an Acer Aspire One (1.6GHz, 1GB, 8GB SSD) in order to speed it up and it has worked great out of the box. It takes less than a minute to boot, connect to the internet and have a browser open ready to go, it runs smoothly and I didn't have to install any drivers! After many years using Windows I was very impressed, apart from an issue with the microphone or sound card.

I just tried to run Skype for the first time and although I am getting sound out of the speakers, the microphone is not picking anything up.

The first thing I tried was the settings within Skype. Under sound devices the microphone input is listed as "PulseAudio server (local)". Next, I went to the mixer which brings up many different sound card options.

"HDA Intel (Alsa mixer)" 
"Realtek ACL268 (OSS Mixer)" 
"Playback: Internal Audio Analog Stereo (PulseAudio Mixer)"
"Capture: Monitor of Internal Audio Analog Stereo (PulseAudio Mixer)"
"Capture: Internal Audio Analog Stereo (PulseAudio Mixer)"

I have tried turning the input on all of these up to maximum but none of them seem work or come up as options under the sound settings in Skype. I only offers the default choice of "PulseAudio server (local)".



How can I configure skype and/or the soundcard to work with the microphone?

Oh and one tiny other thing. Everytime I boot, the system volume is always muted as well as having the mixer all the way down. Is there any way of changing the default volume level?

Cheers

---

### Post by kostkon on 2010-04-18
Install the PulseAudio Device Chooser utility and use the pulseaudio volume contro.

---

### Post by napecuas on 2010-04-18
> **kostkon said:**
> Install the PulseAudio Device Chooser utility and use the pulseaudio volume contro.

I've installed that and I'm still not having any luck with it.

How exactly should all of the settings be for it to work? I can't seem to get it right.

---

### Post by lidex on 2010-04-18
Scroll down to the "Skype" section of this page:
[http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")

Have you tried alsamixer?

---

