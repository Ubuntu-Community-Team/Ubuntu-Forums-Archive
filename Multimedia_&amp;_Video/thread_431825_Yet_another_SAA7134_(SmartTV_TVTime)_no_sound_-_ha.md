---
title: "Yet another SAA7134 (SmartTV TVTime) no sound - have weird static"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by bekamyn on 2007-05-03
After countless reading of forums and articles, my kernel has all the necessary modules built and I still can't figure out why I don't have working sound. I have intermittent static with no apparent relation to what's being said on TV.

```
/etc/modprobe.d/saa7134
options saa7134 i2c_scan=1 oss=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-oss
#options saa7134-alsa index=1
options saa7134-oss dsp_nr=1 mixer_nr=1

```



```
=Dmesg]
saa7130/34: v4l2 driver version 0.2.14 loaded
saa7134[0]: quirk: PCIPCI_NATOMA
saa7134[0]: found at 0000:06:00.0, rev: 1, irq: 11, latency: 0, mmio: 0x3c000000
saa7134[0]: subsystem: 1131:2004, board: Philips EUROPA V3 reference design [card=69,autodetected]
saa7134[0]: board init: gpio is 40000
saa7134[0]: i2c eeprom 00: 31 11 04 20 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: 01 40 01 02 02 00 01 03 08 ff 00 b0 ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c scan: found device @ 0x96  [???]
saa7134[0]: i2c scan: found device @ 0xa0  [eeprom]
tuner 1-004b: chip found @ 0x96 (saa7134[0])
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
saa7134 OSS driver for DMA sound loaded
saa7134[0]: registered device dsp1
saa7134[0]: registered device mixer1

```


```
=lsmod]
Module                  Size  Used by
ipv6                  227680  10
snd_seq_oss            28928  0
snd_seq_midi_event      5888  1 snd_seq_oss
snd_seq                43504  4 snd_seq_oss,snd_seq_midi_event
snd_seq_device          6412  2 snd_seq_oss,snd_seq
snd_pcm_oss            41536  0
snd_mixer_oss          14848  2 snd_pcm_oss
nls_utf8                1920  1
capability              3468  0
commoncap               5376  1 capability
fuse                   38804  0
lp                      9928  0
parport_pc             24548  0
parport                30408  2 lp,parport_pc
psmouse                35616  0
saa7134_oss            13592  1
tuner                  61304  0
saa7134               114264  1 saa7134_oss
video_buf              19848  2 saa7134_oss,saa7134
3c589_cs               10504  1
compat_ioctl32          1280  1 saa7134
ir_kbd_i2c              7192  1 saa7134
ir_common              26636  2 saa7134,ir_kbd_i2c
videodev               25600  1 saa7134
v4l2_common            22144  3 tuner,saa7134,videodev
v4l1_compat            12936  2 saa7134,videodev
pcmcia                 31272  1 3c589_cs
ata_generic             5256  0
snd_maestro3           21560  3
snd_ac97_codec         90404  1 snd_maestro3
ac97_bus                2176  1 snd_ac97_codec
snd_pcm                68240  4 snd_pcm_oss,snd_maestro3,snd_ac97_codec
snd_timer              19208  3 snd_seq,snd_pcm
snd_page_alloc          7688  1 snd_pcm
snd                    43108  11 snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_maestro3,snd_ac97_codec,snd_pcm,snd_timer
yenta_socket           24476  5
i2c_piix4               7572  0
soundcore               5984  4 saa7134_oss,snd
rsrc_nonstatic         11276  1 yenta_socket
pcspkr                  2432  0
uhci_hcd               21140  0
i2c_core               17680  4 tuner,saa7134,ir_kbd_i2c,i2c_piix4
pcmcia_core            34488  4 3c589_cs,pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               5380  0
evdev                   8320  0
shpchp                 30240  0
intel_agp              21148  1
agpgart                27952  1 intel_agp


```

```
=lspci]
06:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors EUROPA V3 reference design
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at 3c000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [40] Power Management version 1

```


```
=how I run tvtime]
#!/bin/sh
#-q
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
soxpid=$!
sleep 0.5
tvtime
kill $soxpid

```


From what I understand is that I have to pipe the onboard sound in the tuner into my soundcard. Which is what sox is doing. However, when I do this all I get is interrmittent static with no intelligiable voices/music (whatever the tv is displaying). This static is present independent of tvtime's input (television, s-video, composite)

I have tried both the saa714-alsa and saa7134-oss driver with the same result. I've also tried using the autodetected card/tuner (since this card appears to have an eeprom) and I've tried the various card # that are listed in the saa7134 video4linux wiki as utilitizing the saa7134 chipset. 

I've tried the scanning script which incrementally goes through the card/tuner values. And I've also tried card=13 tuner=54 (The "standard" for the SmartTV card).

Right now I've got all the video4linux, saa7134, oss, alsa items compiled as modules in my kernel (as suggested by various sites and documentation).

But I don't have fully working sound. Anybody got any ideas?

---

### Post by bekamyn on 2007-05-06
I'm going to investigate further the card=? tuner? 

Is it ossible that I have the tuner value correct but the card value is wrong?  Although the card does appear to have an eprom so, I would think it's being auto-detected correctly.

Which takes precedence?

---

### Post by bekamyn on 2007-05-07
```

#dmesg
saa7130/34: v4l2 driver version 0.2.14 loaded
saa7134[0]: quirk: PCIPCI_NATOMA
saa7134[0]: found at 0000:06:00.0, rev: 1, irq: 11, latency: 0, mmio: 0x3c000000
saa7134[0]: subsystem: 1131:2004, board: Medion 7134 [card=12,insmod option]
saa7134[0]: board init: gpio is 40000
saa7134[0]: i2c eeprom 00: 31 11 04 20 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 20: 01 40 01 02 02 00 01 03 08 ff 00 b0 ff ff ff ff
saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 40: ff 22 00 c2 96 ff 02 30 15 ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7134[0]: i2c scan: found device @ 0x96  [???]
saa7134[0]: i2c scan: found device @ 0xa0  [eeprom]
saa7134[0] Cant determine tuner type 22 from EEPROM
saa7134[0] Tuner type is 54
tuner 1-004b: chip found @ 0x96 (saa7134[0])
saa7134[0]: registered device video0 [v4l2]
saa7134[0]: registered device vbi0
saa7134[0]: registered device radio0
saa7134 OSS driver for DMA sound loaded
saa7134[0]: registered device dsp1
saa7134[0]: registered device mixer1

```

Looks like it wasn't getting the right card type and I adde saa7134-dvb

```

#/etc/modprobe.d/saa7134
options saa7134 i2c_scan=1 card=12 tuner=54 oss=1
install saa7134 /sbin/modprobe --ignore-install saa7134; /sbin/modprobe saa7134-oss; /sbin/modprobe saa7134-dvb
#options saa7134-alsa index=1
options saa7134-oss dsp_nr=1 mixer_nr=1

```

Now I have sound and video!

Remaining issues:


Tvtime volume doesn't control sound , because sox is so that means I can't control it Tvtime, which means tvtime should be control the master mixer which should allow control of my laptop's sound card.

---

