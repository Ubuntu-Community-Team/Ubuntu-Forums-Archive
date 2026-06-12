---
title: "jack Who?"
date: 2011-01-19
forum: Multimedia Software
---

### Post by hartz on 2011-01-19
I've googled arround a bit about jackd, purely because it is a pre-requisite for "jack timemachine". There seems to be quite a bit of misconception about jackd-vs-pulseaudio-vs-alsa-vs-oss-vs-esd-vs-etc and I have a few questions before I just go and install jackd.

Firstly, I understand that it overlaps in functionality with PulseAudio, and that there are some isues in running both at the same time.  Also I understand that audio programs need to be made aware of which sound server they should use.  For some programs there are plugins to allow them to connect to various sound servers.  Others have an option in a preferences to select the sound server.  Others require more work and others are incompatible with some sound servers.

I don't want to have to remember every time I try out a new program that I need to check whether it is compatible with jackd ... so I will likely remove it again after using it.  

Unless, and here comes my question: Is there an easy way to switch between PulseAudio and Jackd?  Maybe an applet similar to the network management tool?  Which utilities should I install to be able to see what is going on, what is active, etc in "sound land" in my computer?

Or are my fears largely unnecessary?  Does leaving both sound servers active in my desktop actually have any real or difficult to spot, or subtle disadvantages or problems?  Performance issues?

Many of the articles try to banish myths about requirements, benefits, disadvantages, etc, and much of these articles that I've found are old (circa Ubuntu Hardy, etc) so maybe much of these incompatibilities have since been ironed out?

Thanx,
  _Johan

P.S. I seem to have a more-or-less once-off need for "jack timemachine", so if there is a good PulseAudio alternative to it, or a way to use timemachine without jackd, please let me know.  I need something which I can set to record into a 10-minute ring-buffer.  Then when my peacocks call in the morning I can get up and go stop the recording.

---

### Post by cchhrriiss121212 on 2011-01-19
Jack is for pro-audio, music editing and production with low latency. Pulse is for regular stuff like firefox etc with no consideration for low latency. 

You do not need to run both at the same time, if you start jack, pulse is suspended so there are no issues having them both installed on your machine. Jack only does something if you tell it to, you need to start it up manually and tell it where you want your connections to go.

Having seen your other thread I don't think you need jack at all. Audacity is the best choice, it has a sound activated recording function which would allow you to capture the audio you need at a user defined dB level. After installing go to:
Edit>Preferences>Recording

---

