---
title: "high CPU usage when JACK and qjackctl running"
date: 2009-07-21
forum: Multimedia Software
---

### Post by ltwelve2 on 2009-07-21
When I run JACK with the command line, top measures reasonable CPU usage for the jackd process, something like 3%-5%.  When I run it with qjackctl, both qjackctl and JACK show usage in the 15%-20% range.  Together, they soak up a third or more of my processor cycles and create all kinds of havoc.  Any idea why this is?  I've tried both dummy and alsa drivers with and without running qjackctl, with the same sample rate and number of frames, and when the GUI is running, both processes go crazy.  
 
I'm running Ubuntu Studio 9.04, installed and updated just a couple of days ago with the realtime kernel and all that good stuff.  Realtime priorities and memlock have been set appropriately, I believe (or at least they are the same whether I'm running qjackctl or not).

---

### Post by igorzwx on 2009-07-21
Do you have pulseaudio?

Open task manager and see which processes consume CPU

---

### Post by igorzwx on 2009-07-21
more exactly, if you have pulse, everything may happen.
I was not able to understand what happens with CPU when I run Audacity.

---

### Post by ltwelve2 on 2009-07-21
I've been using the "top" utility in a terminal window to see what's using CPU cycles.  The only significant contributors are jackd and qjackctl.  I don't know if I have pulseaudio or not, but I'll check.  It doesn't show up on the list of running processes, though.  
 
Does the task manager measure things differently than "top"?  Maybe I'm using the wrong diagnostic tool!

---

### Post by igorzwx on 2009-07-21
If you do not know, you have.
See pulse, and pulseaudio in synaptic.
It is a kind of evil.
It very possible that CPU might be consumed by pulse,
but in the task manager you may see that it is consumed by a GUI.

You kill pulse, start Audacity.
And pulse is runnig again.
You kill pulse once more.
Start playback in Audacity,
and pulse is already runnig again.

---

