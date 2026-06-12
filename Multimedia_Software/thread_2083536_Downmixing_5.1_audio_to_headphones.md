---
title: "Downmixing 5.1 audio to headphones"
date: 2012-11-12
forum: Multimedia Software
---

### Post by isbura on 2012-11-12
After a long struggle battling to get Ubuntu to work with my sound setup I'm almost there. I've got 5.1 working, but the problem is now when I plug in my headphones I seem to get strange output.

Playing a 5.1-encoded video works fine without headphones. When I try to listen with headphones I get an odd situation where I get full stereo but it only seems to consist of certain elements of the original audio, namely the background music. All dialogue is missing.

I've tried several files in both VLC and Totem and the result is the same. I'm guessing it's because the dialogue track is being output to the centre speaker/subwoofer and my headphones are only playing back the front L/R audio channels. The files in question sound great without headphones, and sound fine with or without headphones when I play them in Windows.

On Windows all this gets automatically downsampled to stereo whenever I plug my headphones into either the front audio jack on my PC or the headphone jack on my speaker system. The sound driver detects the headphones being inserted and reconfigures the sound to be mixed to stereo. I'm sure Linux has an option to do the same somewhere, but I just can't figure out how.

lspci:

```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: Giga-byte Technology Device a002
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 47
	Region 0: Memory at fbff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
```

edit: Actually 12.10 and not 10.04 like my user info says, but the site won't let me update it.

edit2: After plugging headphones in to either my speaker system or my PC's front audio jack, running the Sound Test from the Sound Settings dialog gives me silence in all outputs except Front Left/Right, confirming what I suspected above. I've been through the Ubuntu sound settings, pavucontrol, alsamixer, gnome-alsamixer and still can't find a downmix option.

---

