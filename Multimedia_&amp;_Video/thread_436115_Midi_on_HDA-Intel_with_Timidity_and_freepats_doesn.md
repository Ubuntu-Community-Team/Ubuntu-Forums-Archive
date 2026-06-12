---
title: "Midi on HDA-Intel with Timidity and freepats doesn't work"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by temcat on 2007-05-07
Hi, I'm trying to get midi (with vkeybd) working to no avail. I have timidity and freepats installed.

Here's my /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq

Here's my /etc/default/timidity

# Defaults for TiMidity++ scripts 
# sourced by /etc/init.d/timidity
# installed at /etc/default/timidity by the maintainer scripts
# $Id: timidity.default,v 1.3 2004/08/07 14:33:26 hmh Exp $

#
# This is a POSIX shell fragment
#

# Enable MIDI sequencer (ALSA), default is disabled
TIM_ALSASEQ=true

# Setting overrides (of /etc/timidity.conf) for the ALSA sequencer daemon
TIM_ALSASEQPARAMS="-B2,8 -Os"

When I try to launch timidity I get this:

temcat@eden:~$ timidity -iA -B2,8 -Os
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')

Output from amidi -l is empty:

temcat@eden:~$ amidi -l
Dir Device    Name

VkeyBd produces no sound. What am I dong wrong?

---

