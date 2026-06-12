---
title: "Using TiMidity under Rosegarden"
date: 2009-06-13
forum: Multimedia Software
---

### Post by ilantal on 2009-06-13
I received some very useful help from this forum, and now I am trying to take the next step.
What already works is Rosegarden + QSynth. I had to load a soundfont into QSynth in order to hear something, so I guess I have to do something similar with TiMidity. Thus I added the last line:
> 
# Instrument configuration file for timidity
# $Id: timidity.cfg,v 1.7 2005/09/03 19:26:03 hmh Exp $

# You can change just about every option in TiMidity++ using
# This config file.  Please refer to the timidity.cfg(5) manpage
# for more details

## If you have a slow CPU, uncomment these:
#opt EFresamp=d		#disable resampling
#opt EFvlpf=d		#disable VLPF
#opt EFreverb=d		#disable reverb
#opt EFchorus=d		#disable chorus
#opt EFdelay=d		#disable delay
#opt anti-alias=d	#disable sample anti-aliasing
#opt EWPVSETOZ		#disable all Midi Controls
#opt p32a		#default to 32 voices with auto reduction
#opt s32kHz		#default sample frequency to 32kHz
#opt fast-decay		#fast decay notes

## If you have a moderate CPU, try these:
opt EFresamp=l
opt EFreverb=g,42
opt EFchorus=s
opt s32kHz
opt p64a

# Disabling some of the Midi Controls can help with the CPU usage a lot.
# The same goes to the VLPF, sample anti-aliasing and effects such as
# reverb and chorus

# Include a configuration for the selected patchset or soundfont
# By default, try to use the instrument patches from freepats:

source /etc/timidity/freepats.cfg
soundfont /home/ilan/rosegarden/mustheory2.sf2

I also uncommented the options for a moderate CPU. Still there is no sound from TiMidity and if I want to hear something I need to add QSynth.

Can anyone tell me what I'm missing and/or doing wrong? I'll include a Pathage diagram of my setup. For test purposes I'm using the Rosegarden sample Sonata in C.

---

