---
title: "Sound problem"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by EvilMarshmallow on 2007-01-24
Hey all, 

Total noob here, trying to figure out how to install sound card drivers.  I have an onboard audio chipset (Analog Devices AD1885, I think, judging from what I saw in Device Manager).  I get sounds ok, but when I run a game that requires directional audio (such as Call of Duty), my sounds lag about half a second behind real time.  They sound perfect, they come through in the proper directions, they're just laggy.  One of the error messages I got said that i had this was because my sound card didn't support "direct to hardware" or something like that.

When I open winecfg and click on the audio page, I get the following message in the terminal:

[INDENT]ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory[/INDENT]

I have alsa-base and alsa-utils packages installed.  Is there something else I need?

---

### Post by al_sharpe on 2007-03-08
Hello EvilMarshmallow:

The snd-seq kernel module did not get loaded by default.

```
sudo modprobe snd-seq
```

I found this solution posted by nixx on amsynth

Enjoy

Al Sharpe

---

### Post by EvilMarshmallow on 2007-03-09
This repaired the little error messages I was getting but the sounds still lag by about half a second.

Anyone have any ideas?

---

