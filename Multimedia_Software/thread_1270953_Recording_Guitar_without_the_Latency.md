---
title: "Recording Guitar without the Latency"
date: 2009-09-20
forum: Multimedia Software
---

### Post by muddles on 2009-09-20
my problem is.. i have a Hard Drive-less Gateway MT6832b laptop -
[ see specifications here](http://support.gateway.com/s/Mobile/2007/Oasis/1014394R/1014394Rsp2.shtml)
so it is currently running on a 4GB USB SD card reader

I want to connect up my :guitar:lectric/ *Semi acoustic (with pre-amp)* to the laptop, throught the Mic/ Line in port.

my current choice of programs and initial software are
Audacity 
ASLA
TiMIDIty
VLC

i have browsed around the web and the ubuntu forums, and all that gets said is "buy a new sound card" or hook it up to a microphone/ amp and mike...

i've seen ways to remove latency from general audio recording from microphones and such, but havent managed to clearly solve the issue... 

the basic function that i want my laptop to work as.. would be as a miniturized amplifier.
in which it can capture and playback whatever audio is input..

---

### Post by raboofje on 2009-09-20
Some sound cards have a 'direct monitoring' switch that makes it directly send out whatever it picks up on the inputs - you could try and see if your card has something like that in 'alsamixer'.

If not, you might want to try:
- instal the 'linux-rt' kernel
- start qjackctl
- open the 'connections' window
- connect the 'system' input directly to the 'system' output.

---

