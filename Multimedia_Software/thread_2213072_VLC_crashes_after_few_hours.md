---
title: "VLC crashes after few hours"
date: 2014-03-24
forum: Multimedia Software
---

### Post by joaquim3 on 2014-03-24
Hello,

UBUNTU 12.04.4 LTS

I've been using VLC for some years as video Engine for a JAVA application. I control VLC through libvlc usign VLCJ. It is an application that plays a list of short videos undefinetely and the sequence is managed by a Web App. 

Since 2 weeks it suddenly started to crash after a few hours (1,5 to 4h) playing.

I have updated everything that was available in Update Manager. I also tried with VLC 2.1 instead of default 2.0.8.

These are the common erros I see in logs:

[FONT=arial][0x7e5eb1b8] main input error: ES_OUT_SET_(GROUP_)[/FONT][FONT=arial]PCR[/FONT][FONT=arial]  is called too late (pts_delay increased to 4747 ms)[/FONT]
[FONT=arial][0x7e5eb1b8] main input error: ES_OUT_RESET_PCR called[/FONT]
[FONT=arial][h264 @ 0x5d6bf580] mmco: unref short failure[/FONT]
[FONT=arial][h264 @ 0x6fe69da0] mmco: unref short failure[/FONT]
[FONT=arial][h264 @ 0x6fe69da0] mmco: unref short failure[/FONT]
[FONT=arial][h264 @ 0x5d6bf580] illegal short term buffer state detected[/FONT]
[FONT=arial][0x7e5eb1b8] main input error: ES_OUT_SET_(GROUP_)[/FONT][FONT=arial]PCR[/FONT][FONT=arial]  is called too late (jitter of 11556 ms ignored)[/FONT]
[FONT=arial][0x7e5eb1b8] main input error: ES_OUT_RESET_PCR called[/FONT]
[FONT=arial][h264 @ 0x5d6bf580] mmco: unref short failure
[/FONT][FONT=arial]
After some time the CPU usage goes to 100% and then it start do play slowly, slowly... glitchy.. until it stops.

I use these parameters to play **--no-title-show --no-xlib**

Thanks in advance for any help.
Any help?
[/FONT]

---

### Post by TheFu on 2014-03-24
Same content or does it happen with different content by different authors too?

Does mplayer handle the same content better?

---

### Post by joaquim3 on 2014-03-24
> **TheFu said:**
> Same content or does it happen with different content by different authors too?

Does mplayer handle the same content better?

Different content, different authors.

Didn't try with mplayer. I can do that tomorrow and write here the results.

---

