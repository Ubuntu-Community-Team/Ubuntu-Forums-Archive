---
title: "Rear and Front output switch by default"
date: 2012-09-25
forum: Multimedia Software
---

### Post by dr-kart on 2012-09-25
I have SB Live:
```
Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
Subsystem: Creative Labs SBLive! 5.1 Model SB0100
Flags: bus master, medium devsel, latency 32, IRQ 1
I/O ports at c000 [size=32]
Capabilities: <access denied>
Kernel driver in use: snd_emu10k1
Kernel modules: snd-emu10k1
```I only use it for 2.0 channel configuration. To get **best**/better stereo sound quality it is recommended to use REAR OUTPUT (black) instead of FRONT OUTPUT (green).

So how can I get only **2.0 stereo** output with rear and front channels switched by default?

---

### Post by jonnyboysmithy on 2012-09-25
EDIT: what I posted you already tried...

---

### Post by dr-kart on 2012-09-25
> **jonnyboysmithy said:**
> EDIT: what I posted you already tried...
which post?

---

### Post by jonnyboysmithy on 2012-09-25
This is what I posted earlier but the I edited it and erased it. Anyway this is what it used to say:> 
On my computer (ubuntu 12.04) click the sound icon upper right corner,  from the drop down menu select 'sound settings' and under the 'output'  tab select the drop down menu 'Mode' there you should be able to use  stereo or surround sound.

Not sure if this will make it use the front or back speakers though it did the trick for me.
But then I reread your post and realized thats exactly what you did.#-o

---

### Post by dr-kart on 2012-09-26
Having read (old) pulse audio howto here, I did as follows:

1. Not necessary but I did move these two files
 ```
cp /etc/pulse/daemon.conf /etc/pulse/default.pa -t ~/.pulse/
```2. Edited ~/.pulse/default.pa to add the string:
```
load-module module-alsa-sink device_id=0 channels=2 channel_map=rear-left,rear-right
```

After that I get working sound via REAR OUTPUT (black). But :confused: as I think, this procedure gave me actually 4 channel audio. So it's two front and two rear channels duplicating each other. Is this normal? And I guess the best idea to have ONLY TWO channels, but switched (by software, by os) from FRONT to REAR. What do You think?

---

