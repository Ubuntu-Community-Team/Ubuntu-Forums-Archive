---
title: "No audio after installing Ubuntu 10.04"
date: 2010-07-22
forum: Multimedia Software
---

### Post by mamboze on 2010-07-22
I installed Ubuntu 10.04 several weeks ago and it ran faultlessly. This week I upgraded to a 500Gb hard disk and reinstalled 10.04. Now, the problem is no audio across the board, Rhythmbox, Mplayer, YouTube and so on. 

I checked to see whether the audio device was being recognized: 

```
roy@prospero:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
```
And 
```
 
roy@prospero:~$ lspci -v
.....
.....
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: AOPEN Inc. Device 03cb
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at b800 [size=256]
	I/O ports at bc00 [size=64]
	Memory at fc001000 (32-bit, non-prefetchable) [size=512]
	Memory at fc002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
....

```
I then followed the two stickies in Multimedia & Video; the Multimedia and Video Howto thru the Installation section (using the Lucid repositories) and the Sound Problems Solutions Guide thru the General Help section and Saving Sound Settings.

But still no audio, video OK (as it was before). I've been using Ubuntu for several years but I'm a noob so far as sound setup is concerned (this is a first time problem).

TIA

---

### Post by mamboze on 2010-07-22
OK, stupid noob mistake. Sound muted in Sound Preferences, duh. Tho it is surprising to me that in previous versions I've installed the sound was not muted. At any rate, I learnt some more about Ubuntu.

---

