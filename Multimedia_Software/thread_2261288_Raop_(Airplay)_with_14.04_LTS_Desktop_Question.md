---
title: "Raop (Airplay) with 14.04 LTS Desktop Question"
date: 2015-01-17
forum: Multimedia Software
---

### Post by Hugh_Barstead on 2015-01-17
Hello again, once more I turn to the members of this learned forum for information.

I am new to Ubuntu but so far have been able to accomplish almost everything I want to do with my computer (Dell Inspiron 15-7537). My current goal is to be able to stream a couple of live internet radio stations from "back home" to my audio system. The relevant components in the audio system are a Pioneer SC-71 receiver (Airplay compatible) and an Apple Airport (version 2) acting as a bridge to the Pioneer (the SC-71 has no built in wifi).

To this end I researched and found the Raop Module for PulseAudio, installed it and the PulseAudio Preferences module from the Ubuntu Software Centre, rebooted and voila! The SC-71 and the Airport show up as options in the Sound panel in System Settings.

Sadly, although I can select the sources, neither the receiver nor the Airport respond to the connection attempt. I further installed the PulseAudio Volume Control module, but this did not help - the receiver devices simply do not react at all to the connection attempt.

More research revealed confusing results. Some people claim to have this system working, others claim it is broken. One source describes a difference between Airplay version 1 and 2, something to do with UDP vs. TCP packets and purports to have unstable, experimental software which might work. 

My questions are, Does the Raop module for PulseAudio work under Ubuntu 14.04 desktop? Do I merely have a configuration problem, or is this software broken or unable to communicate with "version 2" Airplay devices? Am I wasting my time with this approach to streaming internet radio stations to my receiver and if so, are there any suggestions for an alternative approach?

Thank you in advance for any information, opinions or suggestions you may offer.


Hugh Barstead

---

### Post by Hugh_Barstead on 2015-01-17
Well, I have solved my problem, but not through the use of Raop, so I am not going to mark this thread as solved. I am still very much interested in Raop and Airplay and hope to see it functioning. If anyone can answer my questions I will be very grateful.

I have solved the problem of streaming live internet radio to my Pioneer receiver through the use of software called "pulseaudio-dlna" (Google "masmu/pulseaudio-dlna". This fantastic little piece provides a list of your DLNA renderers as output choices in the Sound panel in System Settings. Install and start pulseaudio-dlna according to the instructions (simple), fire up Rythmbox (or any other app that uses PulseAudio, as far as I can see), select the audio source you want and then go to the Sound panel and select your prefered device. The sound appears without any other intervention, no remote controls needed. 

There is very significant latency - along the order of 16 or 17 seconds on my laptop - but for audio only this is unimportant. So far the system seems very stable, does not appear to conflict with MiniDLNA or anything else that I can see. If you are looking for a solution to stream audio to your AV receiver, smart TV or Blu Ray player, give this software a try.

Hugh Barstead

---

### Post by qos2 on 2015-02-07
Hello Hugh,

I digged into this sometime ago.
The pulseaudio raop module is just for the RAOP 1 protocol. Version 2 is not supported, and imho they don't plan to do so. There is a pulseaudio 5 & 6 fork on github [somewhere]("http://hfujita.github.io/pulseaudio-raop2/") which implements raop 2. I tested this myself and it worked, but it is not that easy to compile and has to be started for your default pulseaudio instead. Besides that this pulseaudio fork likes to crash every 3 or 4 hours. So not that great of an option.

So the pulseaudio raop module works fine, but just with raop 1 devices. Sadly the majority of the devices you can buy are raop 2. You don't have a configuration problem. In my opinion you are wasting your time with getting raop 2 running, besides the mentioned fork. It is easier to use open standards like DLNA.

I am using pulseaudio-dlna myself and can say that the latency is network related. i have a cable setup running here and the delay is about 1-2 seconds. with my wifi (and very good signal strength) it is about 3 seconds.
So i assume that your network is quite slow.
Also i can confirm that pulseaudio-dlna does not conflict with any other DLNA services you might have installed on your computer.

---

