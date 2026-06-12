---
title: "(Almost) No Sound, Troubleshooting Done"
date: 2009-10-16
forum: Multimedia Software
---

### Post by burtzacarach on 2009-10-16
Hi.
I've been troubleshooting this for a couple of days now, I've done everything on the Comprehensive Sound Problem Solutions Guide 0.5
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
I have three sound cards in my box, and I thought they might be interfering with each other somehow, so when I updated my kernel from
2.6.28-15-generic
to
2.6.31.4
I recompiled it myself with the EMU10k1X driver and the EMU10k1 driver as a module only.
These are my three cards.

Intel Corporation 82801EB/ER (ICH5/ICH5R) onboard
Creative Labs [SB Live! Value] EMU10k1X (Dell OEM)
M-Audio DELTA 1010LT

and I'm trying only to get the Creative card working.
As of right now, I get absolutely no sound from the any of the cards, (I haven't tried getting the 1010LT working but that's a work-in-progress) but when I run my iPod into the LINE-IN of the EMU10k1X, I can get output to my speakers and adjust the level with the GUI mixer and the ALSA mixer.
All the cards work in windows... :confused:
So, I've exhausted all I know what to do in this situation to no avail. Does anyone have any ideas?

Here are some outputs.
```
aplay -l
```
```
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
lspci -k
```
```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb
02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
	Kernel driver in use: serial
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Kernel driver in use: EMU10K1X
	Kernel modules: snd-emu10k1x
02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp
02:03.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
```
```
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at dec0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1X
	Kernel modules: snd-emu10k1x

02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64
	I/O ports at de88 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

```

```
zac@zac-desktop:/usr/src$ grep 'audio' /etc/group
audio:x:29:pulse,root,zac,guest
```

The drivers load, I've spent about 10 hours trying every conceivable switch and option setup in my mixer, my playback device is set correctly, and I have my VLC player configured correctly...
I JUST WANT TO WATCH MY COWBOY BEBOP!
Thanks for any help!

---

