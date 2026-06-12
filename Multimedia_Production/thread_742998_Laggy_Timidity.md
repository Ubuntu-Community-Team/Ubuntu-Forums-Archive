---
title: "Laggy Timidity"
date: 2008-04-02
forum: Multimedia Production
---

### Post by boomtisk on 2008-04-02
Hi, everyone, yesterday I decided to make another attempt at trying to get my MIDI keyboard working in Linux (using Xubuntu) with strange results.

I followed a howto and lo and behold, I managed to get Rosegarden to connect to my keyboard, although there was a noticable amount of input lag. I then tried a couple of things including installing the low latency kernel and disabling a couple of CPU-heavy features in /etc/timidity/timidity.cfg. 

Eventually, I was proud to discover that I'd managed to get rid of the lag somehow. I was overjoyed and spent all evening jamming on my midi keyboard.

This morning, I felt like jamming some more. I fired up Rosegarden and much to my dismay, **the lag was back**. 

I eventually ended up ditching Xubuntu for Ubuntu Studio which didn't help either, the lag was still there, even some tweaks I've read about didn't help. Does anyone have an idea what could be wrong? This is pretty damn strange.

Here's my /etc/timidity/timidity.cfg

```

# Instrument configuration file for timidity
# $Id: timidity.cfg,v 1.7 2005/09/03 19:26:03 hmh Exp $

# You can change just about every option in TiMidity++ using
# This config file.  Please refer to the timidity.cfg(5) manpage
# for more details

## If you have a slow CPU, uncomment these:
opt EFresamp=d		#disable resampling
opt EFvlpf=d		#disable VLPF
opt EFreverb=d		#disable reverb
opt EFchorus=d		#disable chorus
opt EFdelay=d		#disable delay
opt anti-alias=d	#disable sample anti-aliasing
#opt EWPVSETOZ		#disable all Midi Controls
#opt p32a		#default to 32 voices with auto reduction
#opt s32kHz		#default sample frequency to 32kHz
#opt fast-decay		#fast decay notes

## If you have a moderate CPU, try these:
#opt EFresamp=l
#opt EFreverb=g,42
#opt EFchorus=s
#opt s32kHz
#opt p64a

# Disabling some of the Midi Controls can help with the CPU usage a lot.
# The same goes to the VLPF, sample anti-aliasing and effects such as
# reverb and chorus

# By default, try to use the instrument patches from freepats:

source /etc/timidity/freepats.cfg

```

And here's my /etc/default/timidity file:

```

# Defaults for TiMidity++ scripts
# sourced by /etc/init.d/timidity
# installed at /etc/default/timidity by the maintainer scripts
# $Id: timidity.default,v 1.3 2004/08/07 14:33:26 hmh Exp $

#
# This is a POSIX shell fragment
#

# Enable MIDI sequencer (ALSA), default is enabled
# Disable it if you have real MIDI hardware
TIM_ALSASEQ=true


# Setting overrides (of /etc/timidity.conf) for the ALSA sequencer daemon
TIM_ALSASEQPARAMS="--no-anti-alias -Os11 -B 99"

```

My computer specs: Athlon 2600+ XP, 768 megs of RAM, SB Live! sound card (the one with the MIDI port at the back.)

Other than my changes to the above config files, my Ubuntu Studio Gutsy install is vanilla with the latest updates. 

Any help would be very much appreciated, thanks a lot in advance.

---

### Post by Hyporeal on 2008-05-22
I would say the problem is in /etc/default/timidity. Try changing the -B 99 parameter to -B2,8. That worked for me.

---

