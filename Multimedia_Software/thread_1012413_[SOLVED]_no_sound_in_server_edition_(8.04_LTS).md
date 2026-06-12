---
title: "[SOLVED] no sound in server edition (8.04 LTS)"
date: 2008-12-15
forum: Multimedia Software
---

### Post by ?xunil on 2008-12-15
i am struggling to get sound output to work in server edition (8.04 LTS).  i have installed mpd and ncmpc.  when i try to play an mp3, i hear nothing.  i have gone through...
[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound)

...and i don't see any issues.  here is what i have...

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)

```

```
lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
        Subsystem: VIA Technologies, Inc. Unknown device 0000
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dde00000-dfefffff
        Prefetchable memory behind bridge: d5d00000-ddcfffff
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at e800 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at ec00 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at dfffff00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: VIA Technologies, Inc. Unknown device 0000
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32, IRQ 255
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: Elitegroup Computer Systems Unknown device a101
        Flags: medium devsel, IRQ 5
        I/O ports at e000 [size=256]
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at dc00 [size=256]
        Memory at dffffe00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03) (prog-if 00 [VGA controller])
        Subsystem: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at dfef0000 [disabled] [size=64K]
        Capabilities: <access denied>

```

```
lspci -n
00:00.0 0600: 1106:3123
00:01.0 0604: 1106:b091
00:10.0 0c03: 1106:3038 (rev 80)
00:10.1 0c03: 1106:3038 (rev 80)
00:10.2 0c03: 1106:3038 (rev 80)
00:10.3 0c03: 1106:3104 (rev 82)
00:11.0 0601: 1106:3177
00:11.1 0101: 1106:0571 (rev 06)
00:11.5 0401: 1106:3059 (rev 50)
00:12.0 0200: 1106:3065 (rev 74)
01:00.0 0300: 1106:3122 (rev 03)

```

```
cat /proc/asound/cards
 0 [V8235          ]: VIA8233 - VIA 8235
                      VIA 8235 with CMI9761A+ at 0xe000, irq 5

```

```
lsmod | grep snd
snd_via82xx            29464  1
gameport               16008  1 snd_via82xx
snd_ac97_codec        101028  1 snd_via82xx
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9728  1 snd_via82xx
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  14 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

```

```
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
amixer info
Card default 'V8235'/'VIA 8235 with CMI9761A+ at 0xe000, irq 5'
  Mixer name    : 'C-Media Electronics CMI9761A+'
  Components    : 'AC97a:434d4983'
  Controls      : 41
  Simple ctrls  : 30

```

```
amixer controls
numid=1,iface=MIXER,name='Master Playback Switch'
numid=2,iface=MIXER,name='Master Playback Volume'
numid=19,iface=MIXER,name='PCM Playback Switch'
numid=41,iface=MIXER,name='PCM Playback Volume'
numid=35,iface=MIXER,name='Surround Jack Mode'
numid=7,iface=MIXER,name='Surround Playback Switch'
numid=3,iface=MIXER,name='Center Playback Switch'
numid=4,iface=MIXER,name='Center Playback Volume'
numid=5,iface=MIXER,name='LFE Playback Switch'
numid=6,iface=MIXER,name='LFE Playback Volume'
numid=13,iface=MIXER,name='Line Playback Switch'
numid=14,iface=MIXER,name='Line Playback Volume'
numid=15,iface=MIXER,name='CD Playback Switch'
numid=16,iface=MIXER,name='CD Playback Volume'
numid=12,iface=MIXER,name='Mic Boost (+20dB)'
numid=24,iface=MIXER,name='Mic Select'
numid=10,iface=MIXER,name='Mic Playback Switch'
numid=11,iface=MIXER,name='Mic Playback Volume'
numid=8,iface=MIXER,name='PC Speaker Playback Switch'
numid=9,iface=MIXER,name='PC Speaker Playback Volume'
numid=17,iface=MIXER,name='Aux Playback Switch'
numid=18,iface=MIXER,name='Aux Playback Volume'
numid=23,iface=MIXER,name='Mono Output Select'
numid=20,iface=MIXER,name='Capture Source'
numid=21,iface=MIXER,name='Capture Switch'
numid=22,iface=MIXER,name='Capture Volume'
numid=31,iface=MIXER,name='IEC958 Capture Valid Switch'
numid=25,iface=MIXER,name='IEC958 Playback Con Mask'
numid=26,iface=MIXER,name='IEC958 Playback Pro Mask'
numid=29,iface=MIXER,name='IEC958 Playback AC97-SPSA'
numid=27,iface=MIXER,name='IEC958 Playback Default'
numid=30,iface=MIXER,name='IEC958 Playback Source'
numid=28,iface=MIXER,name='IEC958 Playback Switch'
numid=32,iface=MIXER,name='IEC958 Capture Monitor'
numid=33,iface=MIXER,name='IEC958 Capture Switch'
numid=40,iface=MIXER,name='IEC958 Output Switch'
numid=36,iface=MIXER,name='Channel Mode'
numid=34,iface=MIXER,name='DAC Clock Source'
numid=37,iface=MIXER,name='External Amplifier'
numid=38,iface=MIXER,name='Input Source Select'
numid=39,iface=MIXER,name='Input Source Select',index=1

