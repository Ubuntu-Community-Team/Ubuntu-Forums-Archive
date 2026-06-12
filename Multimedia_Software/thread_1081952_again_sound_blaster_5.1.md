---
title: "again sound blaster 5.1"
date: 2009-02-27
forum: Multimedia Software
---

### Post by soheil on 2009-02-27
I use ubuntu 8.10 x86 64-bit and sound blaster 5.1. I have problem with my surround speakers.

I find this post
[http://ubuntulinuxhelp.com/enable-51-surround-sound-on-linux-ubuntu-804-hardy/](http://ubuntulinuxhelp.com/enable-51-surround-sound-on-linux-ubuntu-804-hardy/)
that is very useful but it is not working for me. when I use this command

speaker-test -Dplug:surround51 -c6 -l1 -twav

I hear sound from all my speakers but when I use mplayer or totem just one speaker is working! I try to fix it in totem -->/preference/Audio/5.1-channel but
again just one speaker has a sound. also non of outputs in sound volume is mute.
my apaly -l result is
------------------------------------------------------------
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
------------------------------------------------------------

Thank you

---

### Post by soheil on 2009-02-28
No any idea ? :popcorn:

I sow a post about How to use the output sound for other speakers (same sound from all speakers). But I want a real working surround. :guitar:

---

### Post by soheil on 2009-03-01
any body knows why I have three devices? I have only one sound card :confused:

---

### Post by soheil on 2009-03-04
](*,)      :-({|=       :popcorn:    :idea:

---

### Post by soheil on 2009-03-06
It Solved!!!  :lolflag::lolflag::guitar:\\:D/\\:D/:popcorn:

---

### Post by robing9 on 2009-03-06
Hi soheil

I am having the same issue. please can you tell me the way you fixed the issue :(

Regards
Robin

---

### Post by soheil on 2009-03-13
> **robing9 said:**
> Hi soheil

I am having the same issue. please can you tell me the way you fixed the issue :(

Regards
Robin
  
follow the link in my first post.

if it was not successful then use the command
speaker-test -Dplug:surround51 -c6 -l1 -twav
to be sure that your surrounds are working

if they are working
then right click on speaker sign, up in the panel.
and "open the volume control"

choose your device as "Dell sound blaster Live(alsa mixer)"
then choose preferences

and mark every thing which contains the name
surround, 
rear\lfe\center\front 
rear\lfe\center\front jack
(you can check more options if you want)

then return and be sure that none of them are mute

then go to option menu and change the 
rear jack
lfe\center jack and 
front jack 
to the front output

also on totem in the sound option use 5.1 output

It worked for me I hope it work for you too. ;)

---

