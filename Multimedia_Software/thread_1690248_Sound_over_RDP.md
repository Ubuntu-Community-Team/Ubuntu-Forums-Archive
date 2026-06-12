---
title: "Sound over RDP"
date: 2011-02-18
forum: Multimedia Software
---

### Post by Tziff5 on 2011-02-18
Hi all,

I have a headless computer (call it A) which is used only to play audio (I would have connected it to my TV as well, but it refuses to work).

I want it to be able to conveniently play music, so the plan is to go to my desktop, remotely access A's desktop, fire up audacious, and start playing.
I tried working with VNC, however it seems like VNC attaches to an existing user session, i.e. i have to be physically logged in the the machine's console, which is not possible to do since it's supposed to be headless. so I resorted to rdp.

I installed xrdp and i can indeed log in without being physically logged in, its a completely new session. I understand that xrdp doesn't forward sound - but I'm good with that. I want it to play on A's local speakers, not my speakers. however, in "sound preferences" I only have one output device - "Dummy Output", nothing plays on the local speakers.
I tried the ALSA plugin, with PCM and mixer devices set to "default pcm" and "default mixer" devices, but I still get the same result - audacious is playing, however the sound goes to some null audio device. if I try the OSS plugin, the track won't play at all and just immediately to the next track, which won't play at all, and so on till the end of the playlist.

here is some output:
```
tziff5@bigfan:~$ aplay -l
aplay: device_list:235: no soundcards found...
tziff5@bigfan:~$ lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Device 829f
        Flags: bus master, fast devsel, latency 0, IRQ 43
        Memory at fbdf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
...
tziff5@bigfan:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
tziff5@bigfan:~$ uname -a
Linux bigfan 2.6.35-25-generic-pae #44-Ubuntu SMP Fri Jan 21 19:01:46 UTC 2011 i686 GNU/Linux
tziff5@bigfan:~$ xrdp --version
xrdp: A Remote Desktop Protocol server.
Copyright (C) Jay Sorg 2004-2009
See http://xrdp.sourceforge.net for more information.
Version 0.5.0
tziff5@bigfan:~$ pulseaudio --version
pulseaudio 0.9.21-63-gd3efa-dirty
```(pulseaudio was installed from the repositories, dunno why it's dirty).
the outputs above were taken simply with ssh'ing to the machine. while that ssh session is still open, i logged in the the machine's console with my username, returned to the open ssh session and:
```

tziff5@bigfan:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```when I logged out from the console, aplay would again not find any soundcards.

it seems like its not related to xrdp, and that sound will simply not work if you're not physically logged in.
does anyone have any idea as to what's going on and how to resolve this?

---

### Post by Tziff5 on 2011-02-22
solved by adding my user to the 'audio' group.

---