```

```
amixer scontrols
Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Surround',0
Simple mixer control 'Surround Jack Mode',0
Simple mixer control 'Center',0
Simple mixer control 'LFE',0
Simple mixer control 'Line',0
Simple mixer control 'CD',0
Simple mixer control 'Mic',0
Simple mixer control 'Mic Boost (+20dB)',0
Simple mixer control 'Mic Select',0
Simple mixer control 'Video',0
Simple mixer control 'Phone',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958 Capture Monitor',0
Simple mixer control 'IEC958 Capture Valid',0
Simple mixer control 'IEC958 Output',0
Simple mixer control 'IEC958 Playback AC97-SPSA',0
Simple mixer control 'IEC958 Playback Source',0
Simple mixer control 'PC Speaker',0
Simple mixer control 'Aux',0
Simple mixer control 'Mono Output Select',0
Simple mixer control 'Capture',0
Simple mixer control 'Mix',0
Simple mixer control 'Mix Mono',0
Simple mixer control 'Channel Mode',0
Simple mixer control 'DAC Clock Source',0
Simple mixer control 'External Amplifier',0
Simple mixer control 'Input Source Select',0
Simple mixer control 'Input Source Select',1

```

```
amixer contents
numid=1,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=2,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=23,23
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=19,iface=MIXER,name='PCM Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=41,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=25,25
  | dBscale-min=-94.50dB,step=1.50dB,mute=1
numid=35,iface=MIXER,name='Surround Jack Mode'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Shared'
  ; Item #1 'Independent'
  : values=0
numid=7,iface=MIXER,name='Surround Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=3,iface=MIXER,name='Center Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=4,iface=MIXER,name='Center Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=25
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=5,iface=MIXER,name='LFE Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=6,iface=MIXER,name='LFE Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=31,step=0
  : values=25
  | dBscale-min=-46.50dB,step=1.50dB,mute=0
numid=13,iface=MIXER,name='Line Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=14,iface=MIXER,name='Line Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=23,23
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=15,iface=MIXER,name='CD Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=16,iface=MIXER,name='CD Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=24,24
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=12,iface=MIXER,name='Mic Boost (+20dB)'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=24,iface=MIXER,name='Mic Select'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Mic1'
  ; Item #1 'Mic2'
  : values=0
numid=10,iface=MIXER,name='Mic Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=11,iface=MIXER,name='Mic Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=0,0
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=8,iface=MIXER,name='PC Speaker Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=9,iface=MIXER,name='PC Speaker Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=15,step=0
  : values=11
  | dBscale-min=-45.00dB,step=3.00dB,mute=0
numid=17,iface=MIXER,name='Aux Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=18,iface=MIXER,name='Aux Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=31,step=0
  : values=23,23
  | dBscale-min=-34.50dB,step=1.50dB,mute=0
numid=23,iface=MIXER,name='Mono Output Select'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Mix'
  ; Item #1 'Mic'
  : values=1
numid=20,iface=MIXER,name='Capture Source'
  ; type=ENUMERATED,access=rw------,values=2,items=8
  ; Item #0 'Mic'
  ; Item #1 'CD'
  ; Item #2 'Video'
  ; Item #3 'Aux'
  ; Item #4 'Line'
  ; Item #5 'Mix'
  ; Item #6 'Mix Mono'
  ; Item #7 'Phone'
  : values=0,0
numid=21,iface=MIXER,name='Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=22,iface=MIXER,name='Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=15,step=0
  : values=0,0
  | dBscale-min=0.00dB,step=1.50dB,mute=0
numid=31,iface=MIXER,name='IEC958 Capture Valid Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=25,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x0f]
numid=26,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0xcf AES1=0x00 AES2=0x00 AES3=0x00]
numid=29,iface=MIXER,name='IEC958 Playback AC97-SPSA'
  ; type=INTEGER,access=rw------,values=1,min=0,max=3,step=0
  : values=2
numid=27,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x00 AES1=0x82 AES2=0x00 AES3=0x02]
numid=30,iface=MIXER,name='IEC958 Playback Source'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'AC-Link'
  ; Item #1 'ADC'
  ; Item #2 'SPDIF-In'
  : values=1
numid=28,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=32,iface=MIXER,name='IEC958 Capture Monitor'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=33,iface=MIXER,name='IEC958 Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=40,iface=MIXER,name='IEC958 Output Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=36,iface=MIXER,name='Channel Mode'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 '2ch'
  ; Item #1 '4ch'
  ; Item #2 '6ch'
  : values=0
numid=34,iface=MIXER,name='DAC Clock Source'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'AC-Link'
  ; Item #1 'SPDIF-In'
  ; Item #2 'Both'
  : values=2
numid=37,iface=MIXER,name='External Amplifier'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=38,iface=MIXER,name='Input Source Select'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Input1'
  ; Item #1 'Input2'
  : values=0
numid=39,iface=MIXER,name='Input Source Select',index=1
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Input1'
  ; Item #1 'Input2'
  : values=1
```

---

### Post by cariboo on 2008-12-15
I would suggest trying to play an mp3 by using mpg123, it is available in the repository:

```
mpg123 some.mp3
```

I've checked the output of all the commands you listed against my own mp3 server/player, and aside from a different sound card, the results are the same. Mine works, I have the line out going to an old Harmon Kardon receiver, it's loud enough that the neighbors complain. :)

I use randomplay, which in turn uses mpg123 to play my mp3 collection, which is about 10,000 songs. I have randomplay set to not repeat a song for 30 days.

Jim

---

### Post by ?xunil on 2008-12-16
i tried mpg123, but no luck.  i also tried a different distro, slitaz, but no luck.  is there anything else i can try besides alsa?

any other ideas?

thanks,
j

---

### Post by ?xunil on 2008-12-16
oh bother... i figured it out... the machine has an audio front panel as well... (which was hidden behind a plastic snap-in panel, because who needs an audio panel on a server?) ...so this is where my sound was going.

now i just need to figure out how to get the sound on the rear audio panel.

thanks all,
j

---

