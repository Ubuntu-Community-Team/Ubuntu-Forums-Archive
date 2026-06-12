---
title: "weird sound problem - stuttering"
date: 2010-12-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2010-12-11
after a while being logged in the sound stutters. 
i have to either close all apps and then retry music or restart pc. 

when it happens it also affects watching video files and dvd's as the screen will jump also. 

i know it is alpha 1 but wondered if anyone else having this problem or is it just me.

---

### Post by cariboo on 2010-12-11
I've seen other threads about the same sort of problem, have you checked top, to see what it is that is causing the problem? What application are you using when this happens?
What type of sound card/chipset are you using?

---

### Post by pressureman on 2010-12-12
I find that the sound in other apps stutters if I have been using Skype previously in that session. Killing/restarting pulseaudio seems to fix it.

```

pulseaudio -k

```

PulseAudio should automatically restart. You will have to pause/resume any movies/music you had playing at the time.

---

### Post by terry_gardener on 2010-12-12
my soundcard as stated in lshw 

multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:fbff0000-fbff3fff

pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          resources: memory:0-1fffffff

---

### Post by cornelis spronk on 2010-12-12
On account of the stuttering, I have been using 9.04 till just a month ago.  The problem for me was so bad with 9.10 and 10.04 that I just could not use them.  Ubuntu 10.10 is a bit better, but I am going to haul out and old computer box and reinstall 9.04 so I can do some music recording without the stuttering messing things up.

I have attempted to tweak the "default-fragments" to different values in the daemon.conf file, as suggested in another thread,  This for me makes very little difference in making the stuttering worse or better.  At any time when I change the volume, I have to fiddle with the adjustment to stop the stuttering.  Then it works OK for a while, but then the sound sometimes drops out, or the stuttering happens again, and I have to tweak the sound volume adjustment to stabilize the sound.

The daemon.conf file can be found in the terminal by using the command

```
gksudo gedit /etc/pulse/daemon.conf
```

I have not tried to remove pulse audio.  Maybe that would solve the problem.  Does it create new problems?

I would certainly appreciate a solution to this annoyance.

---

### Post by cornelis spronk on 2010-12-12
This is the data for the Turtle Beach Santa Cruz sound card I am using.


        ```
  *-multimedia
                description: Multimedia audio controller
                product: CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator]
                vendor: Cirrus Logic
                physical id: 2
                bus info: pci@0000:01:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Sound Fusion CS46xx latency=64 maxlatency=24 mingnt=4
                resources: irq:17 memory:fe9fe000-fe9fefff memory:fea00000-feafffff

```

---

