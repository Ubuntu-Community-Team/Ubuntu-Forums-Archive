---
title: "Midi doesn't work (/etc/timidity/timidity.cfg: No such file or directory)"
date: 2016-01-14
forum: Multimedia Software
---

### Post by Dingbats on 2016-01-14
I'm trying to get midi to work, running Ubuntu 14.04.  I have installed Timidity for playing midi files.  However, when running

```
timidity file.mid
```

or (as I have seen suggested)

```
timidity -iA file.mid
```

all I get is this:

```
/etc/timidity/timidity.cfg: No such file or directory
timidity: Error reading configuration file.
Please check /etc/timidity/timidity.cfg
```

Googling this error message turns up a lot of similar examples, but where the problem apparently has been that Freepats was not installed.  I do however have Freepats installed, and it's the latest version.  The file etc/timidity/timidity.cfg indeed does not exist.  sudo doesn't solve anything.

I'm completely clueless.  What might the source of the problem be?

---

### Post by Dennis N on 2016-01-14
Here is the configuration file on my computer. The only caution might be the version of timidity - mine is 2.13.2-40build2 which is running in Ubuntu 12.04. But, won't hurt to try using it in that location. If you are using freepats, then you need to comment out my source lines, and uncomment the source line for freepats just above that section.

```

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
#opt EFresamp=l
#opt EFreverb=g,42
#opt EFchorus=s
#opt s32kHz
#opt p64a

# Disabling some of the Midi Controls can help with the CPU usage a lot.
# The same goes to the VLPF, sample anti-aliasing and effects such as
# reverb and chorus

# By default, try to use the instrument patches from freepats:
#source /etc/timidity/freepats.cfg

# alternatively, you can use the fluid-soundfont:
source /etc/timidity/fluidr3_gm.cfg
source /etc/timidity/fluidr3_gs.cfg

```

Comment 1: You will get a lot better sound by using the fluid-soundfont which is in the repositories.
Comment 2: Audacious player will also handle midi, and allow you to have a playlist, but you have to set up the appropriate plugin.

---

### Post by Dingbats on 2016-01-14
Thank you! :)  How simple, now it works fine!

---

### Post by Dennis N on 2016-01-14
No problem. Glad to help. You can mark your thread as 'Solved' by using the thread tools at the top of your first post.

---

