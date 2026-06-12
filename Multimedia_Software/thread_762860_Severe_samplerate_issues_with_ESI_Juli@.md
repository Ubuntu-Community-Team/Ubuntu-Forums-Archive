---
title: "Severe samplerate issues with ESI Juli@"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Kupo on 2008-04-22
When using the default samplerate given in Dmix (44100Hz), the audio output sounds unclear and downright horrible on my ESI Julia. By setting it to 88200Hz, it reaches its optimum, and here's where my confusion begins. The audio source I use only is in 44.100Hz (tried both uncompressed and compressed audio), so it shouldn't be necessary to resample it upwards using dmix. Resampling uses way too much cpu, and i'm trying to avoid that. What could be the source of my problem? ALSA has always been a black box to me - so if something sounds unclear, please ask me for clarification. Help is much appreciated.

Also, i have yet to figure out where to select the hardware samplerate of my audio card.

I'm using the release candidate of Hardy Heron now, but i've had the same problem since i started using Ubuntu Feisty Fawn.

---

### Post by kch on 2008-09-06
I have the same problem

---

### Post by IceMood on 2008-10-15
oh~ God :( I almost buy it!
isn't any clue yet?

---

### Post by silentb on 2008-11-03
use intrepid (alsa 1.0.17). alsa 1.0.16 has known problems.

---

