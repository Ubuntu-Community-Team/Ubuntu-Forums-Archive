---
title: "[SOLVED] Crackling Sound"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Valpskott on 2008-11-04
I've read threads where people have like a cracking sound now and then interlaced with the normal audio, for me.. I got sound last night, left my computer running overnight, and now, all I get is nothing but cracking sounds, first I tried a reboot, didn't help... so before I did any major surgery, I booted up Vista just to se that it wasn't the amp in my speakers that was at fault, which it wasn't, Vista played sound just fine.


sudo lshw -C multimedia

resulted in

  *-multimedia            
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel



Yeah, and also, I'm using 8.10 (L.L. something)... I'm new to linux, so I won't get offended if you explain things as you do to a 5 year old. :)

---

### Post by Ecclesia on 2008-11-06
I have the same problem.  Try adjusting up PCM from your mixer - which will probably be down all the way.  I found this answer here:

[http://ph.ubuntuforums.com/showthread.php?p=5698003&](http://ph.ubuntuforums.com/showthread.php?p=5698003&)

As soon as you move the pcm slider up a little you should stop hearing the crackling sound.

I'm not sure where the crackling is coming from, although I must admit that I'm quite frustrated with the sound coming from my sound card (integrated nvidia) it ends up making a very quiet, yet obnoxious humming noise when I'm doing something processor heavy, most annoyingly when I'm moving window sliders. I believe it's the fault of the card, though it's hard to test as I don't use windows.  It's had this issue since I got it about a year ago from 7.10 on.

---

### Post by Valpskott on 2008-11-06
> **Ecclesia said:**
> I have the same problem.  Try adjusting up PCM from your mixer - which will probably be down all the way.  

Hah, yes... this solved it. Thank you :)

---

