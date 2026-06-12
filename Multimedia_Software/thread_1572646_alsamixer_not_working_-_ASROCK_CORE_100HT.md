---
title: "alsamixer not working - ASROCK CORE 100HT"
date: 2010-09-11
forum: Multimedia Software
---

### Post by checcouniud on 2010-09-11
HI ,

i just bought a ASROCK core 100ht and installed ubuntu 10.04.

My speakers and headphone works fine but my microphone is not working, a common problem. Usually i solve it through alsamixer.
However my Alsamixer shows only " Master PCM     S/PDIF  Capture " (see pic)!
And no microphone option. Does anyone knows what is going on? 

thanks for any help.

these are few of my outputs :

francesco@checco:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbcf0000 irq 22



francesco@checco:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 42
  Mono:
  Front Left: Playback 42 [100%] [0.00dB]
  Front Right: Playback 42 [100%] [0.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]
francesco@checco:~$ sudo lspci -v
...
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: ASRock Incorporation Device 2920
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fbcf0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...

---

### Post by Gonzalo_VC on 2010-09-11
[COLOR="Navy"]In my PC with Ub 9.10 the (external) microphone is not working, either. If I change the configuration (in Sound preferences) from "stereo duplex" to any other option, even the audio stops working :confused:.
I didn't have a mic plugged in when I installed the Koala, was this the problem?

In my Gateway netbook, I have installed Ub. 10.04 and the internal mic is working fine when trying to record a sound, but not for Skype.

From what I saw in other *fora*, the microphone is something _problematic_ under Ubuntu. _[U]**It's a shame**_[/U] :frown:.[/COLOR]

---

### Post by checcouniud on 2010-09-12
Yes i agree. In my opinion UBUNTU HAS to solve this problem. 
I am a normal user and obviously nowadays the microphone is essential. 
Half of the problems that i had with ubuntu systems are microphone
related. I am not a good computer guy but probable my pc literacy is higher than average. Simply, i can not afford to spend 3 days to fix a microphone every time i change computer or do an update.  

Any help? anyone?
God bless you :)

---

### Post by checcouniud on 2010-09-12
I solved the alsa mixer problem by removing linux-alsa-driver-modules-(version)-generic, and installing the latest version of linux-backports-modules-alsa-lucid-generic. (thanks to pcreed and swaprava in the 
[http://ubuntuforums.org/showthread.php?p=9639008#post9639008](http://ubuntuforums.org/showthread.php?p=9639008#post9639008) )

sudo apt-get --purge remove linux-alsa-driver-modules-$(uname -r)

sudo apt-get install linux-backports-modules-alsa-$(uname -r)

Now alsamixer sees all the options.
I just turned on the microphone and it works.
Now i just need to do some setting adjustments...

hope this will be helpful for others.

---

