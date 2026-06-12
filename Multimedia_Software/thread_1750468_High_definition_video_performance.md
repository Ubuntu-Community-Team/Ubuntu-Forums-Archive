---
title: "High definition video performance"
date: 2011-05-05
forum: Multimedia Software
---

### Post by RaYWoLF on 2011-05-05
I have installed ubuntu 11.04 on my computer. I have also instaled xbmc media center to see my movies. I have tried to play an HD movie (MKV with x264) and it doesn't go as smooth as it does in Windows (with Core AVC codec).

Following the information found in may forums, I tried to install:
- x264 package
- Ubuntu restricted extras
- w32codec package (from medibuntu)
- non-free codecs (from medibuntu)

After doing that, I tried it but nothing changed. I rebooted the machine with the same result. I don't know if it uses the new codecs or not. Is there any way to see what codec uses xbmc to reproduce a movie?

Any idea to solve the problem?

---

### Post by RaYWoLF on 2011-05-05
Additional information:
- Processor: Intel(R) Core(TM)2 CPU 6300 @ 1.86GHz
- Memory: 1 Gb
- Graphic card: NVIDIA GeForce 7300 LE (512.0 Mb)

The CPU load with XBMC menu is about 70% in both cores. When I run the movie it's about 50-60%. I don't know why it takes so many CPU doing "nothing" and doesn't use all the CPU to run the movie...

---

### Post by beew on 2011-05-05
Try a different player than XBMC. I tested in on a few machines and find its performance always inferior to mplayer and VLC except in machines with Nvidia cards where it uses VDPAU (not yours, your card is too old and it doesn't support VDPAU)

Try get mplayer from this ppa and see if it helps. You can use coreavc with this one, but it may actually work better without because it needs dshowserver to run coreavc and it may consume a bit of cpu cycles.

[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

---

### Post by RaYWoLF on 2011-05-05
I have tried to install ffmpeg package and it seem to be much better. Now I can see a 720p movie very smooth. The only problem to be perfect is that sometimes there are horizontal lines on the screen (they were there before install ffmpeg). I also have a problem with the sound (rear speakers doesn't sound during the film), but that's another history :)

I want to use xbmc because I use it on my living room computer, the remote works great with it and my parents are familiar with it (is "similar" to media portal, the one which they use on Windows).

---

