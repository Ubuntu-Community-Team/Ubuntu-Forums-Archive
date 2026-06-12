---
title: "Timidity: how to get a soundfont working next to freepats?"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by DaVince21 on 2007-10-08
I have TiMidity++ installed together with the freepats patch set and everything set up as a sound server so I can enjoy my MIDI music in any game or application. However, the freepats patch set is missing a few instruments, so Timidity++ won't play those. Because of this some MIDIs sound weird, sometimes entire parts of the song missing.

I downloaded a GM soundfont from Hammersound which I wanted to use to "fill up" any missing instruments. From what I read in other sources I only have to add this line to my timidity.cfg file:
```
soundfont /sourcedirectory/soundfontfile.sf2
```
I did this (with the correct path, of course). It didn't work, nothing happened. Missing instruments are still missing.

How do I solve this problem? Am I doing something wrong?
(And yes, I AM picking the correct timidity.cfg file, because if I do something wrong in that file Timidity++ complains!)

---

### Post by DaVince21 on 2007-10-17
No one?

---

### Post by alainhenry on 2007-11-10
I am checking my config file  for timidity which reads
```
soundfont /home/alain/soundfonts/Unison.sf2
```
It's the only uncommented line in /etc/timidity/timidity.cfg.  And it's the same as yours. Could it be your soundfont that is not complete ?  

I am now using a somewhat more complex setting, based on FluidR3, which I found on 
[http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_category&category=Collections&ListStart=15&ListLength=15]("http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_category&category=Collections&ListStart=15&ListLength=15")
(Fluid release 3). Let me know if you want more details (I am not checking this forum on a daily basis). I am now using Gutsy with the same setting, an it works fine, except that the music volume is much lower, but only for MIDI. I still have to investigate this. 

Alain

---

### Post by Pettman on 2007-11-26
> **alainhenry said:**
>  except that the music volume is much lower, but only for MIDI. I still have to investigate this.Try adding "opt A 300" in your /etc/timidity/timidity.cfg file, it will increase volume by 300%.

---

### Post by DaVince21 on 2007-11-28
Eh, I use QSynth now (graphical frontend to fluidsynth). Uses much less CPU, lends itself much better as a MIDI server (less lag) and it accepted my soundfont just fine. :)

---

