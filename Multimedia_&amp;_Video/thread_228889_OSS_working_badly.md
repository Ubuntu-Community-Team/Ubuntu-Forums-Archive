---
title: "OSS working badly"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by serras on 2006-08-03
A pair of weeks ago, I updated my Ubuntu 6.06 LTS machine to kernel 2.6.15-26. When I rebooted, the sound started to behave strangely: the sound were repeated in blocks of 2 or 3 seconds, I mean, 3 seconds were listened, then repeated over and over, until other 3 seconds were listened and so on. So I worked with kernel 2.6.15-25 in this time.
The las update for 2.6.15-26 seemed to repair my problem. However, I've been able to test that ALSA and ESD work correctly, but OSS still has this problem. Is there some solution?

---

### Post by croak77 on 2006-08-03
Do you need OSS? You said ALSA works.

---

### Post by christhemonkey on 2006-08-03
I second croak77, OSS is severly deprecated...
And anything that needs it can be used with alsa.

---

### Post by serras on 2006-08-03
Hi again,
I've tested and it seems that is ALSA what is causing the problem, the ones with OSS went because I use alsa-oss. However, now the problem is that ALSA just "jumps over" parts of the sound it is playing. In MPlayer I'm getting "alsa-play xrun of at least xx.xxx miliseconds" every time I'm playing something.
I just happens with kernel 2.6.15-26. Maybe it has something to do with /proc/sys/dev/rtc ??

---

### Post by croak77 on 2006-08-03
Can you elaborate more? What sound card do have? What modules are you using? Do other players work or just not Mplayer?

---

### Post by serras on 2006-08-04
I'm using Ubuntu 6.06 LTS, that was installed over Ubuntu 5.10. I've got a VIA 8235 souncard that is correctly detected. Everything works OK, but on kernel 2.6.15-26. Every single app using sound suffers from the same problem as the stated for MPlayer, for example, both XMMS and Beep Media Player just "jump over" fragments of songs.
I don't have any special modules or services loaded, except kqemu for QEmu. I tried purging and reinstalling ALSA as stated in the guide in this Forum, but it is still the same.

---

### Post by christhemonkey on 2006-08-04
In xmms, if you go into plugins, then output, and select configure on ALSA,
You should be able to set the buffer size.
Set it to, say, double what it currently is.


I think what you are hearing are "xruns", which occur when a buffer is not emptied when more data comes to fill it.

---

