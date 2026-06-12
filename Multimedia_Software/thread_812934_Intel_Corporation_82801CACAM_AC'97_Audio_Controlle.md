---
title: "Intel Corporation 82801CA/CAM AC'97 Audio Controller clock problem"
date: 2008-05-30
forum: Multimedia Software
---

### Post by zaomaster on 2008-05-30
I've got a Thinkpad T30 with this (Intel 82801CA/CAM AC'97) controller, using the snd-intel8x0 driver.  Everything works fine on a fresh boot, but if I suspend or hibernate the computer when I turn it back on again something goes wrong.

It's as if the chipset and/or driver resets the clock speed too fast.  So the tempo and pitch of all audio is too fast/high.

Any thoughts as to what I might be able to do?  I tried manually setting the clock speed, and it worked for when I booted fresh, but did nothing for resuming...

any help would be great!

---

### Post by zaomaster on 2008-05-31
anybody?

I'm not sure how to make the driver set the ac97_clock correctly upon resuming...

---

### Post by zaomaster on 2008-06-02
would it have anything to do with the newer 'tickless' kernel?

---

### Post by zaomaster on 2008-06-16
So it's been a couple of weeks and I'm still at an impasse.  You all are really smart, somebody's got to have a least a clue in what direction I should go.  This is one of the last quirks and my system is perfect!

---

### Post by rikdeek on 2008-09-30
Hi there,
I also have this sound chipset in a toshiba satellite 1110 z15.
I don't know enough about drivers and sound seems to be an awkward area because its so easy to end up with multiple sound servers/engines installed.

If anyone could help us to find out more about our systems, or how to run some tests for the presence of the correct drivers/settings, that would be great.

zaomaster - Have you found anything?

Thanks very much in advance!

---

### Post by zaomaster on 2008-10-10
I would love to say that I've found an answer. But I haven't.

I wish I could find out what's going on, because once this issue gets fixed I've got my perfect install. No need to shutdown ever, low power consumptions, etc.

Keep us updated if you find anything that works.

---

### Post by flamenco108 on 2008-11-17
Hey, this is ridiculous. Yesterday i destroyed kubuntu on my Thinkpad t30 with the same sound chipset, where it worked fine and clear. But my laptop is old and has dead one RAM slot, so I can't expand RAM over 512MB. And I installed xubuntu today, and I have the same problem:

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: IBM ThinkPad T30
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]


```
root@flap:/home/flamenco# 
root@flap:/home/flamenco# aplay -l
aplay: device_list:205: nie znaleziono &#380;adnych kart d&#378;wi&#281;kowych...
root@flap:/home/flamenco# strace -eopen alsamixer
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/dev/snd/controlC0", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC0", O_RDONLY)          = -1 ENOENT (No such file or directory)

alsamixer: function snd_ctl_open failed for default: No such file or directory
Process 6964 detached


```

---

### Post by psyke83 on 2008-11-17
> **zaomaster said:**
> I've got a Thinkpad T30 with this (Intel 82801CA/CAM AC'97) controller, using the snd-intel8x0 driver.  Everything works fine on a fresh boot, but if I suspend or hibernate the computer when I turn it back on again something goes wrong.

It's as if the chipset and/or driver resets the clock speed too fast.  So the tempo and pitch of all audio is too fast/high.

Any thoughts as to what I might be able to do?  I tried manually setting the clock speed, and it worked for when I booted fresh, but did nothing for resuming...

any help would be great!

How did you manually set the clock speed? When your system suspends, usually the kernel modules get unloaded. Therefore, you need to ensure that the appropriate kernel module options are parsed correctly when your machine resumes.

You should edit /etc/modprobe.d/alsa-base, and end to the end of the file:```
options snd-intel8x0 ac97_clock=[COLOR="Red"]x[/COLOR]
```

Be sure to enter the proper value for your case.

Perhaps the ac97_clock rate isn't your problem, however.

---

### Post by zaomaster on 2008-12-11
> **psyke83 said:**
> How did you manually set the clock speed? When your system suspends, usually the kernel modules get unloaded. Therefore, you need to ensure that the appropriate kernel module options are parsed correctly when your machine resumes.

You should edit /etc/modprobe.d/alsa-base, and end to the end of the file:```
options snd-intel8x0 ac97_clock=[COLOR="Red"]x[/COLOR]
```

Be sure to enter the proper value for your case.

Perhaps the ac97_clock rate isn't your problem, however.

You were right, ac97_clock wasn't the issue. PulseAudio was not shutting down during suspend/hibernate. Thus the snd module was unable to unload properly. I added scripts to /etc/acpi/suspend.d and /etc/acpi/resume.d and all is well!

---

