---
title: "Headphone jack has sound, default speakers don't."
date: 2009-01-10
forum: Multimedia Software
---

### Post by Kareeser on 2009-01-10
Hey everybody,

So everything was running great until sound stopped working for no particular reason. Upon further investigation, I find that only sound from the headphone jack works, and not my built-in speakers.

I tried "modprobe snd-intel8x0", but there was no output... no clue what that means.

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

===

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Device 018d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
	Memory at e0100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

===

```

kareeser@kareeser:~$ paplay /usr/lib/openoffice/share/gallery/sounds/space.wav
Connection failure: Connection refused

```

===

```
kareeser@kareeser:~$ killall -9 pulseaudio
[1]+  Killed                  pulseaudio
kareeser@kareeser:~$ pulseaudio &
[1] 8556
kareeser@kareeser:~$ W: W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: pid.c: Stale PID file, overwriting.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

```

===

For some weird reason, sound only comes out of the headphone jack. I don't know whether it's not switching from one output to the other properly, or whether the speakers just stopped working on my laptop, but this is an odd problem!

I've tried restarting the alsa sound server, to no avail, restarting many times.

I use a Dell 700m. Any help would be appreciated! :)

I've attached the output to "alsamixer -Dhw"... I don't know why there are "00"s under the sliders... that looks like it doesn't belong... :S

---

### Post by gettinoriginal on 2009-01-10
Here are several threads that may help:  :p

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Kareeser on 2009-01-24
Already tried all of that stuff.

Anyway, problem diagnosed:
[http://www.lukemiller.org/journal/2006/06/broken-speaker-wires-on-dell-700m.html](http://www.lukemiller.org/journal/2006/06/broken-speaker-wires-on-dell-700m.html)

---

