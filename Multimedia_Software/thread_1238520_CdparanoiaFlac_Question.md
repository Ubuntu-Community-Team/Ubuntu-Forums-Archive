---
title: "Cdparanoia/Flac Question"
date: 2009-08-12
forum: Multimedia Software
---

### Post by nmccrina on 2009-08-12
Hi!
I'm running a very light version of Ubuntu (the command-line install with Fluxbox on top). I didn't want to install sound-juicer and drag in tons of dependencies, so I'm ripping CD's on the command line with Cdparanoia, then encoding them with flac.
I ripped the tracks as the default 16-bit PCM, but flac wants to know some info that I'm not sure of:
1. sign - It wants to know whether the PCM sample is signed or unsigned
2. channels - Number of channels. From looking around, my gut feeling is that the PCM sample has 2, but I didn't find anything conclusive enough to risk an incompatibilty of some sort.

This is how I ripped the tracks:

> -r --output-raw-little-endian
	      Output  headerless  data as raw 16 bit PCM data with interleaved
	      samples in LSB first byte order.


Can a more experienced audiophile suggest what I should put for those two options? :)

---

### Post by mc4man on 2009-08-12
If this is how you wish to rip (cdparanoia only) then output to .wav (the default
check cdparanoia --help for individual or group commands, for all as separate tracks

```
cdparanoia -B
```

If all your ripped tracks are in a folder then at that dir. prompt
```
flac *.wav
```

You would find that rubyripper and or abcde  have very few depends, RR is both gui and cli, abcde is cli based on a configuration file

---

