---
title: "Capture and Playback Sample Clock Synchronizing in Networked PCs"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by GaryH on 2008-01-11
Hi Everybody,
I'm trying to figure out how to frequency lock ALSA playback clocks in a multiplicity of networked computers. Does anybody out there know where I can find out about ALSA internals. My plan is bump the playback sampling rates slightly up and down in correspondence to the frequency (and hopefully phase) error between them and the computer with the master capture clock reference.
Thanks in advance,
GaryH

---

### Post by GaryH on 2008-01-16
Hey Everybody,
Not much Ubuntu activity out there on ALSA or so it would seem. Anyway the place to go for ALSA tutorials, source, and sample application code fragments is [http://www.alsa-project.org](http://www.alsa-project.org).
Peace,
GaryH

---

### Post by tgalati4 on 2008-01-16
Networked computers will each have a different latency that is variable.  TCP/IP protocol is an asynchronous communication.  I suppose you could ping each machine and use a correction based on the turn-around-time.  This would be valid during a short period of time as network traffic will change latency.

For music coherency, you would need to be accurate to at least 1 millisecond, which is about 1 foot of sound travel in normal conditions.

I do remember seeing a project for multiple musicians jamming over the network using some sort of pseudo-synchronous protocol, but I don't remember the project name.  I also recall some effort at pseudo-synchronous mp3 streaming for multiple PC's in a large house, but again I don't remember the project name.

In digital music production, a 75-ohm cable is used to link digital clocks of various devices and then each device is set to either slave or master depending on configuration.

It's a non-trivial issue:  how do you syncronize clocks to 1 ms accuracy over an asyncronous ethernet-tpc/ip protocol?

---

### Post by GaryH on 2008-01-16
Hi tgalati4,

Thanks for your comments.

The plan is to have a multiplicity of playout computers networked to a central capture computer each with a percise .1 second delay to dejitter the network. Not so cool for jamming over the web but okay to pipe audio wirelessly through my house.

Each playout computer is to have a .2 second dejitter buffer (FIFO) which is played out at 44100 samples per second and fed with 10, 4410 sample UDP packets per second. 

Each playout computer will continuously trim its playout sample clock using the ALSA API, snd_pcm_hw_params_set_rate_near(), to keep its dejitter buffer half (.1 sec) full.

Comments welcome!

Peace,
GaryH

---

### Post by tgalati4 on 2008-01-18
That's an interesting approach.  However each 44K clock has a variability (+/- 3%) that can cause pitch changes and weird phase effects when listening to the same material being clocked with different output devices.  Drift over time becomes and issue as well as a faster clock will drift more and more over several hours.

Your approach handles the LAN problems with multiple streams causing collisions, but it doesn't address the psychoacoustic effects of improper phasing and delay.

Only testing will determine if it's acceptable.  Let us know how it works out.

Last month, I set up a fiber optic audio distribution system for a county fair grounds.  We now have clean sound distributed for several thousand feet, but we now have to figure the acoustic delays and match them between venues.

I did a neat test with AES digital stream (SPDIF is a consumer version of AES using toslink or video coax) running a stereo CD player through a processor then sending the digital stream through 1000' of cheesy Cat-5 cable and playing through a processor at the other end.  1,500' would not work.  I was told by a Sabine representative that 1,200' is probably the limit for Cat-5 digital transmission.  Then you have to go fiber.

Good luck.

---

### Post by GaryH on 2008-01-19
Thanks for the feedbck tgalati4 and you're right test, test, test... 
GaryH

---

