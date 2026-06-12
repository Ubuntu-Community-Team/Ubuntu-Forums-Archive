---
title: "Skype Problems with Creative SBLive 5.1 - Alternative to Skype?"
date: 2008-08-28
forum: Multimedia Software
---

### Post by crazy ivan on 2008-08-28
**How the problem came about:** I bought 2 headsets to connect my thinkpad to a family desktop - both running Ubuntu 8.04 - via skype. Installing the official version ran fine on both. But while thinkpad-skype ran out of the box, I got "audio playback problem" on desktop with my SBLive 5.1 card. 

**What I tried to solve it:** I found out that changing the three sound sources in skype options to SB Live 5.1 Dell OEM [SB0220](hw,live 0) removed this issue and I was able to connect the "test call". But there was no sound recorded. So I launched "audio-recorder" and found out that no sound was recorded.. Playing around with the sound-settings (e.g. adding AC 97 channel, here is a [faster way to do it]("http://ubuntuforums.org/showpost.php?p=1423407&postcount=16")) resolved this issue.

**Where I stand:** When I make the test call to Skype now I get my recorded voice played back all scrambled and delayed (same happens with normal skype calls). Searching the forums got me to [Merogio's posts]("http://ubuntuforums.org/showthread.php?t=534558"). All my porblems are totally identical. Just the scrambled up skype microphone is new...

**My ideas: **None.. I'll just leave it as it is.. If someone has another idea how I could call my family using the headset please post it. Maybe the next skype-version (now running 2.0.0.72) will fix it, since I dont have any other sound issues.

Additional info: 
```
 aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Live [SB Live 5.1 Dell OEM [SB0220]], Gerät 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Untergeordnete Geräte: 32/32
  Untergeordnetes Gerät '0: subdevice #0
  Untergeordnetes Gerät '1: subdevice #1
  Untergeordnetes Gerät '2: subdevice #2
  Untergeordnetes Gerät '3: subdevice #3
  Untergeordnetes Gerät '4: subdevice #4
  Untergeordnetes Gerät '5: subdevice #5
  Untergeordnetes Gerät '6: subdevice #6
  Untergeordnetes Gerät '7: subdevice #7
  Untergeordnetes Gerät '8: subdevice #8
  Untergeordnetes Gerät '9: subdevice #9
  Untergeordnetes Gerät '10: subdevice #10
  Untergeordnetes Gerät '11: subdevice #11
  Untergeordnetes Gerät '12: subdevice #12
  Untergeordnetes Gerät '13: subdevice #13
  Untergeordnetes Gerät '14: subdevice #14
  Untergeordnetes Gerät '15: subdevice #15
  Untergeordnetes Gerät '16: subdevice #16
  Untergeordnetes Gerät '17: subdevice #17
  Untergeordnetes Gerät '18: subdevice #18
  Untergeordnetes Gerät '19: subdevice #19
  Untergeordnetes Gerät '20: subdevice #20
  Untergeordnetes Gerät '21: subdevice #21
  Untergeordnetes Gerät '22: subdevice #22
  Untergeordnetes Gerät '23: subdevice #23
  Untergeordnetes Gerät '24: subdevice #24
  Untergeordnetes Gerät '25: subdevice #25
  Untergeordnetes Gerät '26: subdevice #26
  Untergeordnetes Gerät '27: subdevice #27
  Untergeordnetes Gerät '28: subdevice #28
  Untergeordnetes Gerät '29: subdevice #29
  Untergeordnetes Gerät '30: subdevice #30
  Untergeordnetes Gerät '31: subdevice #31
Karte 0: Live [SB Live 5.1 Dell OEM [SB0220]], Gerät 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Untergeordnete Geräte: 8/8
  Untergeordnetes Gerät '0: subdevice #0
  Untergeordnetes Gerät '1: subdevice #1
  Untergeordnetes Gerät '2: subdevice #2
  Untergeordnetes Gerät '3: subdevice #3
  Untergeordnetes Gerät '4: subdevice #4
  Untergeordnetes Gerät '5: subdevice #5
  Untergeordnetes Gerät '6: subdevice #6
  Untergeordnetes Gerät '7: subdevice #7
Karte 0: Live [SB Live 5.1 Dell OEM [SB0220]], Gerät 3: emu10k1 [Multichannel Playback]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

```

```

ivan@ivan-desktop:~$ sudo lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
	Subsystem: Elitegroup Computer Systems K7VZA Mainboard
	Flags: bus master, medium devsel, latency 8
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 2.0
	Capabilities: [c0] Power Management version 2

...

00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
	Subsystem: Creative Labs Unknown device 8066
	Flags: bus master, medium devsel, latency 32, IRQ 5
	I/O ports at e000 [size=32]
	Capabilities: [dc] Power Management version 1

00:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
	Subsystem: Creative Labs Gameport Joystick
	Flags: bus master, medium devsel, latency 32
	I/O ports at e400 [size=8]
	Capabilities: [dc] Power Management version 1

...


```

---

