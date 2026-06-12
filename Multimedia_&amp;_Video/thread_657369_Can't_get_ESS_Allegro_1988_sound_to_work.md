---
title: "Can't get ESS Allegro 1988 sound to work???"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by amdalex on 2008-01-03
I have an older Compaq computer with a dual boot between Ubuntu Edgy Eft and Windows 98. The sound only works in Windows. In sound options it shows my card but nothing comes out of the speakers. I don't know what to try or do. How might I get sound to work? thanks a bunch:confused:

---

### Post by carrett on 2008-01-03
Try running alsamixer. You might need to install alsa-utils:

```
sudo aptitude install alsa-utils
```

Sometimes things are muted, you want to make sure the Master and PCM settings are not muted and turned up loud enough for you to hear. Then try playing a .wav file with:

```
aplay <somefile.wav>
```

It should work. Good luck.

---

### Post by amdalex on 2008-01-03
How do I run Alsamixer? Also everything is turned up and still no sound.:(

---

### Post by carrett on 2008-01-03
Running alsamixer is as simple as opening a terminal and typing 'alsamixer' (no quotes) followed by the <enter> key. then you use the arrows to navigate the mixer.

In any event, let's check out your module situation. Can you paste the output of:

```
lsmod|grep snd
```According to the ALSA website, you want to see snd-card-maestro3, for one.

---

### Post by amdalex on 2008-01-03
Nevermind, I got it to work.

---

### Post by jeffemmert on 2008-04-23
I have the same problem whether running Ubuntu 7.10 or Mandriva Spring 2008. As nice as these two distros appear, neither is able to correctly drive my ESS Allegro 1998 on a Gateway 600 YGR laptop. When I boot with XP Pro, both channels work fine. In Linux, I only get the left channel, even though various tests show graphs of both channels working. Is there a Linux-based driver for the ESS that I could install?

---

