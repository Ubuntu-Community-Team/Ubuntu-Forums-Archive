---
title: "No capture from USB soundcard"
date: 2008-10-29
forum: Multimedia Software
---

### Post by donr on 2008-10-29
I have a USB soundcard (a TI chip embedded in a ham radio device).
It worked fine under 7.10, but with both 8.04 and 8.10, the capture volume is too low to use.

Alsamixer shows _NO_ capture controls for this card.

The device seems to be recognized:
 $ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 9
 1 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio ODEC  at usb-0000:00:1d.1-1, full s

$ cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control
  8: [ 1- 0]: digital audio playback
  9: [ 1- 0]: digital audio capture
 10: [ 1]   : control

 $ cat /proc/asound/pcm
00-01: STAC92xx Digital : STAC92xx Digital : playback 1
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 3
01-00: USB Audio : USB Audio : playback 1 : capture 1

Any help or ideas will be appreciated.

---

