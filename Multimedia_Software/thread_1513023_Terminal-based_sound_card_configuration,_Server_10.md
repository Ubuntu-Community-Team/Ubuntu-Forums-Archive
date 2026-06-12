---
title: "Terminal-based sound card configuration, Server 10.04"
date: 2010-06-18
forum: Multimedia Software
---

### Post by charlesshoults on 2010-06-18
I debate whether to place this under Server or under Multimedia, because it's both.  I have Server 10.04 installed on a Foxconn Intel Atom board.  For one of it's duties, I hope to set it up as a jukebox with Subsonic.  I plugged in a pair of headphones and set about testing.  Long story short, I have no audio from them, although I can get a light hiss when using sound-test.  (I will have no GUI on this machine.  Everything will be done through terminal or through a browser.)

Using lspci, I have this:
**00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)**

Using aplay -l, I have this:
[B]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]

In alsamixer, I have master and headphones at 100% and front at 45%.  But if I run a speaker test, I get the following.  If I let it continue, it will keep testing front left and never go to the right channel.  I think it's basically setting it to mono because it doesn't know what else to do, and I don't know how to fix it.

[B]speaker-test 1.0.22

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left
Time per period = 2.663892
 0 - Front Left
Time per period = 2.986349
 0 - Front Left
Time per period = 2.986366
 0 - Front Left[/B]

Help.  Please?

---

### Post by charlesshoults on 2010-06-19
If I change the speaker test, I get this, and I do hear the static alternate from left to right.
speaker-test -c2

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.643698
 0 - Front Left

I still don't know if I really have sound, but I know that the computer itself is capable of sending something to the speakers.

---

### Post by robbinhood on 2010-06-19
Terminal-based sound card configuration are given below:-
 List of PLAYBACK Hardware Devices 
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice 0: subdevice 0
card 0: Intel HDA Intel device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice 0: subdevice 0
Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384

---

