---
title: "Ubuntu Studio: JACK dies and kills clients."
date: 2008-10-24
forum: Multimedia Software
---

### Post by The_Marlboro_Man on 2008-10-24
Hi!.

I recently switched from my old Windows-based home-studio setup to Ubuntu Studio, just to see how it feels to work using other tools and to get rid from moral dilemmas.

My computer: A Compaq, dual core (Intel, 2.8ghz) with 1Gb Ram and an onboard Intel sound card. I am using Ubuntu Studio 8.10 and an external Tascam US-122 sound unit.

So, I succesfully managed to setup and get the Tascam sound card to work with Ubuntu Studio (following the how-to's) but never managed to get JACK to work properly. It took a lot of efforts to make JACK run (instead of just freezing my computer or not wanting to start) and when I finally managed to it is behaving... strangely.

I am using (rather, trying to use) Hydrogen to test the whole JACK thing. I'd swear I only managed to hear output once for a few seconds. Every now and then JACK dies. Sometimes it dies with a "Alsa poll timeout error, polled for X usecs" and most of the time it just closes, disappearing from he tray and closing Hydrogen on the way.

I am not exactly sure of what's happening since I can't see a log of those happenings but they happen very very often. Usually I can get JACK to run for a few minutes (running, but I can get no output) before one of the two problems happens. 

My JACK settings are at "Real-time" (using realtime kernel), "Force-16" and the only amount of frames and periods I managed to get JACK to run with (most of the other settings will either fail to "connect to JACK" or will just result in a lot of fan noise and a total freeze of my computer (not even the REISUB trick will work!!!).

Anyone experienced with JACK willing to help?. Any valuable tips?. Please, bear in mind that most of the time I do not really "know" what I am doing with JACK (Windows creates bad habits, doesn't it?). I'll try and catch up with the thread later tonight. Until then every bit of help is appreciated and much thanked for in advance.

---

