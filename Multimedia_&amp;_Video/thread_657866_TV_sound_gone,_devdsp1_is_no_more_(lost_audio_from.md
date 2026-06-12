---
title: "TV sound gone, /dev/dsp1 is no more (lost audio from TV capture card)"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by linuxvacuum on 2008-01-04
My problem is I re-installed alsa-drivers  1.0.15, alsa-lib and alsa-tools, but now I don't hear the sound of my TV in tvtime and in mythtv :popcorn:.
When recording there is also only undesirable sound.


Before I reinstalled these sound drivers, I had **/dev/dsp/ for my integrated audio card** and **/dev/dsp1 for my ASUS TV FM Tuner PCI card**. Now I only have /dev/dsp.


What I want to know is the procedure to autodect all my sound cards when re-installing the alsa drivers.



Thanks everyone, nice forum by the way. It is a real pleasure to learn Linux by reading the vast amount of posts in this great supporting community.

---

### Post by Damanther on 2008-01-04
Wish I could be more help, but you might try going over some of this post and see if any of it helps.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by linuxvacuum on 2008-01-04
Thanks for the info, I am not sure if it is related to TV tuners though.


After installing Ubuntu 7.10, I had sound from my TV recordings. So is it possible to do some kind of **dpkg-reconfigure** command to automatically detect and recover the device /dev/dsp1 ?

MythTV stll sees my TV Tuner, but not its sound input.


Here is a relevant part from dmesg :
> [   27.335053] saa7133[0]: found at 0000:05:08.0, rev: 240, irq: 19, latency: 32, mmio: 0xd0000000
[   27.335058] saa7133[0]: subsystem: 1043:4845, board: ASUS TV-FM 7135 [card=53,autodetected]
[   27.335065] saa7133[0]: board init: gpio is 0
[   27.479643] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[   27.479652] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 20 (level, low) -> IRQ 20
[   27.479668] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   27.490870] saa7133[0]: i2c eeprom 00: 43 10 45 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   27.490877] saa7133[0]: i2c eeprom 10: 00 ff e2 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   27.490883] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 04 08 ff 00 89 ff ff ff ff
[   27.490888] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.490893] saa7133[0]: i2c eeprom 40: ff 14 00 c2 96 ff 01 30 ff ff ff ff ff ff ff ff
[   27.490899] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.490904] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.490914] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   27.704654] tuner 2-004b: chip found @ 0x96 (saa7133[0])
[   27.790823] tuner 2-004b: setting tuner address to 61
[   27.810806] intel8x0_measure_ac97_clock: measured 50724 usecs
[   27.810809] intel8x0: clocking to 46822
[   27.860802] tuner 2-004b: type set to tda8290+75
[   30.150437] tuner 2-004b: setting tuner address to 61
[   30.220426] tuner 2-004b: type set to tda8290+75
[   32.422312] saa7133[0]: registered device video0 [v4l2]
[   32.422326] saa7133[0]: registered device vbi0
[   32.422347] saa7133[0]: registered device radio0
[B][   32.567436] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[   32.567440] saa7134_alsa: Unknown symbol snd_ctl_add
[   32.567460] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[   32.567462] saa7134_alsa: Unknown symbol snd_pcm_new
[   32.567503] saa7134_alsa: disagrees about version of symbol snd_card_register
[   32.567505] saa7134_alsa: Unknown symbol snd_card_register
[   32.567548] saa7134_alsa: disagrees about version of symbol snd_card_free
[   32.567549] saa7134_alsa: Unknown symbol snd_card_free
[   32.567587] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   32.567589] saa7134_alsa: Unknown symbol snd_pcm_stop
[   32.567640] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[   32.567642] saa7134_alsa: Unknown symbol snd_ctl_new1
[   32.567738] saa7134_alsa: disagrees about version of symbol snd_card_new
[   32.567740] saa7134_alsa: Unknown symbol snd_card_new
[   32.567762] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[   32.567764] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[   32.567804] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[   32.567806] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[   32.567869] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   32.567871] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[   32.567959] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[   32.567961] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed[/B]


So from what I understand, my TV tuner is detected fine, but when it comes to its sound part, errors abound!

What files do I have to edit?

---

### Post by linuxvacuum on 2008-01-05
anyone? :KS

---

### Post by linuxvacuum on 2008-01-05
Here is the audio info from **lspci -vv** :

> 05:08.0 **Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)**
	Subsystem: ASUSTeK Computer Inc. TV-FM 7135
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (21000ns min, 8000ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

00:04.0 **Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)**
	Subsystem: ASUSTeK Computer Inc. K8N4-E or A8N-E Mainboard
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at d400 [size=256]
	Region 1: I/O ports at d800 [size=256]
	Region 2: Memory at d0101000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

---

### Post by linuxvacuum on 2008-01-05
#-o

---

### Post by linuxvacuum on 2008-01-06
Hum, does anyone know how mythtv or ubuntu installation gets the /dev/dsp1 from the tv tuner? I just need that step to run it again, then my problem will be solved!

---

### Post by linuxvacuum on 2008-01-08
bump

---

### Post by linuxvacuum on 2008-01-09
Please guys, I really don't want to reinstall the whole OS only for that problem! I am certain there are more advanced users out here!

---

### Post by linuxvacuum on 2008-01-13
OS REINSTALLED :evil:

---

