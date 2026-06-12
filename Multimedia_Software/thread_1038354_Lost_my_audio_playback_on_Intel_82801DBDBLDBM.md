---
title: "Lost my audio playback on Intel 82801DB/DBL/DBM"
date: 2009-01-12
forum: Multimedia Software
---

### Post by inspired on 2009-01-12
Hi folks,
Sound was fine on this machine until today. I also notice that USB is problematic as of today. I am not sure if they are related, but I stick to describing the audio problem.

I can't playback sound. If I load up something like Audacity it records sound from the mic but there is no playback. I have tried every sound controller option in the Audacity prefs. I have also tried testing every different controller in the Sound preferences for the OS.

If I turn up the sound for one of the mic options I do get sound coming directly through from mic to the speakers. 

Yesturday I installed about 5 difference audio apps in order to find one I liked. I think that may have screwed things up.

All the audio apps worked yesterday, but since rebooting the machine none of them work. Most (perhaps all) of them tend to lock up too and I have to force them to quit.

My config is:
Ubuntu 8.10
Sound card: 
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Compaq Computer Corporation Device 0860
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 4000 [size=256]
	I/O ports at 4880 [size=64]
	Memory at a0200000 (32-bit, non-prefetchable) [size=512]
	Memory at a0300000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

```
aplay -l gives me:
```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I get what seems like a big list of options in the sound controllers for capturing and playback.
I note that the following major sound systems are installed:
Pulseaudio
alsa-base
alsa-oss
esound

Audio apps I have installed in the past few days (most of them yesterday whilst trying to find one I like on Linux):
Amarok
BMPx
Banshee
Exaile
Kyamo
Quod Libet
Rythmebox
Audacious
Audacity (installed weeks ago for audio recording)
Mplayer (I think it was already installed or at least ages ago)
Streamtuner

I have checked the alsa mixer and nothing is muted. I have checked the gui system mixer and nothing is muted.

Somehow I broke my sound. I spent some hours reading through many threads and discussions about how to test and fix sound issues, but I've found nothing specific I could apply. I did see many people finding that sound starting working in Skype after removing pulseaudio, but that seems to be potentially problematic and I've not tried it. It was whilst trying to get a Voip app working today that i realised my sound was dead.

I also note that Ubuntu starts up with the sound muted. That never used to be the case.

I'd greatly appreciate some help on this.

With thanks,
Jonathan

---

