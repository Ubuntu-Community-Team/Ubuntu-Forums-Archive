---
title: "mounting sound card???"
date: 2006-02-13
forum: Multimedia &amp; Video
---

### Post by bountonw on 2006-02-13
Read through some of the papers here, I am really new.  Haven't had any sound for 2 weeks, but have been dealing with many other problems, (many still unresolved).  Learning a little everyday, but also overwhelmed with it all.  

I checked the volumn control and it was muted (learned that in a post.)  Undid that and still didn't have sound.

I did lspci -v and got the following. 

> 0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 2a09
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d7dfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>


Tried 
```
lspci -v |grep audio 
```
as some someone suggested.  It only returned me to my prompt.  Do I need to mount this somehow?

Please point me in the right direction or  give me a link.

---

### Post by christhemonkey on 2006-02-13
You need to make sure the module for this card is loaded,
```
lsmod | grep snd
```
and see if it mentions snd-intel8x0 or snd-hda-intel
If not:
```
sudo modprobe snd-intel8x0
```
let me know!

---

### Post by bountonw on 2006-02-13
```
lsmod | grep snd

```
> snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm


```
sudo modprobe snd-intel8x0

```

```
lsmod | grep snd
```

> snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  5 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  3 snd_intel8x0,snd_hda_intel,snd_pcm


---

### Post by bountonw on 2006-02-14
Now what?:-k

---

### Post by christhemonkey on 2006-02-14
Now try going to a terminal typing:
```
alsamixer
```
Press F5 to view all then press m to mute and unmute everything that looks suspicious!
(If it says there is no such command, then you might need to get a package called something like alsautils from synaptic)

---

### Post by bountonw on 2006-02-14
SOUND!!!!  YIPPIE!!!

Thank you, christhemonkey.  I can hear again.  So, nice to have sound after two weeks of silence.  Thank you.

---

### Post by christhemonkey on 2006-02-14
S'aright, anytime!

---

