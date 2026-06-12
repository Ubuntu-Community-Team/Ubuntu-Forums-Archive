---
title: "Distorted sound when playing 48 kHz files"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by cronholio on 2006-10-16
Playback of sound files that do not have a sample rate of 22 or 44 kHz, but 48 kHz, is terribly distorted on my computer (runs Dapper). This happens for movies as well as music files, in applications that use GStreamer as well as in VLC. I guess the problem is related to my soundcard, but I don't know where to start troubleshooting.

By the way, the soundcard is recognized as a USB PnP sound device, even though it is onboard (ASRock 939Dual-VSTA Mainboard).

---

### Post by Alucard_swe on 2006-10-17
I have the same motherboard and same problems but music works but if I try too watch some video its the same freaky sound you have.
I found this but havent tried it yet ( [http://ubuntuforums.org/showthread.php?t=265040&highlight=VSTA](http://ubuntuforums.org/showthread.php?t=265040&highlight=VSTA))

I really hope this problem will easy be fixed or be fixed in ubuntu 6.10.

---

### Post by cronholio on 2006-10-18
The reason is that most videos probably are "backups" from a DVD, which I believe have a sample rate of 48 kHz. I've tried the solution posted in the thread and it partly works. I can now play all music files in XMMS and all video files in Gxine.

---

### Post by cronholio on 2006-10-18
Okay, VLC now also works if I set it to ALSA output (Settings->Preferences->Audio->Output modules->Advanced options->ALSA->Save).

---

### Post by Alucard_swe on 2006-10-18
Nice but I use mplayer for all my videoplayback? any luck there?

---

### Post by cronholio on 2006-10-18
Now it works. I enabled "software mixer" in MPlayer and set it to ALSA output.

---

### Post by Alucard_swe on 2006-10-20
I meant "mplayer" also can´t found where the alsa config needs too be :(

---

### Post by bep on 2006-10-27
This is a big problem for me, too:

Mplayer is the only player that can play 48 kHz files correct; I would, however, love to use some more sofisticated interfaces like Amarok etc, but no avail.

---

### Post by handy on 2006-10-28
You do know about **alsamixer**?

Type that in to the **Terminal**, & keep scrolling to the right.

I rule of thumb is to not have any of the setting meters in the red.

I hope that helps.

---

