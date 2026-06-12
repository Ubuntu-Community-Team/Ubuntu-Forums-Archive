---
title: "Can't get MIDI to work"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by zerosanity on 2007-08-05
Here's the problem:  I want to compose in Rosegarden and other like programs.  I've configured timidity, and I can get MIDI playback from existing MIDI files, but not from editing progs.  I've tried (unsuccessfully) to install the newest ALSA drivers for my VIA 8237 on-board sound card, but keep getting make errors.

If anyone can help me out, I'd really appreciate it.

Important note:  I've tried the stuff in the sticky on the subject to no avail.  

PLEASE help! Any suggestions are welcome, because I'm REAL stuck.

Thanks in advance,
Zero

---

### Post by dougfractal on 2007-08-05
> to install the newest ALSA drivers
does ubuntu alsa sound not work for you?

have you tried
 [https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)
and
[https://bugs.launchpad.net/ubuntu/+source/rosegarden4/+bug/36801](https://bugs.launchpad.net/ubuntu/+source/rosegarden4/+bug/36801)

if you youv'e got timidity then "timidity -iA -B2,8 -Os1l -s 44100"  to start timidity server.

also go with linux-lowlatency kernel

---

### Post by zerosanity on 2007-08-06
How do I change to the low latency kernel?
Also, I got midi to work somewhat.  I can get midi playback from any program that can output to jack...i run timidity with -iA and -Oj options.  It works pretty well, i spose.  It's definitely better than nothing.

Performance leaves a bit to be desired, though.  It's all a bit laggy.

---

### Post by dougfractal on 2007-08-06
> **zerosanity said:**
> 
Performance leaves a bit to be desired, though.  It's all a bit laggy.

```
sudo apt-get install linux-lowlatency
```

lowlatency could fix this, more strain on a laptop though.

And is timidity setup at boot?

---

### Post by aonegodman on 2007-12-25
Hello - I'm facing the same issues and looking for a work around.

Tried the above timidity thing to activate and got the following response:

-desktop:~$ timidity -iA -B2,8 -Os1l -s 44100
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')

no clues here.

Also Q: installing the low-latency kernal. Is this an additional kernal that you choose during the

GRUB boot menu or does it overwrite the default Ubuntu 7.10 installed currently?

Next, what effect if any will this have on other items or changes in my current kernal?

I can play a ".mid" file in my XMMS player that I d/l off internet. Any thoughts?

---

