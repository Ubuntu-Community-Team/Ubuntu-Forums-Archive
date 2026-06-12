---
title: "Music only at the same time as &quot;AC Adapter beep&quot;"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by Kyle Reese on 2007-07-01
Problem:
I don't have any sound on my laptop. However, there is an exception. When I inserts or pulls the AC Adapter connector, i get the usual "system beep". Under those one or two seconds I also hear the music I'm currently playing in XMMS. I have browsed some of the other sound problem threads, but none of them seems to help, for this problem. Any tips or solutions, anybody?

System data:
Xubuntu 7.04 on a IBM Thinkpad A22p (installed yesterday). The system identifies **Sound Fusion CS46xx** as my sound device.

```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]

```

This is the current volume control set up:
[IMG]http://www-und.ida.liu.se/~joaer919/screenshot.png[/IMG]

---

### Post by wolfen69 on 2007-07-01
did you try checking off the IEC958 boxes?

---

