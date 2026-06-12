---
title: "Problems with Xruns in Jack"
date: 2007-11-05
forum: Multimedia Production
---

### Post by aNonEMooseCowHerd on 2007-11-05
Hi all,
I am drooling over the 1 and 2 ms latencies people are getting with Ubuntu Studio, so I am desperate to get get Jack + Ardour up and running.

Ardour runs fine, but Jack is giving me huge problems.  I get Constant Xruns, weather I set it to 64 or 1024 frames/buffer.
I have the realtime kernel running (that is what I choose from the boot menu.  
I am trying to use my 1.68ghz Core Duo laptop internal sound card.  (for now... I have an FCA-202 Firewire interface, but I want to take this one step at a time.)

Is there something obvious that I'm missing.  Some settings to check??

Thanks!!
{A}

---

### Post by aNonEMooseCowHerd on 2007-11-07
I decided to install Ubuntu Studio from the 7.10 DVD instead of the "Upgrade" from Gusty 7.10, and after some tweaking of the Jack settings, everything works like a charm.

If you can swing it, I recommend installing from scratch using the Ubuntu Studio DVD.  It saved me tons of headaches.

{A}

---

### Post by lapcat66 on 2007-11-08
I'm going to second that advice.  A clean install of Gutsy followed by adding Ubuntu Studio from Synaptic led to endless xruns and other sound issues on my x60.  

I was resigned to rollback to Feisty, when I decided to do a clean install of Ubuntu Studio 7.10 from dvd instead.  Now the jack-enabled apps I normally use all work without issue (Qsynth, Rosegarden (had to add flac), Ardour, Hydrogen, ZynAddSubFX, and even Audacity).  I haven't seen an xrun yet.

The only downside was that it took a while in Synaptic to add the 'standard' non-studio apps I use.  But I'm ecstatic!  Big thanks to the all the developers.

---

### Post by motin on 2008-06-25
I have no oppurtunity to do a clean install or roll back from Hardy, but am experiencing the same issue. Any time I try starting jackd with alsa I get constant xruns, seamingly regardless of parameters used. 

Any ideas of what may causing this?

Thanks

---

