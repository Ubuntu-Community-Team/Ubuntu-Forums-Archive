---
title: "Default Sound (PulseDriver) doesn't produce sound but OSS does"
date: 2009-05-04
forum: Multimedia Software
---

### Post by pwab on 2009-05-04
Hi,

I installed Jaunty last week and everything worked like a charm, including sound. This issue then developed subsequently, and I don't know what I did to cause it.

I have a Compaq Presario with some kind of internal sound device. In the sound preferences, I have a list of options for each output/input device. The first is autodetect, then a few that has the name of my sound device in it (HDA Intel CONEXANT with OSS in there somewhere) Then one for ALSA, OSS and PulsAudio each. 

If I select one of the devices with the name of the soundcard in it, and press the Test button, I hear the test sound. If I set the 'Autodetect' option, I only hear a faint buzzing noise. this is the same noise that I hear if I select PulseAudio. The ALSA option(s) produce errors. 

What happens in my system is that any sound that is played to the default device produces that buzzing sound. IE, If pidgin gives a notification sound for a chat, I get the buzzing, login sounds buzzing etc. For Media players like VLC I have to explictly set the sound output device to use the OSS drivers/devices and then the sound works.

Is it possible to set the Default device (presumable PulseAudio) to use OSS and then have sounds on my system? Or, is it possible to 'reset' the sound configuration to the same config it had after installation?

---

### Post by pwab on 2009-05-04
Sorry for wasting all your time. I fixed the issue with a slap to the forehead and increasing the volume level on one of the sliders...

---

