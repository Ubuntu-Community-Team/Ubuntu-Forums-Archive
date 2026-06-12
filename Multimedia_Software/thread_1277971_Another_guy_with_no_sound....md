---
title: "Another guy with no sound..."
date: 2009-09-28
forum: Multimedia Software
---

### Post by MuccaPazza on 2009-09-28
Hello all, 

I know from reading many other threads that this is a very common topic... please forgive me for bringing this up, again, but I could not find the answer anywhere. 
Yes, me too, am brand new to Ubuntu (9.04). Maybe someone with similar hardware as me will face the same problems, hopefully there is a cure. 
Toshiba Tecra A10

I have no sound, zero, nothing, not a bip. I read many threads, tried several solutions, none worked so far. 
First, I should mention that I previously had XP installed on this laptop, so I know my hardware functions. 
Second, I am completely new to Linux, Ubuntu, and just tried it for kicks (programmer buddy..). So far I love it, other than this issue. 
Then, I tried several fixes, on several threads, nothing worked so far. Part of the reason is because I'm a complete newbie, and a lot of the abbreviations and terminology used threw me off. Now I at least know (a little bit) how to use the Terminal... don't laugh and remember _your_ first hours! 
Last, after those unsuccessful fixes, I re-installed Ubuntu, so this is now a fresh copy. 


Anyway, here's what I have tried so far: 
1-
[http://ubuntuforums.org/showthread.php?t=1130858&highlight=no+sound+9.04](http://ubuntuforums.org/showthread.php?t=1130858&highlight=no+sound+9.04)
this led me to:

2- 
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)
this is where I am stuck. 

Following this guide, I was able to confirm that: 
1) Nothing is muted, all the levels are above zero. 
2) The system is recognizing my card.
3) I do have the sound modules installed.
4) The sound card is installed and physically recognized by my hardware.
5) This is where I got stuck: "Is my sound card supported?"

I clicked the ALSA link, searched for my card, and couldn't find it. 

Here's what Terminal spit out: 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 03)
        Subsystem: Toshiba America Info Systems Device 0001
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at ce000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel



So this is where I'm at. I've spent a couple days trying to fix this issue and the biggest part is probably due to my ignorance of Ubuntu. 
Help would be much appreciated. Let me know if you need more info.

Thank YOU! 
MuccaPazza

---

### Post by MuccaPazza on 2009-09-30
Anybody out there?

---

### Post by MuccaPazza on 2009-09-30
This is fixed ;-)   Please read here:  ...linuxforums.org/forum/ubuntu-help/153659-discouraging-sound-issue-9-04-a.html

---

