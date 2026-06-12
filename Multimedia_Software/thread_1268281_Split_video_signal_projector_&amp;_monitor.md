---
title: "Split video signal: projector &amp; monitor"
date: 2009-09-16
forum: Multimedia Software
---

### Post by ricardisimo on 2009-09-16
I'd like to have both a monitor and a projector connected to my computer, with a special twist: I want the monitor to display all toolbars, controls, options, whatever, and I want the projector to show ONLY the image, presentation, movie... whatever I'm running. I don't want my audience ever to see my pointer or cursor or menu items, only the content itself as I run it or modify it.

Can this be done? What app? Which connectors? Thanks.

---

### Post by ricardisimo on 2009-09-26
No takers?

---

### Post by rajan on 2009-10-23
how does ooimpress fall short of your needs?

---

### Post by ricardisimo on 2009-10-23
For producing presentations it exceeds my expectations if anything. That wasn't the question, though. Besides, the office presentation is just one example among many of media that might come up.

I want to be able to have the presenter move her/his mouse around the "control screen", for lack of a better term, without it showing on the "room screen" that the audience is staring at. I want to be able to adjust the image geometry, turn subtitles on/off or switch media sources at my end without the audience seeing menus flying fast and furious all over their screen.

Hence the title: How do I split my signal so that I get "dirty" on my monitor and "clean" to the room?

---

### Post by markbuntu on 2009-10-23
You need two outputs from your gpu or two gpus. Nvidia and ati both have gpus and drivers that can do this but I am not so sure what video players allow a separate display from the controls.

What gpu do you have and what driver is it using?

---

### Post by ricardisimo on 2009-10-25
I might not be reading this correctly, but it doesn't seem to say which card, just the brand:
```
VGA compatible controller: nVidia Corporation Device 0615 (rev a2)
	Subsystem: Device 1b0a:9038
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at fbee0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb
```
It's using the proprietary nvidia driver, version 180.

---

### Post by ricardisimo on 2010-07-15
Bumpity-bump.

I'm going to be using my machine as a variety of cinema server, and I'd **_really_** like to figure out how to view my monitor regularly, and have whatever player I'm using only exporting the actual video being shown - and not any of my windows, desktop, mouse action, cursor, etc.

Suppose I'm using VLC for this... Can I select which output it is sending the stream to? Like, just out of HDMI #1, for example? Thanks again.

---

