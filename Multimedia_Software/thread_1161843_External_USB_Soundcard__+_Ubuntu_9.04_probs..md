---
title: "External USB Soundcard  + Ubuntu 9.04 probs."
date: 2009-05-17
forum: Multimedia Software
---

### Post by w0lla on 2009-05-17
Hi 

first timer here, and more or less a first timer on ubuntu too. ):P

I have a HP 2510p laptop with ubuntu 9.04 installed, in my stereo setup I have a external Dac with a USB input which is connected to my stereo amp. I would like to be able to use my laptop as a source occasionally. When I connect it through the USB, Ubuntu does see it automatically. When go into the sound configuration in preferences I can choose my DAC, when I then press "test sound", I do hear the test sound coming through. But even if I put all the sound settings to my DAC, mp3 wont play through it, using amarok... 

But I would like to keep the settings on automatic, so that if I unplug the USB DAC it will switch to the inbuilt soundcard and vice versa. Or if there would be a music player which lets me choose the sound output manually, like you can do in foobar2000. 

thanks.

---

### Post by kostkon on 2009-05-17
Yes, Ubuntu uses *PulseAudio* and indeed the audio streams fallback automatically to the next available device when the default becomes unavailable.

The thing you need to do is to put your sound plaubacks (and inputs if you like) in your sound preferences (i.e. S*ystem &#8594; Preferences &#8594; Sound*) back to *Autodetect* and then install the *PulseAudio Device Chooser* utility which will allow to set the Default input and output devices and some more things.

For more info, check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by w0lla on 2009-05-18
downloaded pulseaudio device chooser, now I can choose my usd dac as default, and move any streams to it and it works. But it still doesnt switch automatically, having all the settings in sound preferences on Automatic (also tried on pulseaudio). If I plug in the dac I have to move the stream to it, if I want to use the onboard soundcard I have to move the stream back to the onboard. If I unplug my USB dac without moving the stream back to the onboard soundcard Rhythmbox doesnt find any output.

---

