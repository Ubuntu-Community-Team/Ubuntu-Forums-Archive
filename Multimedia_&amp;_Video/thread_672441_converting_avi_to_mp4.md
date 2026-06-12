---
title: "converting avi to mp4"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by Seikmann on 2008-01-19
So I have an .avi file that I would like to convert to mp4 (to play on my PS3)
I looked in [this](http://ubuntuforums.org/showthread.php?t=548547) thread. but I did not understand. I have mencoder and I would like to get some help with that program, but if there is other programs that are clearly much better please tell me so, and how to convert avi -> mp4. 

when I tried myself, mencoder told me to look at "-o", but when I looked it wouldn't work.
```
seik@eientei:~$ mencoder /home/seik/Downloads/COMMANDO\ \[DVDRip.XviD-vik13\]\[Napisy\ PL\]/Commando\[1985\]DVDRip\[Eng\]-vik13.avi  mp4
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Exiting... (No output file specified, please see the -o option.)
seik@eientei:~$ mencoder -o
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Error parsing option on the command line: -o

Exiting... (error parsing command line)
seik@eientei:~$ 
```

---

### Post by erginemr on 2008-01-19
Hello,

I didn't use mencoder, but a combination of ffmpeg (text-mode converter like mencoder) and avidemux (as a graphical movide editor/converter) is powerful enough:
[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

Another one is kdenlive:
[http://www.kdenlive.org/index.php](http://www.kdenlive.org/index.php)

---

### Post by gual0s on 2008-02-23
Hi there,

Try this:

```

mencoder original.avi -o new.mp4 -oac copy -ovc lavc -lavcopts vcodec=mpeg1video -of mpeg

```

I have a few avi files which i convert using that command. Worth mentioning that the original avi file:
video: FFMpeg MPEG-4, audio: MPEG-1 Layer 3

Hope it helps.

---

### Post by Greyhair on 2008-02-23
I use DeVeDe which I find a lot easier to use than Avidemux. I regularly convert avi to mpeg-4 for my eldest son; for his PSP. It's also easy to convert avi to ISO images for burning to CD/DVD
To install use synaptic, or if you want the most up-to-date version head over to   [www.getdeb.net](www.getdeb.net)

---

### Post by tango_ninja on 2008-02-23
you could also use something like **winFF** (repo's) or **Fuoco** (available here: [http://fuocotools.byethost13.com/index.php?topic=3.0](http://fuocotools.byethost13.com/index.php?topic=3.0))

---

