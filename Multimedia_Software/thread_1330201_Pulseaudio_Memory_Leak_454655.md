---
title: "Pulseaudio Memory Leak 454655"
date: 2009-11-18
forum: Multimedia Software
---

### Post by ageeb on 2009-11-18
Is anyone else affected by this?
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655)

For me, it seems the bug doesn't materialize until i update the system after a fresh install and then reboot, but i don't see which packages may be affecting pulseaudio in the list.  Regardless, i discovered this... (system was still funcional, i was just poking around).

[http://imagebin.org/72017](http://imagebin.org/72017)
[http://imagebin.org/72018](http://imagebin.org/72018)

:frown:

What would you guys do as a workaroud until theres a fix released (hopefully)?

---

### Post by VertexPusher on 2009-11-18
> **ageeb said:**
> What would you guys do as a workaroud until theres a fix released (hopefully)?
Remove PulseAudio.

Sound works just fine without it.

---

### Post by ageeb on 2009-11-18
> Remove PulseAudio.

Sound works just fine without it.     i was suggested the same thing by someone else.  I tried 

```
sudo apt-get remove pulseaudio
```rebooted and installed alsa-mixer via synaptic.  I turned up all the audio channels and did get audio, but far from fine.  Unfortunately lots of background static.

I also tried the 0.9.20 pulseaudio and that didn't fix the leak either fyi.

---

### Post by ageeb on 2009-11-18
for anyone watching this thread i reinstalled and turned off recommended updates and did a system update.  After reboot pulseaudio was still stable, so for my system, it's something in the recommended section making pulseaudio bleed to death.

I'll start to go through recommended updates 1x1...

---

### Post by ageeb on 2009-11-18
Well... after alot of trial and error with 107 packages we have a winner!!
[SIZE=2][B]
package 'udev' [/B][/SIZE](147~-6.1 according to synaptic) makes my pulseaudio bleed to no end.  All available updates from security and recommended are installed minus 'udev' and pulseaudio is sitting at a stable 2M.  

Hopefully this is useful for someone.

---

### Post by VertexPusher on 2009-11-19
> **ageeb said:**
> I turned up all the audio channels and did get audio, but far from fine.  Unfortunately lots of background static.
I guess that explains the memory leak. There seems to be an issue with your soundcard driver.

---

### Post by ageeb on 2009-11-19
> I guess that explains the memory leak. There seems to be an issue with your soundcard driver.     My audio is fine at the moment, as i have not uninstalled pulseaudio on this latest build.

Read the bugtracker thread in the first post and you'll see the issue is with the udev package.  This work brought it from unconfirmed to confirmed and importance went from undecided to high.  

Thanks for suggestions  though...

---

### Post by VertexPusher on 2009-11-20
> **ageeb said:**
> My audio is fine at the moment, as i have not uninstalled pulseaudio on this latest build.
But it's full of static when you remove it?

That doesn't make sense. PulseAudio is an ALSA client just like any other application. If there's a bug in ALSA's driver that causes static, PulseAudio won't make it disappear.

---

### Post by alexfish on 2009-11-20
i have same package udev 147~6.1  running a dvd / testing vlc  with 5.1 / 2 runs of dvd / memory shows 275 mib of 2gb 
     

    intel atom330  2gb memory   old sound card hurcules lists as CM8738

---

### Post by alexfish on 2009-11-20
i have same package udev 147~6.1  running a dvd / testing vlc  with 5.1 / 2 runs of dvd / memory shows 275 mib of 2gb 
     

    intel atom330  2gb memory   old sound card hercules lists as CM8738

---

### Post by cutterjohn on 2009-11-21
> **ageeb said:**
> Is anyone else affected by this?
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/424655)

For me, it seems the bug doesn't materialize until i update the system after a fresh install and then reboot, but i don't see which packages may be affecting pulseaudio in the list.  Regardless, i discovered this... (system was still funcional, i was just poking around).

[http://imagebin.org/72017](http://imagebin.org/72017)
[http://imagebin.org/72018](http://imagebin.org/72018)

:frown:

What would you guys do as a workaroud until theres a fix released (hopefully)?Yup, I ended up noticing this yesterday after doing a little investigation of creeping memory usage as in using all 4GB DRAM and all 4GB vm eventually after sleep when before sleep it was using ~50% DRAM and ZERO vm.

```
6072 pqrstuv    20   0 4301m 2.4g 1968 S    0 62.0   5:36.71 pulseaudio
```

---

### Post by alexfish on 2009-11-23
> **cutterjohn said:**
> Yup, I ended up noticing this yesterday after doing a little investigation of creeping memory usage as in using all 4GB DRAM and all 4GB vm eventually after sleep when before sleep it was using ~50% DRAM and ZERO vm.

```
6072 pqrstuv    20   0 4301m 2.4g 1968 S    0 62.0   5:36.71 pulseaudio
```
  
Thanks in advance / could you post your system

---

### Post by cutterjohn on 2009-11-23
> **alexfish said:**
> Thanks in advance / could you post your systemMSI GT725-074US (PM45 + ICH-9M)
Intel P8600
4GB DDR2-800
ATI Mobility Radeon 4850 512MB GDDR3
Intel WiFi 5100
IIRC the sound chip is the Realtek 889S

Ubuntu 9.10 x86-64
catalyst 9.11

soft-modem is disabled, no driver loaded(I never use it), as is bluetooth, and camera.

Interesting enough doing an aplay -l this shows up:
```
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Also note, this is dist-upgraded from 9.04

[EDIT=somewhat later]
I also have udev 147~6.1 up and running as well... probably should go add to the bug entry when I get around to it...
[/EDIT]

---

### Post by bender1234 on 2009-12-29
Confirmed, pulseaudio leaks constantly. Acer aspire 6930G with Intel HDA.

[HTML]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/HTML]

Ubuntu Karmic 2.6.31-17-generic x86_64 GNU/Linux. Clean install

---

### Post by cutterjohn on 2009-12-31
Ooops, my bad, the sound IC is actually a Realtek ALC1200:
```
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

BTW if you search for pulseausio ubuntu 9.10 memory leak it'll turn up a bug entry in launchpad with a workaround:

edit /etc/pulse/default.pa and find
```
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif
```change to```
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
#.endif
```

This "fixed" the memory leakage for me, however after one reboot pulse apparent;y wasn't able to find my sound card so no sound.

To "fix" that just undo the editing, kill pulse(thing is undead it'll start again by itself), undo edit, kill pulse and you should be good to go again.  (You may have to/want to reboot after restoring the original default.pa again, and then re-edit default.pa to no use the udev detect...)

---

### Post by Kapuster on 2010-01-21
Yes, that also worked for me. I changed the file like you did it. 

```
Pulseaudio -k
Pulseaudio -D
```

This is for stopping and starting the pulseaudio deamon. Than I restored the old file for the next reboot. Pulseaudio works now since more than 10 hours without increasing memory.

Edit: Ok, on the Launchpad is already a new version postet without that bug.

---

