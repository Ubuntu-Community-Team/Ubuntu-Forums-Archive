---
title: "Audio input looping to speakers (Asus Xonar DS PCI) (12.04)"
date: 2012-09-25
forum: Multimedia Software
---

### Post by keithjr on 2012-09-25
I'm having a bit of a bizarre problem.  After a fairly large apt update, I rebooted to find that my microphone input is now looping back to my speaker output.

I tried updating to the audio-dev ppa as per [the troubleshooting procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"), to no avail.  I installed pavucontrol and muted anything that said "monitor" on it; didn't help.  What's *really* odd is that even if I mute my output device, I still hear the loopback just as loud as before, even though all normal output is correctly silent.  

Muting the microphone entirely does stop the loopback, but it also means I don't have microphone input anymore.  I just want to disable this new monitoring behavior, but there doesn't seem to be a knob for it anywhere.  Hints?  

```

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.

$ cat /proc/asound/cards
 2 [DS             ]: AV200 - Xonar DS
                      Asus Virtuoso 66 at 0xc800, irq 22

```


PS - also as an aside, [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) returns a 404, so I can't use that to get debug information.

---

