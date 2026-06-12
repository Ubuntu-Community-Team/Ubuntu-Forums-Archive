---
title: "Switching from gnome to Awesome, no sound"
date: 2009-01-09
forum: Multimedia Software
---

### Post by Pixel on 2009-01-09
Trying to run alsamixer I get this:

```

kyager@lucibox:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

```Any idea what I need to do?  *Audio works just find under gnome.*

nevermind that, audio used to work, now it doesn't, I'm a user of the audio group and all the required services are running.

aplay -l says it detects no soundcards.

It was working before I installed awesome3, that's all I know.

```

kyager@lucibox:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4800000 irq 22

```

---

