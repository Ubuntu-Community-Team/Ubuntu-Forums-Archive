---
title: "[SOLVED] From everything works to Snap, crackle and pop sound in Ubuntu 8.10"
date: 2008-11-10
forum: Multimedia Software
---

### Post by alexandreracine on 2008-11-10
Ubuntu 8.10 intrepid, all updates until 10 nov. 2008.

I was listening to music while working with Rhythmbox and suddently the music froze while repeating the last 1/4 second over and over again.

After a couple of testing, updates, reboots, and the fact that the sound work perfectly with Vista (on another partition), I have conclude that the sound does not work anymore with Ubuntu. But why?

All I get from the speakers is some Snap, crackle and pop like the Rice Krispies ([http://en.wikipedia.org/wiki/Rice_Krispies](http://en.wikipedia.org/wiki/Rice_Krispies))

Everything seems to be fine hardware. (And it does work in Vista). Can anyone help? Thanks.

# sudo aplay -l

carte  0: Intel [HDA Intel], périphérique 0 : ALC883 Analog [ALC883 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC883 Digital [ALC883 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0


# sudo lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by psyke83 on 2008-11-10
There is an odd bug where sometimes the ALSA PCM or Master mixer resets itself to 0%. When this occurs, the speakers will emit a very slight crackling (which is actually another bug - it should be completely silent at 0%... go figure).

The fix is to turn the volume back up:

```
$ alsamixer -Dhw
```

---

### Post by alexandreracine on 2008-11-10
Yep, that did the trick!

I went a little furthur and commented some related bugs [https://bugs.edge.launchpad.net/ubuntu/+source/alsa-utils](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-utils)

Thanks.

---

### Post by dmcbob on 2008-11-15
thanks a bunch!

---

### Post by verdemachina on 2008-12-09
Yes, thanks so much for the tip about the PCM volume level.

Cheers,

Brad

---

### Post by gychang on 2008-12-09
> **psyke83 said:**
> There is an odd bug where sometimes the ALSA PCM or Master mixer resets itself to 0%. When this occurs, the speakers will emit a very slight crackling (which is actually another bug - it should be completely silent at 0%... go figure).

The fix is to turn the volume back up:

```
$ alsamixer -Dhw
```

I have the same problem playing flac files but don't understand the above.

do I  enter the code and turn the volume back up?

thanks,

gychang

---

### Post by gychang on 2008-12-09
> **psyke83 said:**
> There is an odd bug where sometimes the ALSA PCM or Master mixer resets itself to 0%. When this occurs, the speakers will emit a very slight crackling (which is actually another bug - it should be completely silent at 0%... go figure).

The fix is to turn the volume back up:

```
$ alsamixer -Dhw
```

Entered the code but get an error.

"alsamixer: function snd_ctl_open failed for hw: No such file or directory"

help.  still crackling...

gychang

---

### Post by BARlotta on 2008-12-13
> **psyke83 said:**
> There is an odd bug where sometimes the ALSA PCM or Master mixer resets itself to 0%. When this occurs, the speakers will emit a very slight crackling (which is actually another bug - it should be completely silent at 0%... go figure).

The fix is to turn the volume back up:

```
$ alsamixer -Dhw
```

Just found this post and it got me back up and running.  One day I booted up and was left with crackling speakers and this fixed it (after trying lots of other "fixes").  I'm going to post this in a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927") I was tracking on.

:D

---

### Post by busmechanic on 2009-01-03
New user to Linux and Ubuntu Great OS BTY Loving it,

I had same problem with cracking and found that by unchecking the digital output under ppreferance did the trick for me.

---

