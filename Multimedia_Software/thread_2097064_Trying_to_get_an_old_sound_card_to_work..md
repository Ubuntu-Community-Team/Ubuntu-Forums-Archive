---
title: "Trying to get an old sound card to work."
date: 2012-12-22
forum: Multimedia Software
---

### Post by lethalfang on 2012-12-22
I have a very old sound card that was working on a 32-bit Linux computer. I upgraded to a 64-bit computer now, and want to use that PCI sound card in the new computer, but it's not working. 
The new computer has a builtin sound card, but I would live to have a speaker as well as headphones without switching back and forth. 

```

~$ sudo lspci -vvv

01:01.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Subsystem: VIA Technologies Inc. Albatron PX865PE 7.1
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 22
	Region 0: I/O ports at e080 [size=32]
	Region 1: I/O ports at e000 [size=128]
	Capabilities: [80] Power Management version 1
		Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: snd_ice1724
	Kernel modules: snd-ice1724



```


It actually just makes a low-level humming noise when the speakers are turned on.



Add:
I searched around the internet, and found that I was able to turn on the sound card by executing this command after looking at this [1-year old thread]("http://ubuntuforums.org/showthread.php?t=1818126"):
sudo /sbin/alsa force-reload
However, I need to execute this command every time. 

Any idea to fix this problem permanently?

---

