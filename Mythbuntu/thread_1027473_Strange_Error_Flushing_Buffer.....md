---
title: "Strange Error Flushing Buffer...."
date: 2009-01-01
forum: Mythbuntu
---

### Post by Ronno6 on 2009-01-01
I really am in need of some help. The random sound issue strikes again.

At the start of the recording, the backend log indicates the show name, channel number on cardid 1, sourceid 1, then adds the phrase "strange error flushing buffer...." to the same line. The sound is missing data, and the video is accelerated due to the synch function. File size is decreased from that of a normal recording, down from 768mb to 738mb due to missing audio. Video plays normally in the preview thumbnail, so problem is audio related. 

The above is the only abnormal entry I see in the logs.If there is information needed to help me diagnose and cure this problem, please let me know and I will try to furnish what is needed.

Note: the next recording (immediately after this one)was flawless. 

I am really frustrated by this problem as it makes recording unreliable.

Can somebody _PLEASE_ help me??

Mythbuntu 8.04.1
Dell Optiplex GX370
Pentium4 2.8g
2g ram
Dvico Fusion HDTV5 RT Gold
PNY 6200GX 256mb

---

### Post by bauner on 2009-03-30
could you solve this problem?

I have the same error sometimes, but i can´t find whats the reason.
It happens randomly on all channels, but i´ve never had this issue with reocrdings <60 min.

For testings purposes i´ve tried not to auto encode recordings.
most recordings plays fine but in a few recordings the playback time counter hangs but the video play´s correctly to it´s end(often at 1h 19min playback time). When i try to encode such an file the strange error flushing buffer appears and the encoded file have no sound but the playtime counter works fine....

I tried more ram, played with irq latency, another tuner and a other mainboard/cpu.

Sorry for my bad english. I hope you now what I try to explain...

---

### Post by azmyth on 2009-03-30
May want to try running the frontend in a terminal with mythfrontend -v all.

I ran into this when I was running Fedora 6 as it would give the same error and then segfault making it unusable. This would happen on first recording on reboot or if idle too long. After the segfault it would run great. I tried all the irq latency and it didn't work. In the end, I thought it had to do with alsa but I never could figure it out. When I upgraded to F8 it went away.

---

### Post by Ronno6 on 2009-04-02
I never resolved this issue. Web searches gave information that the "buffer overflow," and "strange error flushing buffer" messages   indicate a  LAME problem for "some obscure reason." All reports tend to indicate that it is of no significance.Maybe not, but the playback of the recording suffers due to synching of video with incomplete audio data. The problem appears to be totally random, and that renders the whole shebang undependable. I've pretty much given up.
Good luck.

---

