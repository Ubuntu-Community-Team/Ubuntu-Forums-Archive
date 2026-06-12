---
title: "Help Enabling Surround Sound with X-fi card"
date: 2009-02-20
forum: Multimedia Software
---

### Post by Krumar on 2009-02-20
Hello,
   I have a Creative Sound Blaster X-Fi XtremeGamer Fatal1ty Pro installed under Ubuntu 8.10 x86_64 bit.

Here is the output of lspci -v
```
02:0a.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0023
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at 8c00 [size=32]
	Memory at c3c00000 (64-bit, non-prefetchable) [size=2M]
	Memory at bc000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi


```
Right now the card is only playing sound through my front left and right speakers. I would like to set it up to play 5.1 to match my speakers. Right now I'm running the X-fi in conjunction with my motherboard's on-board sound card and using pulse audio to play them separately. I don't know if that changes anything, just wanted to try let you guys know everything I can about how I'm set up. 

Can anyone help me with surround sound?

Thanks in advance,
Krumar

---

### Post by MartyBuntu on 2009-02-20
> **Krumar said:**
> Hello,
   I have a Creative Sound Blaster X-Fi XtremeGamer Fatal1ty Pro installed under Ubuntu 8.10 x86_64 bit.

Here is the output of lspci -v
```
02:0a.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0023
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at 8c00 [size=32]
	Memory at c3c00000 (64-bit, non-prefetchable) [size=2M]
	Memory at bc000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi


```
Right now the card is only playing sound through my front left and right speakers. I would like to set it up to play 5.1 to match my speakers. Right now I'm running the X-fi in conjunction with my motherboard's on-board sound card and using pulse audio to play them separately. I don't know if that changes anything, just wanted to try let you guys know everything I can about how I'm set up. 

Can anyone help me with surround sound?

Thanks in advance,
Krumar


There is no mature ALSA driver for X-FI cards that supports multi-channel...*yet*.

The working OSS driver does not support multi-channel I believe.

---

### Post by catphive on 2009-06-16
That first reply is probably bogus. If you got this far, you already, like me, have the creative drivers installed probably. I doubt creative shipped without surround sound support...

In fact, this guy claims to have done it by switching to alsa sans pulse:
[http://ubuntuforums.org/showthread.php?t=1159632](http://ubuntuforums.org/showthread.php?t=1159632)

Although he doesn't really say everything he did to fix it.

I have the same problem on Ubuntu 9.04 x64. I do have the creative open source driver installed from creative's website. Only front speakers and sub work. Center and back do not.

I tried settings the number of channels to six as per here: [http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

Here's my lspci -v
0a:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
	Subsystem: Creative Labs Device 0044
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi

I can hear sound out of my front speakers, but for some reason speaker-test (following directions here: [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)) gives me this:
speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.18

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Playback open error: -2,No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Playback open error: -2,No such file or directory

Maybe it's some kind of pulse audio configuration issue?

---

### Post by xjgnsdof on 2009-08-19
Same problem, but my subsystem says 0031, not 0044 like catphive's or 0023 like the OP's.

---

### Post by xjgnsdof on 2009-08-23
The solution lies here: [http://ubuntuforums.org/showthread.php?t=1159632](http://ubuntuforums.org/showthread.php?t=1159632)

---

