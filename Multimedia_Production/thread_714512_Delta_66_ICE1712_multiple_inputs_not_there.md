---
title: "Delta 66 ICE1712 multiple inputs not there?"
date: 2008-03-03
forum: Multimedia Production
---

### Post by seedsca on 2008-03-03
After reading for a couple of hours about alsa, asoundrc, etc.
I feel like my head is spinning....

I'm not even sure this is possible, but. I have a M-audio Delta 66 and a SB Audigy2 zs. I don't see all the inputs the Delta 66.

Audacity only shows:

    /dev/dsp
    /dev/dsp1
    hw:0,0 (audigy adc capture/standard pcm playback)
    hw:0,1 (audigy mic capture)
    hw:0,2 (audigy multichannel capture/pt playback)
    hw:0,4 (audigy p16v)
    hw:1,0 (delta 66 ICE1712 multi)

shouldn't there be more inputs for the ICE1712 chip? like hw:1,1 etc? where are those settings changed. asoundrc just confused me to no end...

I've read the info on this link but it's a bit to over my head.
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html]("http://www.sabi.co.uk/Notes/linuxSoundALSA.html")

This is all I got.

cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0350]
                      Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xc000, irq 18
 1 [M66            ]: ICE1712 - M Audio Delta 66
                      M Audio Delta 66 at 0xc800, irq 21



aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
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
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M66 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/card1/ice1712
M Audio Delta 66 at 0xc800, irq 21

EEPROM:
  Subvendor        : 0x121432d6
  Size             : 28 bytes
  Version          : 1
  Codec            : 0x15
  ACLink           : 0x80
  I2S ID           : 0x1
  S/PDIF           : 0x3
  GPIO mask        : 0x2
  GPIO state       : 0xc0
  GPIO direction   : 0xfd
  AC'97 main       : 0x0
  AC'97 pcm        : 0x0
  AC'97 record     : 0x0
  AC'97 record src : 0x44
  DAC ID #0        : 0x1
  DAC ID #1        : 0x1
  DAC ID #2        : 0x0
  DAC ID #3        : 0x0
  ADC ID #0        : 0x2
  ADC ID #1        : 0x2
  ADC ID #2        : 0x0
  ADC ID #3        : 0x0

Registers:
  PSDOUT03         : 0x0a0a
  CAPTURE          : 0x00003210
  SPDOUT           : 0x0000
  RATE             : 0x08
  GPIO_DATA        : 0xea
  GPIO_WRITE_MASK  : 0x02
  GPIO_DIRECTION   : 0xfd

---

