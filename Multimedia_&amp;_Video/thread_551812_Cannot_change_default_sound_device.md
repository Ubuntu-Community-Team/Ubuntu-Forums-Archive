---
title: "Cannot change default sound device"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by Serph on 2007-09-15
Hi there,

 My computer has two sounds cards.

1) NVida CK804 (Onboard) (Currently default)
2) Chaintech AV710 (PCI) (I want this to be the default Sound Card)

I want 2) Chaintech AV710 to be my default sound card and be used for playback recording etc.
Currently I can only get sound playback to come through my onboard sound. 

System>Preferences>Sound seems to have no effect on changing device

I've tried setting options to ALSA/Autodetect/ICE724  and default mixer track as Chaintech av710(alsa mixer)

Doesn't seem to work.
```

serph@ubuntu:~$ gksudo asoundconf list
Names of available sound cards:
CK804
UART
AV710
serph@ubuntu:~$ gksudo asoundconf set-default-card AV710
```

Alsamixer still shows device ck804 when I open it
```
serph@ubuntu:~$ alsamixer
```

Help?

---

### Post by linuxwizard on 2007-09-15
Look on this page for:  Configuring default soundcards / stopping soundcards from switching

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

