---
title: "Audio problem with PCTV Pinnacle Hybrid Pro"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by Mescal on 2007-09-18
I's sorry for my English:)

	
I have a problem with my card tv
I immediately succeed to syntonize the video but I do not succeed to listen to the audio
The problem could derive from the graphical card that has incorporated the TV-OUT or it does not interpret like main escape that one of card TV
I partially succeed to resolve the problem following the instructions of this link
[http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa](http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa)
especially here
>   ALSA audio with other applications

To hear the audio through ALSA using tvtime (or other programs that don't support it directly), run the following command after starting tvtime:

arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

It basically records at 32kHz Stereo from the SAA7134 ALSA source (hw:1,0 or change accordingly), and plays it through your default ALSA output. Look at the options from aplay to change your output.

There might be a delay between the video and the audio. To avoid it, specify a device for aplay (not the 'default' device):

arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -D surround41

In order to get full surround sound from the stereo TV audio output, edit your /etc/asound.conf or ~/.asoundrc file as described in ALSA FAQ028 ([http://alsa.opensrc.org/FAQ028](http://alsa.opensrc.org/FAQ028)) and use this device:

arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -D ch51dup

I don't know how to use ALSA directly with xawtv, motv, kdtv, tvtime, or zapping; if you do, please add it in here!

If using arecord still causes a delay between the video and the audio, try using sox:

sox -r 32000 -w -t alsa hw:1,0 -t alsa hw:0,0

Sox might get you mono sound, while all the alsa solutions cause delays. A combination has been known to work:

arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0

If sox doesn't have alsa support, you can try this instead:

arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | play -q -c 2 -r 32000 -w -t wav -

Alternatively you can use alsa's oss-emulation with sox, which seems to result in way better latency then all the above:

sox -q -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp



I asked myself if a simple method exists

I post my dmesg
> [   36.467691] ACPI: PCI Interrupt 0000:05:06.0[A] -> GSI 21 (level, low) -> IRQ 21
[   36.467698] saa7133[0]: found at 0000:05:06.0, rev: 209, irq: 21, latency: 32, mmio: 0xfeaff000
[   36.467704] saa7133[0]: subsystem: 11bd:002f, board: Pinnacle PCTV 310i [card=101,autodetected]
[   36.467712] saa7133[0]: board init: gpio is 600e000
[   36.586599] input: Pinnacle PCTV as /class/input/input5
[   36.586748] ir-kbd-i2c: Pinnacle PCTV detected at i2c-0/0-0047/ir0 [saa7133[0]]
[   36.658037] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   36.658044] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2e 32 e3 ff ff
[   36.658051] saa7133[0]: i2c eeprom 20: 01 2c 01 23 23 01 04 30 98 ff 00 e7 ff 21 00 c2
[   36.658057] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff 15 0e 6c a3 eb 03 c7 80 5a
[   36.658062] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   36.658068] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   36.658074] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   36.658080] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   36.805760] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   36.865646] tuner 0-004b: setting tuner address to 61
[   36.913556] tuner 0-004b: type set to tda8290+75a
[   37.069263] tuner 0-004b: setting tuner address to 61
[   37.117173] tuner 0-004b: type set to tda8290+75a
[   37.215359] saa7133[0]: registered device video0 [v4l2]
[   37.215470] saa7133[0]: registered device vbi0
[   37.215573] saa7133[0]: registered device radio0
[   37.215711] ali1563: SMBus control = 0403
[   37.215827] ali1563_probe: Returning 0
[   37.223692] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 25
[   37.238668] saa7134 ALSA driver for DMA sound loaded
[   37.238695] saa7133[0]/alsa: saa7133[0] at 0xfeaff000 irq 21 registered as card -2


---

