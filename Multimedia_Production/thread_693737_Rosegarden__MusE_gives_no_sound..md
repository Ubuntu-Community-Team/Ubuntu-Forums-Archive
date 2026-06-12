---
title: "Rosegarden / MusE gives no sound."
date: 2008-02-11
forum: Multimedia Production
---

### Post by Jeek on 2008-02-11
I have a fresh installation of Ubuntu Studio 7.10 with the hope of trying to compose music, but I can't get those softwares working.

I have followed the tutorial on JACK connection, and could produce sounds in that manner. I am able to run Timidity and hear MIDI files as well.

However, when I started Timidity as a MIDI server, I heard nothing from Rosegarden or MusE, and received these responses from the terminal:

timidity -iA -B2,8 -Os1l -s

Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 8192, period size 4096 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 129:0 129:1 129:2 129:3
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')

What can I do to resolve the problem?

---

### Post by Stochastic on 2008-02-13
when you start timidity as your midi server, do you have jack up and running and are you assigning it to jack output with the -Oj flag?

---

### Post by Jeek on 2008-02-15
After trying your advice (ie. replacing -Os1l with -Oj in the command, with JACK switched on), it works.

Thanks a lot.

By the way, how can I add flac to Rosegarden? While I don't think I will need to save in that format for the moment, the pop-up is getting annoying.

---

### Post by bir7 on 2008-02-17
@Stochastic: Thank you very much. Now i can hear Midi Sounds with Rosegarden! :guitar:

---

