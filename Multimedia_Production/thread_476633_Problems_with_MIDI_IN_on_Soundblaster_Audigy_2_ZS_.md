---
title: "Problems with MIDI IN on Soundblaster Audigy 2 ZS Platium Pro"
date: 2007-06-17
forum: Multimedia Production
---

### Post by Teh Mick on 2007-06-17
Hello there

I just installed Ubuntu Studio first DVD release on my computer. I have a Creative Soundblaster Audigy 2 ZS Platium connected via MIDI to my Korg Karma Music Workstation.

The problem is MIDI In doesn't work. I can't input any note from my synth to ZynAddSubFX even if they are connected with QjackCtrl.

I can send MIDI to my keyboard with aplaymidi -p 16:32 Toadman.mid and it's works fine. 

My Korg Karma is configured to output on MIDI Channel 01 in GLOBAL mode (for those who know Korg synths)

lspci output:
```

00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0d.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0e.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0e.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0e.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1)

```

aplaymidi -l
```

 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    Audigy 2 ZS [2001]               Audigy MPU-401 (UART)
 16:32   Audigy 2 ZS [2001]               Audigy MPU-401 #2
 17:0    Emu10k1 WaveTable                Emu10k1 Port 0
 17:1    Emu10k1 WaveTable                Emu10k1 Port 1
 17:2    Emu10k1 WaveTable                Emu10k1 Port 2
 17:3    Emu10k1 WaveTable                Emu10k1 Port 3
 24:0    MPU-401 UART                     MPU-401 UART MIDI

```

---

### Post by goobsoft on 2007-06-30
I have the same problem.  Let me know if you figure it out and I'll do the same.

The only think I've come up with thus far is that the front midi input is not supported in alsa.

See "front panel midi connectors" in "Known bugs" on 

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=P17&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=P17&module=emu10k1)

Chad

---

### Post by Mandibela on 2007-11-02
> **goobsoft said:**
> I have the same problem.  Let me know if you figure it out and I'll do the same.

The only think I've come up with thus far is that the front midi input is not supported in alsa.

See "front panel midi connectors" in "Known bugs" on 

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=P17&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=P17&module=emu10k1)

Chad

Hi! I have a MIDI-in problem with Audigy 1 card. 
- I (try to) use a Roland RD-700 and a no-brand MIDI-cable attached to the gamport/midi -connector.
- What does front midi input mean? 
- That link is 404...
- Anyone have any ideas on howto search on?

```
 aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    Audigy 1 [SB0090]                Audigy MPU-401 (UART)
 16:32   Audigy 1 [SB0090]                Audigy MPU-401 #2
 17:0    Emu10k1 WaveTable                Emu10k1 Port 0
 17:1    Emu10k1 WaveTable                Emu10k1 Port 1
 17:2    Emu10k1 WaveTable                Emu10k1 Port 2
 17:3    Emu10k1 WaveTable                Emu10k1 Port 3

```

---

### Post by JohnCub on 2007-11-15
> - What does front midi input mean? 
The Audigy 2 ZS Plat Pro has a daughterboard of sorts that lives in one of the spaces a cd-rom might live in, on the front of the computer.

It is on this front panel daughterboard that they speak of.

---

### Post by MusicianX on 2008-06-01
I have the same problem with MIDI in with my SoundBlaster Live!. The strange thing is, if I boot in Windows XP first and then reboot in Linux Midi in is working!

I have tested it with other distros and the behaviour is the same, so it must be a problem with ALSA.

---

