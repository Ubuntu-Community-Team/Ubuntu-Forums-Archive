---
title: "sound issue, help!"
date: 2008-04-26
forum: Multimedia Software
---

### Post by guy.thingy on 2008-04-26
alright let tell you the whole story...
i have a sound card(x fi extreme audio) and on board sound..and im trying to get my audio working correcrly here is how it is right now...

1. if im using alsa my audio works in wine, amarok, etc except FIREFOX.
2. if im using pulseaudio i have to plug my speaker to the onboard sound plug to get the audio working, but then the audio works when i download "libflashsupport" which is only for pulseaudio and now the sound in wine doesnt work...

now i would prefer not to use my on board sound and use my sound card, but then pulseaudio doesnt work and i dont get audio on firefox...so is there something like "libflashsupport" for alsa? or could i somehow make pulseaudio work with my sound card? i have tried playing around with devices in system -> pref -> sound but nothing...


thank you.

---

### Post by guy.thingy on 2008-04-27
over that 8 hours and still not someone attempting to help? great support guys, if im a n00b that doesn't mean you shouldn't be helping me..this what is the support forum section is all about helping people and then people helping others..

---

### Post by svaens on 2008-04-27
Sorry that I can't help you. 
I just sympathized with your plight because 

1. no one had yet answered you (although I was asleep for those 8 hours ;) ) 
and
2. I also have sound problems. 

I am beginning to have deep suspicions that Hardy wasn't ready for this new pulseaudio. My audio was super fine (well.. not perfect) in gutsy... 
And I understand what one of the things pulseaudio is about... better multi sound source support... (one of the problems I had in gutsy). 

So, while I agree that pulse audio is a good idea, and should be furthered. 
I think that perhaps it should be somehow optional. 
In fact, I see a bug opened with this same opinion:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/220759](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/220759)

What we need NOW are comprehensive instructions on just how to revert to the old sound system (successful removal of pulseaudio and reinstatement of the previous). I assume it is will not be as simple as apt-get autoremove pulseaudio, and installation of the other. 
And what was the other anyway? Eaudiod or something like that... 
I unfortunately am still new with linux, and cannot write this myself. 
anyone got the knowhow?

---

