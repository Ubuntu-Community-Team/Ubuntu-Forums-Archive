---
title: "[SOLVED] Alsa: no mixing, need help with asound.conf"
date: 2009-01-02
forum: Multimedia Software
---

### Post by BatPenguin on 2009-01-02
Hello all,

I've spent the better part of two days now fighting against my Ibex installation and it's sound issues. I would really appreciate some help in getting my Alsa to do either hardware or software mixing. I don't care how it's done as long as many applications can play at the same time :)

I would imagine that I have the required alsa and gstreamer things installed, but if this sounds like an issue with something like that, please let me know and I'll check what's installed. THis is all on Intrepid. The same machine had Hardy with occasional sound problems (this chip isn't the greatest supported thing), but everything pretty much finally went to hell after an upgrade to Intrepid a few days ago. First sound just disappered, then I decided to "get this pulseaudio thing working once and for all", then reality hit after I could get it done after trying pretty much everything, so finally I removed pulseaudio (I know not supposed to do it, but seemed like the only option), dabbled with Esound (doens't work in all programs, not usable to me, although it DID mix sounds), and now I'm back to trying to salvage a working ALSA configuration. Also plays sounds fine now, but no mixing. Mixing is important to me, I often have Skype etc. on so I need to hear sounds from multiple applications. Besides, it's not 1988 anymore, multiple sounds should not be difficult to get...

I have a feeling that this should be a simple enough basic ALSA stuff to use either hardware mixing or dmix, I suppose, but I just do not know how to do it. I'm not a newbie in Linux, but sound issues have always been very difficult for me to deal with for some reason.

I'll list up a lot of information here now in the hope that sometbody could give me a hand in crafting a /etc/asound.conf or ~/.asoundrc that would give me mixed sounds.

I do not wish to sound ungrateful to any advice, but please do not suggest going back to Pulseaudio. I followed every guide and trick under the sun for 2 days, and it did not work. I can give it another shot if I get mixed ALSA sounds working now and it looks like that configuration is just a matter of backing up a few files. But for now, I think I just need somebody who understands the alsa configuration files to tell me what to put there to use some kind of mixing of sounds. When and if Alsa works perfectly, I'll entertain going back to Pulse when I have a weekend to waste. Thanks!

And the files:

/etc/asound.conf:

(This quite simply dumps everything into the SPFID output, that's what I want. My guess is that this file needs to say "dump everything into mixer X and then mixer X -> SPDIF. How this can be done is totally beyond me even after surfing Ubuntu and alsa forums enough to make my eyes bleed. Coming up with this working non-mixed setup was a surf-fest of several hours to begin with)

```
pcm.!default {
  type plug
  slave {
    pcm "spdif"
    rate 48000
    format S16_LE
  }
}

```

I have no ~/.asoundrc and ~/.asoundrc.asoundconf files at the moment. Here's the relevant output of sudo lspci -vv:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: ABIT Computer Corp. Device 1082
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

..and here's aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

amd aplay -L:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
risto@Galactica: 535/etc$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=U0x46d0x990,DEV=0
    USB Device 0x46d:0x990, USB Audio
    Front speakers
surround40:CARD=U0x46d0x990,DEV=0
    USB Device 0x46d:0x990, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=U0x46d0x990,DEV=0
    USB Device 0x46d:0x990, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=U0x46d0x990,DEV=0
    USB Device 0x46d:0x990, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=U0x46d0x990,DEV=0
    USB Device 0x46d:0x990, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=U0x46d0x990,DEV=0
    USB Device 0x46d:0x990, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=U0x46d0x990,DEV=0
    USB Device 0x46d:0x990, USB Audio
    IEC958 (S/PDIF) Digital Audio Output

```


My /etc/modprobe.d/alsabase includes "options snd-hda-intel model:auto". This chip has had problems with Alsa, but the current version seems to work fine. If hardware mixing isn't possible, oh well, but any type of mixed sounds will do by now.  

Thanks for reading and please, if you know how to get ALSA mixing, let me know. Thanks!

---

### Post by BatPenguin on 2009-01-03
Well, like I thought it might - this turned out to be a rather simple fix to /etc/asound.conf. This works:

```
pcm.!default { type plug slave.pcm "dmixer"
}
pcm.dmixer { type dmix ipc_key 1025 slave { pcm "hw:0,1" period_time 0 period_size 1024 buffer_size 4096 rate 44100
}
bindings { 0 0 1 1
}
} 
```

It creates the dmixer as the default device, and now programs using Alsa can play at the same time.

I'm marking this thread as solved now, but hopefully this little bit of information can help somebody later on. Looks like these Intel HDA cards are not quite as plug & play as one would hope.

---

### Post by afrodeity on 2010-07-02
bump

---

