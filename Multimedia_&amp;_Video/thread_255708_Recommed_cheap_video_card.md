---
title: "Recommed cheap video card?"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by smilinggoat on 2006-09-11
Hey all, I'm looking for a video card compatible with Ubuntu for my x86 box with the following requirements:

-Fanless
-TV out
-Good enough to play emulated console games up to N64

It doesn't need to be able to play FPS games or anything.  It's really just for watching XViD,etc and playing the occasional console game.

And oh yeah, cheap!

Any ideas?

Thanks!

---

### Post by Malta paul on 2006-09-12
I am using a GeForce 6600 256MB DDR card with good results with both a CRT and a LCD Monitor, I downloaded update Niva drivers using Ubuntu and it works OK.
But it dose have a small fan!

---

### Post by Hairyred on 2006-09-13
I have an nVidia 7300gs,with 128mb ram onboard, seems to do the job. Had to install driver update, cheap and good.

---

### Post by Rhubarb on 2006-09-13
Any of the cheapest nVidia cards should do the trick.
I had a 128Mb 5200 (no fan), cheap as chips, and it'll also handle Xgl + Compiz.
If you've got a computer market near by, go to one of those - you can buy some dirt cheap stuff there, including 2nd hand stuff.
nVidia drivers are easy to install:
```
sudo apt-get install nvidia-glx
```

... And you might have to change a line in your /etc/xorg.conf
In devices, change 'nv' to 'nvidia', that should do the trick.
Check the forums here if you need anymore help.

---

