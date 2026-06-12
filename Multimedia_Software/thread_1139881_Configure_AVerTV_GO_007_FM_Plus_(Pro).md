---
title: "Configure AVerTV GO 007 FM Plus (Pro)"
date: 2009-04-27
forum: Multimedia Software
---

### Post by stew1690 on 2009-04-27
Firstly i am completly new to Xubuntu but am really enjoying the experience and have managed to set this computer up as a server (pat on my back). 
 
After many hours of searching and trying things i still have no clue how to get this card working. I should be clear in that: i only want to use the video out port to connect to a TV and not to use it for watching TV. The end result means playing movies on the computer that are displayed on the TV.
 
These steps i have taken so far are:
Installed mercurial
downloaded the hg tree from v41-dvb made and installed
checked this link ( [http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_GO_007_FM](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_GO_007_FM) )and tried to complete the commands - see below

read loads of posts to no avail
 
I dont know wether i am:
missing firmware
not configured the display settings (not sure how to at the moment)
Flogging a dead horse
 
hope you can help
 
Cheers
 
Stew
 
 
 
**Results from wiki link:**
 
*root@stews-server:/**# modprobe saa7134-oss*
*FATAL: Module saa7134_oss not found.*
 
 
and
 
*root@stews-server:/**# sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp*
*sox soxio: Can't open input file `/dev/dsp1': unknown file type `ossdsp'*
 
 
 
 
**lspci returns**
 
00:09.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
 
**dmesg returns**
 
[ 27.830233] Linux video capture interface: v2.00
[ 28.456467] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 28.493295] PCI: setting IRQ 5 as level-triggered
[ 28.493312] saa7134 0000:00:09.0: found PCI INT A -> IRQ 5
[ 28.493366] saa7133[0]: found at 0000:00:09.0, rev: 208, irq: 5, latency: 64, mmio: 0xcfffe000
[ 28.493381] saa7133[0]: subsystem: 1461:f31f, board: Avermedia AVerTV GO 007 FM [card=57,autodetected]
[ 28.493409] saa7133[0]: board init: gpio is 80400
[ 28.493825] input: saa7134 IR (Avermedia AVerTV GO as /devices/pci0000:00/0000:00:09.0/input/input3
[ 28.770017] saa7133[0]: i2c eeprom 00: 61 14 1f f3 ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770041] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770055] saa7133[0]: i2c eeprom 20: ff d2 fe ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770069] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770084] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770098] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770112] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770127] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770141] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770277] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770292] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770306] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770321] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770335] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770349] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 28.770364] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 29.206383] tuner' 1-004b: chip found @ 0x96 (saa7133[0])
[ 29.256917] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[ 29.293940] tda829x 1-004b: setting tuner address to 61
[ 29.465909] tda829x 1-004b: type set to tda8290+75
[ 34.127230] saa7133[0]: registered device video0 [v4l2]
[ 34.127367] saa7133[0]: registered device vbi0
[ 34.127450] saa7133[0]: registered device radio0
[ 34.190280] Trident4DWaveAudio 0000:00:01.4: found PCI INT B -> IRQ 11
[ 34.275050] saa7134 ALSA driver for DMA sound loaded
[ 34.275161] saa7133[0]/alsa: saa7133[0] at 0xcfffe000 irq 5 registered as card -2

---

### Post by phamthanhnam on 2009-05-06
Sorry, but I feel quite dim with your writing phrase. Do you want to output video signal to TV display?
This TV card has an SVIDEO-IN port to capture input video signal, for example from a handycam (digital video camcorder), not SVIDEO-OUT, so you can't connect it to a TV to display your movies on TV.
You can use this card to view and record your antenna/cable TV signal, listen/record FM, use its remote control and capture video signal from a video camcorder (over an SVIDEO cable).
I developped driver for this card from 12/2008, and my support is already officially in kernel 2.6.29. However Ubuntu 9.04 still uses kernel 2.6.28.
You can switch to kernel 2.6.29, or download v4l-dvb source from [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb) to update driver module saa7134.
You won't need any configuration. Just restart your PC!
To use sound, you need module saa7134-alsa (it's better, and maybe loaded after restarting), because saa7134-oss is no longer available in Ubuntu.
And then, use sox to forward sound from TV card to your speakers.
Hope it may help!

---

