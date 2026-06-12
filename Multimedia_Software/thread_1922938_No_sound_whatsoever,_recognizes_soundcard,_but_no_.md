---
title: "No sound whatsoever, recognizes soundcard, but no alsa drivers"
date: 2012-02-09
forum: Multimedia Software
---

### Post by hihihi100 on 2012-02-09
Hiyas:

How it happened:

I was trying to play a sega ROM via Kegafusion, that uses OSS, not ALSA (NOW I know this). I clicked quite a few times the "enable sound" in the kegafusion console, to always get the same answer: sound cannot be activated. And from that momento on, all sound has been broken.


First:[http://www.alsa-project.org/db/?f=74f89ad537d190628d85cb5ae4231b5face314e3](http://www.alsa-project.org/db/?f=74f89ad537d190628d85cb5ae4231b5face314e3)

As you can see, no driver found, but my machine recognizes the sound card:
```
 lspci -v
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
	Subsystem: CLEVO/KAPOK Computer Device 0802
	Flags: bus master, medium devsel, latency 0, IRQ 4
	Memory at d3300000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel


```
relevant lines only

```
lspci:
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller

```

relevant line only
```
aplay -l
aplay: device_list:240: no soundcards found...

```

QUESTIONS:

Theoretically I could access alsamixer by simply opening a terminal and writting that (alsamixer). Note that I have the alsa-base package installed (synaptic), and I dont need anything else. Correct me if wrong:

```
alsamixer
cannot open mixer: No such file or directory

``` 

I also have GNOME-alsamixer, but, if opened, it will only show a blank square, and if I click on any of the options, it will segfault.

And I have been trying to follow the instructions found at:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

But I cannot pass step 1 for 11.10 (my distro), because (and notice that I copy and paste that huge command, correct me if I have to split it):

[CODE]E: Unable to locate package linux-alsa-driver-modules-3.0.0-15-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-15-generic'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-3.0.0-15-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-15-generic'
[CODE]

I still want my machine to produce sound both for regular music and kegafusion effects. I guess the kega effects could be activated via the ALSA plug in for OSS instead of installing the whole OSS4 package

---

### Post by Yellow Pasque on 2012-02-09
Yet another victim of the Sound Troubleshooting Guide.. :(
See if this fixes your sound: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

> Kegafusion, that uses OSS
The next time you try and use an OSS program, start it with padsp, for example:
```
padsp Kegafusion
```

---

### Post by hihihi100 on 2012-02-10
Temüjin:

None of the solutions proposed works, I havent seen any difference

Alsamixer is still nonexistent

Help

---

### Post by Yellow Pasque on 2012-02-10
Can you run the alsa-info script again to verify that you installed the module correctly?

---

