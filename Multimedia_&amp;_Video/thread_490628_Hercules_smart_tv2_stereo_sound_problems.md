---
title: "Hercules smart tv2 stereo sound problems"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by hasplu on 2007-07-02
Hi all,
I know there was written a lot about it, but after nearly a month struggling I managed to make it working in 7.04, but still shows picture only, no sound

I read lots of forums and can't find my solution, so if anyone can help gets a sixpack of beer :))

```
02:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
       Subsystem: PROVIDEO MULTIMEDIA Co Ltd Unknown device 952b
       Flags: medium devsel, IRQ 17
       Memory at f4001000 (32-bit, prefetchable) [size=4K]
       Capabilities: <access denied>

hasplu@Tupcho:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
 Subdevices: 1/1
 Subdevice #0: subdevice #0

from  dmesg | grep Bt878
[  155.097305] bttv0: Bt878 (rev 17) at 0000:02:05.0, irq: 17, latency: 32, mmio: 0xf4000000
[  155.475546] bt878: Bt878 AUDIO function found (0)
```

I feel the key is in the last line, but can't figure it out:(

---

### Post by hasplu on 2007-07-03
come on guys! anyone any idea where to search for? I'm googling 2 days and no luck !

---

### Post by hasplu on 2007-07-06
solved, but thanks for the help!

anyone specialist about LIRC? can't execute modprobe lirc_dev and modprobe lirc_i2c ?

---

### Post by Skerit on 2008-02-02
Could you perhaps, after all these months, indulge us?

I once got the sound to work, but it was very bad quality... Now I'm back at square one, *no* sound.

When I tried to load the snd-bt87x module with the load_all option I was able to see the sliders in the alsa-mixer but it didn't do much, still had no sound...

---

