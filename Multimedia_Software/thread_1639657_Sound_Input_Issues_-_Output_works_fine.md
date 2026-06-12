---
title: "Sound Input Issues - Output works fine"
date: 2010-12-06
forum: Multimedia Software
---

### Post by aoberoi on 2010-12-06
i know theres a couple thousand threads on sound issues and i tried to look through some before creating a new one... hopefully this isn't too annoying

i have sound output working fine, 5.1 surround. right out of my install of 10.10 it was set to "Analog Stereo Duplex" but i just changed this to "Analog Surround 5.1 Output + Analog Stereo Input" on the Hardware tab of the Sound Preferences, and it worked great!

however for the input i cant get any sound. i am using a fairly older audigy 2 sound card, it has at least 2 inputs (line in and mic). in the Input tab, there is no choice since i guess it only sees one input. i tried connecting my output from my other sound device to both of the inputs available on the card and did not see any action in the "Input level" meter.

so how do i go about debugging this issue?

other notes: i have another audio device (on the motherboard) but i prefer not to use it, so i disabled it on the Hardware tab. i also saw other threads including the output of lspci -v so i have that copied below:
```
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs SB0090 Audigy Player
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at b400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
	Subsystem: Creative Labs SB Audigy Game Port
	Flags: bus master, medium devsel, latency 64
	I/O ports at b800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

```

thanks!

---

### Post by mocha on 2010-12-07
It's probably just muted.  Go into the alsamixer and unmute the line in or the mic.

---

### Post by aoberoi on 2010-12-07
that wasn't it. i played with every control in gnome-alsamixer to try and get it to work.

another couple notes:
- gnome-alsamixer shows the 2 devices with different names, is that normal? the sound blaster audigy device is coming up as TriTech TR28602 and the internal mobo sound device is coming up as Analog Devices AS1980.

- could disabling the mobo sound device have anything to do with this? it doesnt show up as disabled or anything in gnome-alsomixer which i find odd, so i assume they are both talking to the hardware independently and possibly interpreting what they find wrong? it is therefore possible that my line in thats physically on one device could show up as a control for the other?

shots in the dark, but i'm really not sure what to make of this. any other debugging help would be greatly appreciated!

---

### Post by aoberoi on 2010-12-07
GOT IT :D

turns out playing with all the controls one-by-one is the wrong appraoch.

i ended up having to turn up the channel called Line and unmuting it, while also turning up the channel called Analog Mix (all of this in the playback section). thanks for your help!

---

