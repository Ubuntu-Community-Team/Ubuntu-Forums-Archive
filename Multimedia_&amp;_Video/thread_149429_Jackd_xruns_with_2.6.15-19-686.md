---
title: "Jackd xruns with 2.6.15-19-686"
date: 2006-03-23
forum: Multimedia &amp; Video
---

### Post by bwanab on 2006-03-23
A couple of days ago a new kernel was available for dapper. I got it, but when I boot into it (2.6.15-19-686), jackd reports around 10 xruns per second - and this is with no applications running audio or otherwise. I can boot back into 2.6.16-18-686 and it still works fine. No xruns except occasionally (except playing with zynaddsubfx of course).

Any ideas what might be the problem?

---

### Post by dolson on 2006-03-23
That is strange... I don't have the same behaviour here.

Did you try using the -686 or -K7 or whathaveyou for your system, other than the -386? It might make a difference, but it doesn't make a lot of sense to me..

If it doesn't subside with the -20- release, which is bound to happen shortly, I'd imagine, then you might want to open a support ticket or even a bug report if someone else can reproduce it.

As a side note, I am going to work as hard as I can (hopefully with some help from Forest and Maarten) to provide a pre-built -rt kernel after Dapper's launch. Right now the kernel changes WAY too often to keep up. The -rt kernel is much much much better for audio work.

---

### Post by bwanab on 2006-04-08
Now that 2.6.15-20-686 is out, I tried this again - no luck. I found that if I increase the number of periods to 3 that the xruns on startup don't happen. Thus, I'm using:

/usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p512 -n3

I was able to bring up qsynth and attached vkeybd and play some notes no problem. But, when I lauched jack rack and loaded a rack with a couple of the CAPS amp/cabinet simulation plugins, all hell broke loose. Even with a buffersize of 2048 and 4 periods (-p2048 -n4), loading the rack caused way too many hard xruns.

On 2.6.15-18-686, I'm running jack with:

/usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p512 -n2

with no problems at all.

I'm trying to think of What could have regressed in the newer kernel builds that would explain this behaviour?

---

### Post by dolson on 2006-04-08
If anyone can reproduce this, I think it needs to be opened up as a bug ASAP. That is a pretty high period, even with a non-rt kernel, IMHO.

---

