---
title: "No sound -  fatal error"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by gravediggers on 2006-12-11
Hi,

Just done fresh install of Kubuntu 6.10, and don't have any sound. This wasn't previously a problem in Breezy, so may be it is some kind of bug??  And, I keep getting an annoying warning message "sound server fatal error. CPU overload.. aborting.". Tried searching through some similar threads, but didn't find anything greatly helpful, other than a very useful thread by LordRaiden 
[Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449") 
(Which I still have to digest more of).

My on board sound is being detected, and what seem like the right drivers are installed, so I'm not quite sure where to go from here (I'm still feeling my way in the area of Linux sound).
Here are some of my settings.

```
gravediggers@gandalf:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
gravediggers@gandalf:~$   

```

```
gravediggers@gandalf:~$ cat /proc/devices
Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 21 sg
 29 fb
116 alsa
128 ptm
136 pts
171 ieee1394
180 usb
189 usb_device
216 rfcomm

Block devices:
  1 ramdisk
  2 fd
  3 ide0
  8 sd
 22 ide1
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
gravediggers@gandalf:~$
```

```
gravediggers@gandalf:~$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.12rc1 emulation code)
Kernel: Linux gandalf 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
VIA 8237 with ALC655 at 0xbc00, irq 201

Audio devices:
0: VIA 8237 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC655 rev 0
gravediggers@gandalf:~$
```

```
gravediggers@gandalf:~$ lsmod | grep snd
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
snd_seq_midi            9984  0
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            30360  2
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10240  1 snd_via82xx
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    58372  14 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
gameport               17160  2 snd_via82xx,analog
soundcore              11232  1 snd
gravediggers@gandalf:~$ 
```    

I'm not really sure what my problem is, so has anyone got an idea?:confused:

[EDIT]Oh yeah, and I have reinstalled a couple of times, and had the error each time!

---

### Post by igknighted on 2006-12-11
I get this error **all the time**.  I have never figured out how to get rid of it.  It is some issue with that VIA audio, because I have the same one.  I also have a SoundBlaster Live which I use and works well, but if I could get rid of that crash I would be elated.

ps: sometimes KDE will disable arts output and it will work ok until arts decides to be used again, so I assume arts to be the culprit.  Any way to disable it?  It tries to start whenever I use Amarok.

---

### Post by gravediggers on 2006-12-11
Thanx dude! Always nice to know I'm not the only one having the problem. I wasn't planning on spending any $ on a new sound card, but I guess I could do that, and disable the onboard sound. Would seem a pity to do that, considering it all worked OK with Breezy!
Would I still have problem anyway, as the PCI would still use the 8237 chipset?

---

### Post by gravediggers on 2006-12-13
What an idiot! I had checked the sound wasn't muted, and had a bit of a play with the mixer, but forgot to turn the speakers on!
Banished annoying artsmessage to desktop 4 for all eternity.

---

### Post by Oceola on 2006-12-23
With a sound blaster I found no sound with Dapper but found if you uncheck the IEC 958 there's sound, along with turning on the wave checks. I also found something like 32 emulator packages for send and receive which I could not relinquish my self of but I was able to turn off 31 without an loss of sound, one wouldn't go away. But the IEC 958 did the same thing in Breezy. Check under preferences if your using the Sound Blaster Live Value (CT4871)
The emulators are tagged as EMU10K1 PCM send or recieve and the are numbered 1 through 32.

---

