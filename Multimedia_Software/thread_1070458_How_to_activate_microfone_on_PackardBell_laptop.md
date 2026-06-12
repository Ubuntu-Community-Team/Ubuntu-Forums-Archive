---
title: "How to activate microfone on PackardBell laptop??"
date: 2009-02-15
forum: Multimedia Software
---

### Post by Benzaa on 2009-02-15
Hi,

I've looking for an answer to this question for almost 1/2 a year and I havent found anything that works.

I was wondering if someone could help me or point me towards a solution to this rather annoying thing.

the output from my lspci is:

```

lspci -v
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
	Subsystem: QUANTA Computer Inc Packard Bell A8550 Laptop
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1c00 [size=256]
	I/O ports at 18c0 [size=64]
	Memory at b0040800 (32-bit, non-prefetchable) [size=512]
	Memory at b0040400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

The output from cat /proc/asound/* is:

```

cat /proc/asound/*
cat: /proc/asound/card0: Is a directory
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with Cx20551 at irq 16
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 20: [ 0- 4]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 26: [ 0- 2]: digital audio capture
 27: [ 0- 3]: digital audio capture
 33:        : timer
cat: /proc/asound/ICH6: Is a directory
 0 snd_intel8x0
cat: /proc/asound/oss: Is a directory
00-04: Intel ICH - IEC958 : Intel ICH6 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel ICH6 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel ICH6 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel ICH6 - MIC ADC : capture 1
00-00: Intel ICH : Intel ICH6 : playback 1 : capture 1
cat: /proc/asound/seq: Is a directory
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-1: PCM capture 0-1-1 : SLAVE
P0-2-1: PCM capture 0-2-1 : SLAVE
P0-3-1: PCM capture 0-3-1 : SLAVE
P0-4-0: PCM playback 0-4-0 : SLAVE
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Nov 25 2008 for kernel 2.6.24-22-generic (SMP).

```

I tried changing the model on the /etc/modprobe.d/alsa-base, using:
```

options intel-hda-snd model=XXX

```

And didnt work.

I also checked the alsamixer and all the recording options are seleted. The mic is on and the capture is on as well.

I have re-installed ALSA several times and no luck so far.

Please, any help will be appreciated.

---

### Post by markbuntu on 2009-02-15
There is a listing here for the Packard Bell Easynote

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by Benzaa on 2009-02-16
It didnt work,

I tried that option on my alsa-base file.

The mic is still dead, any other idea??

---

