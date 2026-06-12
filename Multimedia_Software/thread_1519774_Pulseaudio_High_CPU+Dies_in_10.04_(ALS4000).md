---
title: "Pulseaudio High CPU+Dies in 10.04 (ALS4000)"
date: 2010-06-28
forum: Multimedia Software
---

### Post by arindrel on 2010-06-28
Hi, i know there already a LOT of posts on the forum about pulse audio, i have read a good number of them, but don't seem to be any closer to a fix.  I assume (given that my problem is replicable) that someone can just point me in the right direction of the fix.

I Had some problems upgrading from Karmic to lucid, Pulse just kinda dies, but i left it be.  Recently i brought a fresh 1TB hard disk and decided it was time for a clean install of 10.04 to fix that.  Im running of a clean install, only additional packages i have pulled down are the Nvidia driver, wine, and VLC.. the rest is 'out of the box' config.  Have tried reinstalling 3 or 4 times, i get the same sound problem each time.

Pulse works fine to start with, i can play music, play warcraft under wine with sound.  However as time goes on i find that the pulseaudio process takes up more and more cpu time.  Eventually it hits about 90% plus then crashes out.  The system hangs for a minute, then resumes with no sound.  When i run "top" the pulseaudio daemon is no longer running.  The only way to get sound back is to manually "Pulseaudio -D" or to reboot the system.  This isn't just "a warcraft problem".  It happens with Spotify (also under wine) Rthymbox, and VLC.  

A friend suggested i run the Pulseaudio daemon with a higher cpu importance?  Is that sensible?  Are there any pages where i can read up on how better to configure pulse?  I have read lots of guides about linux sound problems and most seem to be about alsa not pulse.  

Any ideas?

My hardware info is included below, please let me know if any further diagnostic info is needed to trouble shoot this.  Any help is appreciated

```

arin@chrome:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ALS4000 [Avance Logic ALS4000], device 0: ALS4000 DSP []
  Subdevices: 1/1
  Subdevice #0: subdevice #0


arin@chrome:~$ lspci -v


----snip ----

04:07.0 Multimedia audio controller: Avance Logic Inc. ALS4000 Audio Chipset
	Subsystem: Avance Logic Inc. ALS4000 Audio Chipset
	Flags: bus master, fast devsel, latency 64, IRQ 16
	I/O ports at 9c00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ALS4000
	Kernel modules: snd-als4000


```

---

### Post by reve_etrange on 2010-09-07
High CPU usage in Pulse can be caused by resampling, although presumably you are using the default, low quality resampler.  Take a look at /etc/pulse/daemon.conf (you can put a user-specific copy in ~/.pulse/daemon.conf) and then read about the different resamplers available.
The default sample rate for pulseaudio is 44.1 KHz, same as CD audio, but most modern (non-CD) sources are 48 KHz...try changing the
```
default-sample-rate = 44100
```
line to "... = 48000"

PS top only shows the most active/demanding processes, try using ```
$ps aux | grep pulse
``` or ```
$pgrep pulseaudio
```
although running pulseaudio with -D should fail if pulse is still running.

---

