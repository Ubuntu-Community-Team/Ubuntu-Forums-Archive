---
title: "Upgrade to Gutsy lost sound, custom kernel won't let me get it back"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by fowie on 2007-12-29
I've seen some other posts about sound being lost in the upgrade to gutsy and the issue being resolved by installing a linux-ubuntu-modules or something-like-that package.  My problem is that I had to recompile my kernel to get my it8212 RAID driver to work properly, so the '-generic' package doesn't really work for me.  Any ideas how to get my sound working?  I've tried following the howto's all over the place.  

lspci -vvnn shows:
```

00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
	Subsystem: AOPEN Inc. Unknown device [a0a0:060b]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express Unknown type IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled CommClk- ExtSynch-
		Link: Speed unknown, Width x0
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Unknown (5)

```

and lshw -class sound shows:
```

  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

my alsa module is snd-intel8x0 according to alsa's website, but even after a 
```

modprobe snd-intel8x0

```
my sound isn't working and lsmod shows:
```

snd_intel8x0           36124  0 
snd_ac97_codec        101924  1 snd_intel8x0
ac97_bus                3456  1 snd_ac97_codec
snd_pcm_oss            53504  0 
snd_mixer_oss          18304  1 snd_pcm_oss
snd_pcm                88580  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
snd_seq_dummy           4996  0 
snd_seq_oss            35712  0 
snd_seq_midi            9728  0 
snd_rawmidi            25856  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                58480  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25988  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63628  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_page_alloc,snd_seq_oss,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               8928  1 snd
...

```

Help?

---

