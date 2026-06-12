---
title: "(K)ubuntu 7.10 without sound"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by cliowa on 2007-12-07
Dear community,

I recently installed Kubuntu 7.10 but now I do not have any sound whatsoever.

I checked that everything is unmuted in the alsamixer, when I turn of certain channels I even hear a clicking noise in my speakers.
Then I tried all kind of checks/changes from the[Comprehensive Sound Problem Guide]("http://ubuntuforums.org/showthread.php?t=205449"), but that didn't help.

Could you point out any other possibilities? Thank you in advance.

Here's some ouputs:
- "lspci" gives
> lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:07.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0b.0 USB Controller: NEC Corporation USB (rev 41)
00:0b.1 USB Controller: NEC Corporation USB (rev 41)
00:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0c.0 RAID bus controller: Promise Technology, Inc. PDC20276 (MBFastTrak133 Lite) (rev 01)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a2)


- cat /proc/asound/modules gives
> cat /proc/asound/modules
 0 snd_via82xx
 1 snd_emu10k1

 -Then there's aplay -l
> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8233A [VIA 8233A], device 0: VIA 8233A [VIA 8233A]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: V8233A [VIA 8233A], device 1: VIA 8233A [VIA 8233A]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SB Live 5.1], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 1: Live [SB Live 5.1], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SB Live 5.1], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Please do let me know in case there's anything else I can to do help you help me with this problem.
Best regards...Cliowa

---

