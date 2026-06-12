---
title: "No sound output in Audacity"
date: 2010-06-20
forum: Multimedia Software
---

### Post by crazyfuturamanoob on 2010-06-20
Audacity doesn't play any sounds, although it can record from my microphone. And kubuntu plays the startup sounds (BTW, how to turn them off?).

```

arho@a91-156-166-231:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
arho@a91-156-166-231:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
arho@a91-156-166-231:~$ lspci|grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
arho@a91-156-166-231:~$ 

```

When I ran Audacity from command line I got this:
```

arho@a91-156-166-231:~$ audacity
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653
arho@a91-156-166-231:~$

```
It's complaining about "capture.pcm failed" but recording works! :confused::confused::confused: So how to fix the sound?

---

### Post by cchhrriiss121212 on 2010-06-20
You could try switching to ALSA in the audacity preferences or altering the playback/capture device.
It is also possible to remove pulse on a 10.04 install, but I'm not too sure why it worked when I did it.

---

### Post by crazyfuturamanoob on 2010-06-20
> **cchhrriiss121212 said:**
> You could try switching to ALSA in the audacity preferences or altering the playback/capture device.
It is also possible to remove pulse on a 10.04 install, but I'm not too sure why it worked when I did it.

It's already on ALSA in audacity preferences. And I tested all playback devices, nothing works.

And it seems to be that I don't have pulseaudio installed. Maybe kubuntu devs switched back to ALSA :D
```

arho@a91-156-166-231:~$ sudo apt-get remove pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pulseaudio is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
arho@a91-156-166-231:~$

```

---

### Post by crazyfuturamanoob on 2010-06-21
I don't like bumping but I can't find solutions with google. :(

---

### Post by Yellow Pasque on 2010-06-21
Do you have bluez-alsa installed? If you do and you don't have a need for bluetooth, remove it.

---

### Post by lidex on 2010-06-22
These may help:
[http://forum.audacityteam.org/viewtopic.php?f=37&t=3509]("http://forum.audacityteam.org/viewtopic.php?f=37&t=3509")
[http://forum.audacityteam.org/viewforum.php?f=18]("http://forum.audacityteam.org/viewforum.php?f=18")

---

### Post by El~Zilcho on 2010-06-23
> **Temüjin said:**
> Do you have bluez-alsa installed? If you do and you don't have a need for bluetooth, remove it.

You sweet, sweet bastard sir! I thought I'd try what you suggested even though I didn't think it would work, and I figured it would probably stop my mouse from working. It worked! Flicked everything back to pulseaudio and it's ON.

Just hope mouse works after restart :)

---

### Post by crazyfuturamanoob on 2010-07-01
Removing bluez-alsa did not help.

---

