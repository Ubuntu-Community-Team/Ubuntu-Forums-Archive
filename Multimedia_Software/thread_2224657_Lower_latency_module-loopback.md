---
title: "Lower latency module-loopback"
date: 2014-05-17
forum: Multimedia Software
---

### Post by Kyle_Siefring on 2014-05-17
My piano is connected to my computer via analog audio cable. I want to have it so that I can hear myself play piano and listen to music through my headphones. Notably, it is nessesary to keep sound down in the area around me. Running the command "pactl load-module module-loopback" results in a loop that is not low enough latency for me. By testing with the piano's metronome, I can get about 240 bpm before I start having trouble telling if the piano plays beat n+1 before the computer plays back beat n.

I am currently on ubuntu 13.10 (okay, mint). For this, I am using the anolog ports on my motherboard. The chipset is Realtek ALC887 and my mother board is a gigabyte GA-78LMT-USB3.

---

### Post by m-dw on 2014-05-19
Hi.  Have you tried installing a low-latency kernel and using jack as a sound server?

I've been running UbuntuStudio (which is a complete multimedia platform) since 12.04 which has a bunch of audio applications installed by default, but there's no problem with only installing the ones you want.  The low latency-kernel allowed me to get down to about 2ms on an AMD64 3200+ @ 2000MHz.

Getting jack working is a bit of a learning curve, but applications like qjackctl make it easier.

---

### Post by Kyle_Siefring on 2014-06-18
I installed ubuntu studio and it has been working rather well. To get the desired effect, I have to start jack from qjackctl and connect the system output and input.

There are a few annoyances. My monitors don't turn off by themselves anymore so I have to turn them off manually. Secondly, built-in audio has glitched out on me once. Jack seemed to be started up when that happened even though I turned it off. I will have to wait for that to happen again. My final complaint is that the "for creative humans" on the start up screen is somewhat condensending,

---

