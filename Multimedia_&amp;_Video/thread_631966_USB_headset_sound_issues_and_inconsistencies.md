---
title: "USB headset sound issues and inconsistencies"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by tmoldovan on 2007-12-05
Hello,
This is my problem: 
- I would like to use my USB headset as the main sound output device. I can go to System/Preferences/Sound and select USB Audio for all the categories. I can also do a test and hear a beep.
However, I hear no other sounds, except in Rythmbox audio player. For example, in System/Preferences/Sound/Sounds there are a couple of sounds for login and logout that I can click "play" on, and when I do, I hear nothing.

I have gone (doubleclicked) on the speaker icon and changed the device from the default one to my USB headset (alsa mixer), but that doesn't seem to have any effect.

My hardware:
intel motherboard with built in audio, another PCI audio card, and my USB headset.
(I want to use the headset mainly for a VOIP game I play...)

Ubuntu 7.10

A couple of other things I've noticed, maybe they can help diagnose:
in System/Preferences/Sound when I test my sound capture, I can actually hear myself through the earphones (as is expected) but after a few seconds, I get an error message:
Failed to construct test pipeline for 'gconfaudiosrc ! audoconvert ! audioresample ! gconfaudiosink profile = chat

And if I go into Applications/Sound and Video/Sound Recorder, I get the "Your audio capture settings are invalid. Please correct them in the Multimedia settings.

I get no sound from any of the games in the Applications/Games.

Thanks in advance.

---

