---
title: "No sound - Thinkpad R61i - Karmic"
date: 2010-12-08
forum: Multimedia Software
---

### Post by TomDaBomb2u on 2010-12-08
I had taken a long break from Ubuntu, but now I'm back on it. I just installed 9.10 Karmic on my Lenovo Thinkpad R61i, and it's beautiful....except there's no sound.

I have gone through the [Comprehensive Sound Problem Solutions Guide]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=205449"), to no avail. As well, I have searched the all of the Internets, and still have no sound.

Here is some system info:

```
tomdabomb2u@tomdabomb2u-thinkpad:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 20ac
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at fe100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I also added options [FONT="Courier New"]**snd-hda-intel model=thinkpad**[/FONT] to the end of my **[FONT="Courier New"]/etc/modprobe.d/alsa-base.conf[/FONT]** file. Still nothing. I would really like to hear the [Antoine Dodson song]("http://www.youtube.com/watch?v=hMtZfW2z9dw") on my laptop...not sure how much longer I can go.

Note: Everything in Sound Preferences appears to be working, I just still can't HEAR anything. 

Thanks yall,
Thomas

UPDATE: I notice that sound is working in the headphones jack...just not internal speakers. Does that help?

---

### Post by TomDaBomb2u on 2010-12-14
bump bump bump

---

