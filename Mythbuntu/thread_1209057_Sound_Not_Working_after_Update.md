---
title: "Sound Not Working after Update"
date: 2009-07-09
forum: Mythbuntu
---

### Post by murbanci on 2009-07-09
My sound was working with Mythbuntu 8.10 however after an update, my sound no longer works.  I have tried Mythbuntu 9.04 with the same problem. Heres some info on the soundcard:

aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v
```
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: ASRock Incorporation Device 0888
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I have also tried reinstalling the alsa modules using
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

Still no luck.  Any ideas how I can get this to work?? Its kinda necessary since I use this as a DVR.  Any help would be appreciated.

---

### Post by klc5555 on 2009-07-10
Having made sure the appropriate modules have loaded with lsmod, the next step would be to see whether alsa is configured correctly.

Sometimes, if the sound card uses that Via chipset, and you have one or more software decoding tuners that contain a sound chip, ALSA gets confused and sets the wrong soundchip as the default.

asoundconf list 

will give you the soundchips that ALSA knows about --the one currently the default is listed first. If that's not the one for your actual sound card, use 

asoundconf set-default-card

to set it to the correct chip.

speaker-test

will pump some white noise through the system to determine whether the sound is enabled or not.

Sometimes too, particularly when running mythtv on top of regular Ubuntu, the ALSA master gets set to "muted", for odd reasons. Check to make sure it has been unmuted.

And sometimes if you're using analog tuners, the system becomes fussy whether the tuner is set to output sound to /dev/dsp, /dev/dsp1, or /dev/dsp2. Result: no tv sound, but sound elsewhere.

Finally, there's a sketchy sound troubleshooting guide on the wiki at [http://www.mythtv.org/wiki/Sound_Troubleshooting](http://www.mythtv.org/wiki/Sound_Troubleshooting) which may be of some use.

Good luck! :)

---

### Post by Andrew U.K. on 2009-07-11
Hi,

Have you had any luck sorting out your sound problem.
Mine stopped after upgrade.
But works in ubuntu 9.04 only when I add myttv on top does the sound stop, including the ubuntu side.
My card shows up  o.k. with aplay -l

[I]andrew@andrew-mythbox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
andrew@andrew-mythbox:~$ 


03:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at cd00 [size=32]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106[/I]


Have you tried installing ubuntu 9.04 to see if it is purely mythtv related?

---

### Post by giulliano on 2009-07-23
I have a SoundBlaster sound card and my sound stoped work after I updated my XUbuntu 9.04.

I typed the following command to force ALSA to reload:

sudo alsa force-reload

After that, I noticed that it was saying that some files didn' t have .conf extension (for example /etc/modprobe.d/oss-compat) so I fixed it using:

sudo mv oss-compat oss-compat.conf

After that, I typed again:

sudo alsa force-reload

And my sound was working again.


I hope it could help someone like me.

---

