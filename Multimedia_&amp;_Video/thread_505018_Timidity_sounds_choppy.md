---
title: "Timidity sounds choppy"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by jaywhy13 on 2007-07-19
I've tried quite a bit of stuff.... 
First nothing was uncommented in my /etc/timidity/timidity.cfg
Now it looks like this
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
opt anti-alias=d        #disable sample anti-aliasing
opt EWPVSETOZ           #disable all Midi Controls
opt p32a                #default to 32 voices with auto reduction
opt s32kHz              #default sample frequency to 32kHz
opt fast-decay          #fast decay notes

## If you have a moderate CPU, try these:
opt EFresamp=l
opt EFreverb=g,42
opt EFchorus=s
opt s32kHz
opt p64a

# Disabling some of the Midi Controls can help with the CPU usage a lot.
# The same goes to the VLPF, sample anti-aliasing and effects such as
# reverb and chorus

# By default, try to use the instrument patches from freepats:

source /etc/timidity/freepats.cfg


I also tried the nice level fix thing to add to the started to supposedly increase the priority of timidity when it starts....
START="--nicelevel -5 --start --quiet --exec ${DAEMON} --pidfile ${PIDFILE} -- ${PARAMS}"

However sound is STILL choppy.
I haven't installed any patches or anything like that... Please help.

I start timidity manually like so:
timidity -iA -B2,8 -Os1l -s 44100 &

I'm using a program under wine .... Guitar Pro and this other app.. both of them experience the same problems.... I've also tried reducing the sample rate using -s 22000.. that doesn't work either... 

Please help

---

### Post by fredj on 2007-07-19
What is your computer and what sound card are you using? Choppy sound is usually caused by lack of cpu
power or a high latency soundcard.
Sound works best on Ubuntu when you install the realtime kernel and run everything through the jackd
audio server.

---

### Post by Artemis3 on 2007-07-23
> **jaywhy13 said:**
> I've tried quite a bit of stuff.... 
First nothing was uncommented in my /etc/timidity/timidity.cfg
Now it looks like this

## If you have a slow CPU, uncomment these:
opt EFresamp=d          #disable resampling
opt EFvlpf=d            #disable VLPF
opt EFreverb=d          #disable reverb
opt EFchorus=d          #disable chorus
opt EFdelay=d           #disable delay
opt anti-alias=d        #disable sample anti-aliasing
opt EWPVSETOZ           #disable all Midi Controls
opt p32a                #default to 32 voices with auto reduction
opt s32kHz              #default sample frequency to 32kHz
opt fast-decay          #fast decay notes

## If you have a moderate CPU, try these:
opt EFresamp=l
opt EFreverb=g,42
opt EFchorus=s
opt s32kHz
opt p64a

# Disabling some of the Midi Controls can help with the CPU usage a lot.
# The same goes to the VLPF, sample anti-aliasing and effects such as
# reverb and chorus

# By default, try to use the instrument patches from freepats:

source /etc/timidity/freepats.cfg


This doesn't look right. **Don't uncomment all!**

My system is an old Duron 1300 with 1gig of ram. The only line i have uncommented is:
opt EFresamp=l

And nothing else. Midi playback takes around 60% without any dropouts unless i start browsing many sites, etc.

I can also use other .sf2 fonts just fine, even those with 300mb worth of sample data ;)

I'm also using the lowlatency kernel but nothing else.

---

### Post by novosirj on 2007-10-02
On my machine, the -B2,8 causes the problem. -B3,8 works fine -- you probably don't need the nice level.

My machine is a Core 2 Duo at 2.0GHz.

---

