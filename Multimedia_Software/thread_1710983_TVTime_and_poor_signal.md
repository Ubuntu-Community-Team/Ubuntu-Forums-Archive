---
title: "TVTime and poor signal"
date: 2011-03-20
forum: Multimedia Software
---

### Post by HanZro on 2011-03-20
Hi guys. 
I have problem with bad signal in TVTime. Unfortunately I have analog antena on the roof, and its broken or something. Point is, that signal from antena is poor, but still watchable. And here is the problem. if signal is poor, I have no sound in TVtime. Is there any way to fix it? Because in honestech software in Windows is signal worse, than in TVtime, but channels still have sound :) I'll appreciate any idea. :) 

Ubuntu 10.04 Lucid Lynx
TV card: Phillips MuchTV Plus (Saa7134)

---

### Post by BicyclerBoy on 2011-03-20
What part of the world are you ?

Has this worked okay previously?

If this is digital TV DVB-T (guessing from analogue antenna) then the audio & video data is in the same data stream. If the video is watchable (decode-able) then the audio should be okay.

Can you select different audio tracks AC3 (DD5.1) or AAC ?

AFAIK TVTime is a bit out-dated & not likely to work with latm-aac audio.
It does not compare to MythTV.

Try to use VLC or mplayer. VLC has very good tuner interface.
Could try to record to a file to debug playback..

---

### Post by HanZro on 2011-03-21
I'm from Czech republic (Central Europe). In Ubuntu no, but in Windows it works correctly (now Im talking about that sound). No it isn't DVB-T unfortunatelly :(

About AC3 or AAC: I don't know. You mean switch it in TVtime, or directly in Ubuntu? 

I tried VLC and MythTV before TVtime, but both had problem with saa7134 tuner detection. Anyway... Thank you for your advice. :)

---

### Post by BicyclerBoy on 2011-03-21
If this is analogue TV tuner then the output format (video & audio) will be a function of the tuner card & firmware.

Most likely mpeg2 video AAC or PCM audio in a mpeg2-ts container.

The media player (VLC) controls the tuner but requires a driver to be loaded..

There may not be any:
-   firmware
-   driver
-   support of any kind.

Check the tuner is detected
lspci
Check the driver is loaded
lsmod
Check for driver loading errors.
dmesg

A lot of philips sa7134 devices need module options..

Check up on LinuxTV.org.

I would have thought that you will require a DVB-T card to watch any TV in Europe ?

---

### Post by HanZro on 2011-03-22
Driver is detected by TVTime and Xaw for example, I think there is other problem with VLC. 
In TVtime is everything working fine. Except of sound (Even the sound works. Unfortunately, only to the moment when the signal from antenna become worse).

**lspci | grep SAA**
```
00:0c.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
```

**lsmod | grep saa**
```
saa7134_alsa           10380  0 
snd_pcm                70694  6 saa7134_alsa,snd_via82xx,snd_cs4236,snd_wss_lib,snd_ac97_codec,snd_pcm_oss
saa7134               143423  1 saa7134_alsa
ir_common              38875  1 saa7134
snd                    54180  22 saa7134_alsa,snd_wavefront,snd_via82xx,snd_cs4236,snd_wss_lib,snd_ac97_codec,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
v4l2_common            15431  2 tuner,saa7134
videodev               34361  3 tuner,saa7134,v4l2_common
videobuf_dma_sg        10782  2 saa7134_alsa,saa7134
videobuf_core          16356  2 saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134

```

**dmesg | grep saa**
```
[   16.721424] saa7130/34: v4l2 driver version 0.2.15 loaded
[   16.721769] saa7134 0000:00:0c.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.721779] saa7134[0]: found at 0000:00:0c.0, rev: 1, irq: 19, latency: 32, mmio: 0xe8101000
[   16.721789] saa7134[0]: subsystem: 1131:0000, board: Items MuchTV Plus / IT-005 [card=37,insmod option]
[   16.721826] saa7134[0]: board init: gpio is ff00
[   16.721837] IRQ 19/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.824326] saa7134[0]: Huh, no eeprom present (err=-5)?
[   17.037120] tuner 3-0060: chip found @ 0xc0 (saa7134[0])
[   17.299158] saa7134[0]: registered device video0 [v4l2]
[   17.299198] saa7134[0]: registered device vbi0
[   17.299232] saa7134[0]: registered device radio0
[   17.384506] saa7134 ALSA driver for DMA sound loaded
[   17.384546] IRQ 19/saa7134[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.384592] saa7134[0]/alsa: saa7134[0] at 0xe8101000 irq 19 registered as card -2

```


Digitisation in the Czech republic is under construction, but still works in parallel with analogue broadcasting on some places  :)

---

