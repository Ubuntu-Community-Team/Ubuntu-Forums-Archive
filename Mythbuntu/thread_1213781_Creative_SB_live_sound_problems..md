---
title: "Creative SB live sound problems."
date: 2009-07-15
forum: Mythbuntu
---

### Post by nugget1960 on 2009-07-15
Creative SB live sound problems.

I'm new at this, so please excuse any obvious dumbness. I fitted the card and installed Mythbuntu (Ubuntu 9.04 i386 amd64).

I can get sound through the VLC media player, but nothing through MythTV. Is there some MythTV configuration I have to set?


 
This is the information I extracted from my machine:

 lspci
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce PCX 5750] (rev a2)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
04:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
04:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
04:03.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0:cool:
04:03.1 Input device controller: Creative Labs SB Live! Game Port (rev 0:cool:


lsusb
Bus 002 Device 002: ID 2040:8400 Hauppauge 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 073a:2130 Chaplet Systems, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SB Live 5.1
                      SB Live 5.1 (rev.8, serial:0x80641102) at 0xdce0, irq 16




cat /proc/asound/modules
 0 snd_emu10k1


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live 5.1], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0





Any help appreciated

Nugget1960

---

### Post by klc5555 on 2009-07-15
In the frontend setup "General" section is the Alsa setup for mythtv. You can follow the detailed information in the mythtv user manual here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend) Mythtv's default sound device /dev/dsp is frequently not what you want. Rather ALSA:DEFAULT or similar.

If by "no sound in mythtv" you mean just tv itself, but the mythtv internal player will play a dvd with sound, _and_ your tv tuner is a software-encoding analog (not digital) tuner, likewise /dev/dsp (in the backend setup for the tuner) is frequently not correct and /dev/dsp1 or /dev/dsp2 turns out to be necessary.

---

### Post by nugget1960 on 2009-07-18
klc5555, thanks for that. ALSA:Default has got the sound working. Now I just have to fiddle around with the 5.1 surround sound.


Nugget1960

---

