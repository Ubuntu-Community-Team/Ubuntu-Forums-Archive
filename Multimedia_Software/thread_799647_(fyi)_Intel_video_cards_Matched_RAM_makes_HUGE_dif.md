---
title: "(fyi) Intel video cards: Matched RAM makes HUGE difference."
date: 2008-05-19
forum: Multimedia Software
---

### Post by jdong on 2008-05-19
A few days ago I got a new 2GB stick of RAM because I've got a laptop with 1GB and one with 2GB, and the former is starting to crumble under the weight of my workloads and virtualization.

I figured, why not put 1x2GB and 1x1GB in my primary, the macbook, and leave 1x1GB+1x512MB = 1.5GiB in the other system, which suffices?


Trying it out, immediately I noticed a HUGE speed drop in Compiz performance (GMA950) and video playback smoothness.... Reverting to matched sticks fixed that. My other system with dedicated video RAM didn't suffer from this and currently has unmatched 2.5GB while my macbook has its original 2GB.


So lesson learned: Don't mix and match RAM with Intel GPU chipsets.

---

### Post by eldragon on 2008-05-19
go figure, you just sliced your memory bandwidth in half when you didnt match sticks. since your intel graphics card will use system's ram as its own. you are providing the gpu with half the memory bandwidth, no wonder its slower.


thats what running in 128bit mode is all about.

---

### Post by jdong on 2008-05-19
Well yes, I did expect a slowdown, but I did not expect one to this magnitude from lack of interleaving... I'm talking about it taking 2 seconds to alt-tab to and from Firefox....

---

### Post by mc4man on 2008-05-19
> I did not expect one to this magnitude from lack of interleavingMaybe you had 'mismatched' pair, ie. speed. latency, timings. ect.
this article seems to bear out your orig. expectations
[http://lowendmac.com/musings/07/0525.html](http://lowendmac.com/musings/07/0525.html)

---

### Post by jdong on 2008-05-19
Just played with this again in OS X -- did not perceive any noticeable impact. It seems to be specific to the Linux intel driver....

---

### Post by mnml on 2009-01-31
3d acceleration doesn't work on linux for this driver unless you switch to 16 bit depth.
set:
DefaultDepth 16
in your /etc/X11/xorg.conf file.

---

### Post by jdong on 2009-01-31
Really? I've been running 24-bit all this time with 3D acceleration...

---

### Post by mnml on 2009-01-31
mmh it's probably not the same graphic card I have sorry: 
> Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller

---

