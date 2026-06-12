---
title: "No sound - feels like I've tried everything"
date: 2010-08-24
forum: Multimedia Software
---

### Post by Ubun00btu on 2010-08-24
I originally had sound through my AC97 (Realtek) onboard sound.  I have a Creative X-Fi ExtremeMusic that I wanted to get working, so I downloaded the DEB file and installed it.   *poof*  my sound quit working altogether.

I'd like to get my sound working again, better yet, to get the X-Fi working.  I've been through dozens of posts and followed directions trying to rebuild ALSA and everything else and I can't get anything to work.

Help, plz!!

Here is the info that most folks seem to request when dealing with these issues:

aplay -l
```
aplay: device_list:223: no soundcards found...
```

lspci -v (just the sound card info...)
```

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: eVga.com. Corp. Device 1001
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at cfff0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: oss_hdaudio

05:09.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0021
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at 7c00 [size=32]
	Memory at c3c00000 (64-bit, non-prefetchable) [size=2M]
	Memory at bc000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: oss_sbxfi
```

lspci | grep Audio

```
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
```

Ubuntu 10.04.1 LTS, 64 bit, Linux 2.6.32-24-generic.

---

### Post by LarsUb on 2010-08-24
Uninstall, any mixer in your system (pulseaudio, oss, alsa, esd, etc, etc).
$ apt-get purge MixerName
or
$ aptitude remove MixerName

Reboot
Then, try by installing just the Alsamixer, try manually or from software center but probably you'd have to install some front ends for the mixer and the volume control, and add them to the init.d or startup applications in System > Preferences

Reboot
Verify if your card its detected,
$ aplay -l
$ aplay -L
Try your sound with alsa.
$ speaker-test -D default

If this doesnt work, try by reinstalling your soundcard driver, and then re-install the alsa mixer.
Good luck.

---

### Post by Ubun00btu on 2010-08-24
Son of a gun...

LarsUb FTW!=D>

Good job, my friend; and thank you.  Both onboard and XFi cards have output now.  

As a side note to anyone that follows these directions, if you use "apt-get purge (MixerName)", it will remove ubuntu-desktop along with alsa and pulseaudio!  Before restarting you need to:  Sudo apt-get install gdm ubuntu-desktop, or your OS will loop back to the login screen each time you enter your password.

---

### Post by LarsUb on 2010-08-24
Im just some newbie like everyone, but we always can help.. so we could build a better world.. hehe. Share your knowledge and help to others.
Regards!

---

### Post by tommcd on 2010-08-24
> **Ubun00btu said:**
> 
As a side note to anyone that follows these directions, if you use "apt-get purge (MixerName)", it will remove ubuntu-desktop along with alsa and pulseaudio.
So, just out of curiosity, what mixer(s) did you remove? Was it just alsamixer? Or something else?
Do you still have pulseaudio installed?

---

### Post by Ubun00btu on 2010-08-25
I removed everything I had.  Pulseaudio, OSS, and alsamixer.  Will post about pulseaudio in a bit, currently on my windoze boot working on other things.

---

### Post by tommcd on 2010-08-25
> **Ubun00btu said:**
> I removed everything I had.  Pulseaudio, OSS, and alsamixer.  Will post about pulseaudio in a bit, currently on my windoze boot working on other things.
I bet it was the fact that you removed pulseaudio that fixed your problem. A lot of people have had problems with pulseaudio.

---

