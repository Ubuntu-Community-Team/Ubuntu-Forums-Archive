---
title: "sound &quot;jumps&quot; on ibm x20 with Cirrus Logic Crystal CS4281 PCI Audio, ubuntu 9.10"
date: 2009-11-03
forum: Multimedia Software
---

### Post by kubulus on 2009-11-03
hello everybody, 

i just installed ubuntu 9.10 on my old ibm thinkpad x20.
everything works great out of the box, except for sound. well, sound does work, but every few seconds or so, sound jumps as if i would listen to a very scratched cd...

lspci -vv
00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
	Subsystem: IBM Device 0183
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1000ns min, 6000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f4012000 (32-bit, non-prefetchable) [size=4K]
	Region 1: Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: CS4281
	Kernel modules: snd-cs4281

it doesnt matter, which audio-player i use - totem, rhythmbox, vlc (here i tried alsa, pulseaudio, unix oss in audiosettings...). 
so i deinstalled pulseaudio, as mentioned somewhere on the net, and installed esound instead - no success. 
also no better sound by raising volume with alsamixer. this was a solution for others having trouble with their cirrus logic drivers. 
does anybody have an idea what to try next? 
thanks in advance for any hints, help, suggestions...

---

### Post by sea11234 on 2009-12-24
please help i have the same problem with the same computer.

---

### Post by excusemeashish on 2009-12-26
I am also having the same problem.
I've got CSound Blaster PCI 128 4 speaker sound card on my ASUS P5B-MX.WiFi-AP motherboard.
Ubuntu 9.1 has detected the following drivers on my system:
$lspci -v
....
04:00.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]
        Memory at febe0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: CS4281
        Kernel modules: snd-cs4281
....

---

### Post by irmtfan on 2010-10-17
i have exactly the same problem.
ubuntu 10.04.1
here is modinfo
> $ sudo modinfo snd-cs4281

filename:       /lib/modules/2.6.32-25-generic/kernel/sound/pci/snd-cs4281.ko
license:        GPL
description:    Cirrus Logic CS4281
author:         Jaroslav Kysela <perex@perex.cz>
srcversion:     435D2FF4A33BF28E16D01F2
alias:          pci:v00001013d00006005sv*sd*bc*sc*i*
depends:        snd-pcm,snd,snd-opl3-lib,snd-rawmidi,gameport,snd-ac97-codec
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586 
parm:           index:Index value for CS4281 soundcard. (array of int)
parm:           id:ID string for CS4281 soundcard. (array of charp)
parm:           enable:Enable CS4281 soundcard. (array of bool)
parm:           dual_codec:Secondary Codec ID (0 = disabled). (array of bool)


---

### Post by irmtfan on 2010-10-23
*BUMP*
it seems new linux kernels can not detect this old modem. 
anybody can help to solve this issue?

---

### Post by pbburns on 2010-10-24
I have the same problem with sound "jumping" or sounding choppy on my ibm x20 and my ibm 21 on ubuntu 10.04

---

