---
title: "Alc262 audio"
date: 2010-12-10
forum: Multimedia Software
---

### Post by kazha on 2010-12-10
Hi hopefully you can help me
I've been struggling to get my sound card to work for a "quite a while"
So i have Benq P52 notebook with ALC262 sound card(alsa-base.conf->hda model set to hippo)
and i can't manage to make it work as i want
I've been on and off ubuntu for couple of years just because i could not get my audio work...(recording, real-time playback)
If anyone could help me i would greatly appreciate it
so i have a fresh install of ubuntu 10.10
i have tried to install jackd so i could work with rackarrack haven't been able to make jackd work so no rackarrack
no matter how i try to change config in qjackctl it gives me a lot of
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
-------
also i haven't been able to make recording through line-in(guitar) even sound recorder wont't show no response
though i get the sound out of speakers

I have tried a lots of things (lots of google ), but i'm thinking that my hands are too short sort of :( and i really don't want to go back to windows again just because i can't manage to make my audio work
If some more info is needed say, i will deliver it.

---

### Post by kazha on 2010-12-11
Ok huge facepalm for me.Solved the problem, so there wont be no need to go back to windows. :)
By adding "options snd-hda-intel position_fix=1" to alsa-base.conf
and _restarting pc_ ](*,)fixed it, jack works and i can record in ardour, and rakarrack also works. :)
Before tried just alsa force-reload that didn't work!

---

