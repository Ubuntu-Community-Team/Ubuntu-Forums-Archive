---
title: "Weird Timidity problem (Bad sound)"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by WHiZZi on 2007-07-16
Hi, 

I recently installed Timidity on my brand new Dell Latitude D830 laptop. I have several MIDI-files which I need to play and edit.

So, I thought to install Timidity on the laptop, because it doesn't have a nice hardware midi chip. I even installed the low-latency kernel.

Playing a random midi with
timidity file.mid
Plays the midi without any problems (even with the eawpatches)

But when I start timidity as a daemon (using [this]("https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo") howto) and even disabled all midi-effects in timidity.cfg, I cannot play decently using pmidi and rosegarden (the program I like to work with).

When Rosegarden plays the midi (using Timidity as daemon) it sounds like the CPU cannot handle the samples (or something). The sound is very bad.

Again, when using timidity without the daemon option, it works flawelessly.

The CPU cannot be the problem, it's a Intel Core2Duo T7300 at 2GHz and I'm having 2GB of RAM.

My timidity.cfg looks like this:
```

# Instrument configuration file for timidity
# $Id: timidity.cfg,v 1.7 2005/09/03 19:26:03 hmh Exp $

# You can change just about every option in TiMidity++ using
# This config file.  Please refer to the timidity.cfg(5) manpage
# for more details

## If you have a slow CPU, uncomment these:
opt EFresamp=d          #disable resampling
opt EFvlpf=d            #disable VLPF
opt EFreverb=d          #disable reverb
opt EFchorus=d          #disable chorus
opt EFdelay=d           #disable delay
opt --no-anti-alias     #disable sample anti-aliasing
opt EWPVSETOZ           #disable all Midi Controls
opt p32a                #default to 32 voices with auto reduction
opt s32kHz              #default sample frequency to 32kHz
opt fast-decay          #fast decay notes

## If you have a moderate CPU, try these:
#opt EFresamp=l
#opt EFreverb=g,42
#opt EFchorus=s
#opt s32kHz
#opt p64a


#opt EFresamp=l          #use linear resampling
#opt EFvlpf=d            #disable VLPF
#opt EFreverb=d          #disable reverb
#opt EFchorus=d          #disable chorus
#opt EFdelay=d           #disable delay


# Disabling some of the Midi Controls can help with the CPU usage a lot.
# The same goes to the VLPF, sample anti-aliasing and effects such as
# reverb and chorus

# By default, try to use the instrument patches from freepats:

source /etc/timidity/eawpatches.cfg

```

I also tried Qsynth, but that doesn't produce any sound at all. I have a running Feisty with all updates..
Can someone give me a clue what I can do about this problem?

---

### Post by WHiZZi on 2007-07-16
ok. I think I solved it.

I enabled all items in the timidity.cfg file and then changed the /etc/defauilt/timidity to
```

# Enable MIDI sequencer (ALSA), default is disabled
TIM_ALSASEQ=true

# Setting overrides (of /etc/timidity.conf) for the ALSA sequencer daemon
TIM_ALSASEQPARAMS="--no-anti-alias -Os11 -B 99"

```

IT seems that the buffer (-B ) option really makes a difference. I changed it to 99 and now most of the MIDI's play without problems..:guitar:

---

### Post by aonegodman on 2007-12-26
Tried to edit timidity.cfg using gedit but was told I don't have permission?

Also, where and how did you make the change to the /ect/default/timidity you mention? ](*,)

---

