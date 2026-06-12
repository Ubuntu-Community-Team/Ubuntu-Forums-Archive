---
title: "No other program is blocking the souncard"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by mohdridha on 2007-01-02
Ok i got a problem...

First i'm watching one video at youtube.com and all things going well. After a while, i want to hear some music on XMMS. But when i try to play a song, this is the error message i got:

```

Please check that:

Your soundcard is configured properly
You have the correct plugin selected
No other program is blocking the souncard

```

I think i got no problem with the first two options.. 

Another case:
i play XMMS first, then try to play a video on youtube. This time, no error message displayed, but there is no sound played for the video.
 
I'm wondering whether we can or cant use the soundcard for two different programs at the same time.. As for my example: one is for youtube.com (web browser) and the other for xmms..

If can, How to solve it?

Thanks

---

### Post by Lord Illidan on 2007-01-02
What soundcard do you have?

Also try killing esd in Gnome or artsd in KDE.

killall esd or killall artsd in a terminal will do the trick.

---

### Post by mohdridha on 2007-01-02
Its a built-in soundcard..
When i was using Windows, the soundcard detected as Avance '97..

and from lspci -v:
```

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Micro-Star International Co., Ltd.: Unknown device 5850
        Flags: bus master, medium devsel, latency 64, IRQ 201
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=128]
        Capabilities: [48] Power Management version 2

```

and killall esd wont solve the problem

```

kapla@mrn:~$ killall esd
esd: no process killed
kapla@mrn:~$ esd
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave

``` (also tried with sudo command)

---

### Post by happysmileman on 2007-01-02
For some reason Firefox seems to do that for me, so it's possible it does it for you aswell... I just close firefox, open xmms, and restart firefox...

---

### Post by mohdridha on 2007-01-02
[quote=happysmileman]
For some reason Firefox seems to do that for me, so it's possible it does it for you aswell... I just close firefox, open xmms, and restart firefox...
[/quote]

Is that the only way?

---

### Post by arnicainthemembrane on 2008-01-02
I have an identical problem.

How does one simply

1. Figure out what program is using the soundcard

2. Cause that program to stop using the soundcard so another program can use it?

---

### Post by Yellow Pasque on 2008-01-02
I don't recommend doing this until you've exhausted other options, but you may want to give OSSv4 a try (see link in my sig for details). It uses a virtual mixer, which can play simultaneous sound sources.

---

### Post by arnicainthemembrane on 2008-01-02
No, I'm looking for what must be a basic function, that is, simply, how to make the hardware work.

---

