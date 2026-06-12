---
title: "Microphone stopped working"
date: 2010-02-14
forum: Multimedia Software
---

### Post by dapfy on 2010-02-14
Possibly since I recently connected a USB webcam, my microphones (both laptop builtin and audio jack headset) stopped working :-$.  Since the webcam showed up as an audiodevice, for which I don't want to use it, I unplugged it and even rebooted, to no avail.

Kde sound configuration shows no Audio Capture device.  Kmix, does not by default show mic sliders, and if I make them visible, they start out at 0, and pushing them up doesn't help.

Booting windows, makes it work, but again not after booting back.  I have no clue where to look.  Audacity says (rates pulled up):

==============================
Default capture device number: 5
Default playback device number: 5
==============================
Device ID: 0
Device name: ALSA: HDA Intel: AD198x Analog (hw:0,0)
Input channels: 2
Output channels: 2
Low Input Latency: 0,011610
Low Output Latency: 0,011610
High Input Latency: 0,046440
High Output Latency: 0,046440
Supported Rates: 8000 11025 16000 22050 32000 44100 48000
==============================
Device ID: 1
Device name: ALSA: front
Input channels: 0
Output channels: 2
Low Input Latency: -1,000000
Low Output Latency: 0,011610
High Input Latency: -1,000000
High Output Latency: 0,046440
Supported Rates: 8000 11025 16000 22050 32000 44100 48000
==============================
Device ID: 2
Device name: ALSA: surround40
Input channels: 0
Output channels: 2
Low Input Latency: -1,000000
Low Output Latency: 0,011610
High Input Latency: -1,000000
High Output Latency: 0,046440
Supported Rates: 8000 11025 16000 22050 32000 44100 48000
==============================
Device ID: 3
Device name: ALSA: surround51
Input channels: 0
Output channels: 2
Low Input Latency: -1,000000
Low Output Latency: 0,011610
High Input Latency: -1,000000
High Output Latency: 0,046440
Supported Rates: 8000 11025 16000 22050 32000 44100 48000
==============================
Device ID: 4
Device name: ALSA: surround71
Input channels: 0
Output channels: 2
Low Input Latency: -1,000000
Low Output Latency: 0,011610
High Input Latency: -1,000000
High Output Latency: 0,046440
Supported Rates: 8000 11025 16000 22050 32000 44100 48000
==============================
Device ID: 5
Device name: ALSA: default
Input channels: 128
Output channels: 128
Low Input Latency: 0,042653
Low Output Latency: 0,042653
High Input Latency: 0,046440
High Output Latency: 0,046440
Supported Rates: 8000 9600 11025 16000 22050 32000 44100 48000 88200
==============================
Device ID: 6
Device name: ALSA: dmix
Input channels: 0
Output channels: 2
Low Input Latency: -1,000000
Low Output Latency: 0,042667
High Input Latency: -1,000000
High Output Latency: 0,042667
Supported Rates: 48000
==============================
Device ID: 7
Device name: OSS: /dev/dsp
Input channels: 16
Output channels: 16
Low Input Latency: 0,011610
Low Output Latency: 0,011610
High Input Latency: 0,046440
High Output Latency: 0,046440
Supported Rates:
==============================
Selected capture device: 5 -
Selected playback device: 5 -
Supported Rates: 8000 9600 11025 16000 22050 32000 44100 48000 88200
==============================
Available mixers:
==============================
Available capture sources:
0 - Mic:0
1 - Mix:0
2 - Docking-Station:0
==============================
Available playback volumes:
0 - Master:0
1 - PCM:0
2 - Mic Boost:0
3 - Beep:0
4 - Internal Mic Boost:0
==============================
Capture volume is native
Playback volume is native

---

### Post by dapfy on 2010-02-19
It got worse, sound is no longer audible, neither on the laptop audio-jack, nor on the one in the docking station.  Only the built in speaker works.

But above the keyboard there is an led-lit touch-screen type button for mute, and it now regularly activates itself, maybe once a minute.  Just lovely when listening to something :-(

lspci says:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 30be
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at e4624000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
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

Doesn't anybody have a clue?

---

### Post by Julita on 2010-02-19
Please look at
```
alsamixer
``` if the box is grey with 00, it means it is muted. Unmute with the button "m," the unmuted bar has green box. Those without indicator that correspond to your volume system just move up.

---

### Post by dapfy on 2010-02-21
Thanks, Julita, that solved the speaker part.
 
Mic is alas still dead.  Related to that alsamixer only shows Mic Boost and Internal Mic Boost, both of which don't have 00, and both are raised to 100<>100.  I'm not sure if this is actually the Mic itself.

---

### Post by Julita on 2010-02-21
For microphone, please
sudo apt-get install linux-backports-modules-alsa-karmic-generic
sudo reboot
In alsamixer press TAB button, it will show microphone configuration.

---

### Post by dapfy on 2010-02-23
Ok, installed and rebooted.  That gives me "Mic", which like "Capture" has red L R CAPTUR above it.  Unlike Capture the percentage line is empty and nothing happens when I hit up or down arrows.  In the help screen it looked like space might be an interesting command, but it seems to do nothing either.

Also tried running alsamixer as root, in case some device file has broken permissions, but it didn't change anything.

---

### Post by Julita on 2010-02-23
OK, now please
gnome-volume-control
it is the GUI for your multimedia system. If it doesn't launch,
sudo apt-get install gnome-media
Even though you have KDE, this package can be quite useful.

---

### Post by dapfy on 2010-02-26
Julita, you're amazing!  Just by starting that proggie, or probably through the tonne of dependencies it installed, it started working on its own.  Thank you very much!

---

### Post by dapfy on 2011-06-04
Back to square one.  Maybe because my upgrade from 10.10 to 11.04 was a mess (I used the command line suggested by the login prompt.  It stumbled over some python overflow, I typed r, it started over.  It spent hours downloading the same things again, only to go into an endless loop about a missing file.  I broke it, and got a shell prompt without a clue how to continue.  Reboot failed so I spent a lot of time in the repair system.  Most packages were lost...)

Anyway some things seemed funny, most annoyingly no sound card (the same one lspci showed when booted from CD, it did not in my system).  I went back to install and it was friendly enough to upgrade from 11.04 to 11.04 which fixed most things.  Now at least lspci shows

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

And there are lots of snd-* modules loaded into the kernel.  But gnome-volume-control still shows no sound card, just an empty list.

Even though apt-get check reports no errors, freshly installed alsamixer gives:

cannot open mixer: No such file or directory

/proc/asound/cards says:
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe4624000 irq 47

and there are various verbose but not alarming files under /proc/asound/card0

What to do?

---

