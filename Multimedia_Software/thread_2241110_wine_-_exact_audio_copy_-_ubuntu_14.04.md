---
title: "wine - exact audio copy - ubuntu 14.04"
date: 2014-08-24
forum: Multimedia Software
---

### Post by spacemen12 on 2014-08-24
Hi,
   I have to rip a large collection of cd (~1000). My understanding is that exact audio copy is the fastest, please tell me if there are better options.

   I've tried to install it on my ubuntu 14.04 (64 bits) through wine. The installation was straightforward and no problem. BUT, when I start it I have the following error message:
"Unhandled exception
at 0218ADF0 -> access violation."

The program does not start, but freeze there:
"Exact Audio Copy is starting up...
Please wait!"
And it stay like that forever.

When I press ok on the Unhandled exception, EAC stop starting up.

How do I solve that?

---

### Post by speartip on 2014-08-25
EAC is not fast by any means. It's main concern is accuracy & quality.
If you want speed & a reasonable rip, I would use a native ripper like asunder. Its in the repos.
If quality is what your after, I have found EAC difficult to set up in linux. However there is an app called morituri which is a command line program that seems to rip to high quality audio, but it takes longer.

---

### Post by spacemen12 on 2014-08-25
Thanks for the reply. 

I am wondering what is the state of the art to get a "audiophile quality" (e.g. FLAC) rip at the best speed. I have to rip my collection ~800cd in a short time frame.

I was thinking of EAC, but maybe I am wrong.

---

### Post by speartip on 2014-08-25
What I would do is rip a CD using asunder at 320kbps or FLAC if you have the space.
I have tried all kinds of rippers & cannot honestly tell the differnce in audio quality.
Someone may contradict me, but I think asunder should cover your needs.
You can change the quality of the rip in preferences/encode.

---

### Post by shantiq on 2014-08-27
spaceman    i did a small    howto   a while back for[ EAC   ]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385")

should rectify your 

> [COLOR=#000000]"Unhandled exception[/COLOR]
[COLOR=#000000]at 0218ADF0 -> access violation."[/COLOR]



problem there

---

### Post by andrew.46 on 2014-10-10
> **speartip said:**
> If you want speed & a reasonable rip, I would use a native ripper like asunder.

As the use for audio cd rippers slowly dies it is nice to see a quality application like asunder!! But audio cds are becoming increasingly obsolete as the age of digital / Internet song and album transfer is upon us...

---

### Post by Rob Sayer on 2014-10-11
EAC is, as mentioned, not designed for speed but accuracy.  It's good at detecting bad sectors and rereading them, which may or may not work.

Before trying anything in WINE look at the user ratings, which are pretty comprehensive.  Anything under a gold rating isn't generally worth bothering with.  EAC is rated silver.

Incidentally, optical drives are so slow compared to everything else in your computer that it wouldn't matter that much how fast the software was, assuming there is a big difference among programs, which there isn't.

I've ripped a lot of CDs and DVDs in the past with 2 laptops.  One is a single core, the other has an i3.  The latter machine is 3 or 4X faster.  Ripping DVDs took almost exactly the same time on both.

---

