---
title: "Xubuntu 13.04, laptop internal mic not functioning"
date: 2013-04-26
forum: Multimedia Software
---

### Post by kumoshk on 2013-04-26
I have a Compaq Presario CQ-212US Notebook PC. I'm trying Xubuntu 13.04 64-bit on it. So far, so good (my wifi actually works, which is a totally awesome improvement), except that my microphone isn't functional.

The volume is turned up on the microphone. I can adjust the volume, but when I try recording with Audacity, it doesn't record any sound.

I tried opening Alsamixer from the command-line and turning up all the microphone stuff (microphone boost, capture, etc.) there (which wasn't turned up), but that didn't do anything, either. I tried selecting Pulse Audio in Audacity, but that didn't work, either.

The microphone was similarly dysfunctional in every other edition of Xubuntu that I recall, and most versions (not all) of Ubuntu.

However, it's entirely functional in the current stable version of Debian (using Gnome and GTK 2).

Any ideas?

If I type
lspci | grep -i audio
I get
Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)

Regular audio works fine.

---

### Post by kumoshk on 2013-04-26
amixer gives me this output:

```
$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 74
  Mono: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB]
  Front Right: Capture 80 [100%] [6.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 2 [67%] [-6.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB]
  Front Right: Capture 80 [100%] [6.00dB]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Mute-LED Mode',0
  Capabilities: enum
  Items: 'On' 'Off' 'Follow Master'
  Item0: 'Follow Master'

```



But, it switches to the following frequently when I start doing stuff to the mixer:

```

$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 74
  Mono: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 0 [0%] [-74.00dB]
  Front Right: Capture 0 [0%] [-74.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 2 [67%] [-6.00dB] [on]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Disabled'
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Internal Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB]
  Front Right: Capture 80 [100%] [6.00dB]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Mute-LED Mode',0
  Capabilities: enum
  Items: 'On' 'Off' 'Follow Master'
  Item0: 'Follow Master'


```

amixer contents gives me this:

```
$ amixer contents
numid=25,iface=CARD,name='HDMI/DP,pcm=3 Phantom Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=off
numid=15,iface=CARD,name='Headphone Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=off
numid=17,iface=CARD,name='Internal Mic Phantom Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=on
numid=16,iface=CARD,name='Mic Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=off
numid=14,iface=CARD,name='Speaker Phantom Jack'
  ; type=BOOLEAN,access=r-------,values=1
  : values=on
numid=11,iface=MIXER,name='Master Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=10,iface=MIXER,name='Master Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=74,step=0
  : values=74
  | dBscale-min=-74.00dB,step=1.00dB,mute=0
numid=4,iface=MIXER,name='Headphone Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=3,iface=MIXER,name='Headphone Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=74,step=0
  : values=74,74
  | dBscale-min=-74.00dB,step=1.00dB,mute=1
numid=27,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=255,step=0
  : values=255,255
  | dBscale-min=-51.00dB,step=0.20dB,mute=0
numid=6,iface=MIXER,name='Mic Boost Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=4,step=0
  : values=4,4
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=7,iface=MIXER,name='Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=80,step=0
  : values=80,80
  | dBscale-min=-74.00dB,step=1.00dB,mute=0
numid=21,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=22,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=23,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=24,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off
numid=5,iface=MIXER,name='Auto-Mute Mode'
  ; type=ENUMERATED,access=rw------,values=1,items=2
  ; Item #0 'Disabled'
  ; Item #1 'Enabled'
  : values=0
numid=13,iface=MIXER,name='Beep Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=12,iface=MIXER,name='Beep Playback Volume'
  ; type=INTEGER,access=rw---R--,values=1,min=0,max=3,step=0
  : values=2
  | dBscale-min=-18.00dB,step=6.00dB,mute=0
numid=28,iface=MIXER,name='Digital Capture Volume'
  ; type=INTEGER,access=rw---RW-,values=2,min=0,max=120,step=0
  : values=120,120
  | dBscale-min=-30.00dB,step=0.50dB,mute=0
numid=8,iface=MIXER,name='Internal Mic Boost Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=4,step=0
  : values=4,4
  | dBscale-min=0.00dB,step=10.00dB,mute=0
numid=9,iface=MIXER,name='Internal Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=80,step=0
  : values=80,80
  | dBscale-min=-74.00dB,step=1.00dB,mute=0
numid=18,iface=MIXER,name='Mute-LED Mode'
  ; type=ENUMERATED,access=rw------,values=1,items=3
  ; Item #0 'On'
  ; Item #1 'Off'
  ; Item #2 'Follow Master'
  : values=2
numid=2,iface=MIXER,name='Speaker Playback Switch'
  ; type=BOOLEAN,access=rw------,values=2
  : values=on,on
numid=1,iface=MIXER,name='Speaker Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=74,step=0
  : values=74,74
  | dBscale-min=-74.00dB,step=1.00dB,mute=1
numid=20,iface=PCM,name='Capture Channel Map'
  ; type=INTEGER,access=r----R--,values=2,min=0,max=36,step=0
  : values=3,4
  |     | TLV size error (257, 8, 0)!

numid=19,iface=PCM,name='Playback Channel Map'
  ; type=INTEGER,access=r----R--,values=2,min=0,max=36,step=0
  : values=0,0
  |     | TLV size error (257, 8, 0)!

numid=26,iface=PCM,name='Playback Channel Map',device=3
  ; type=INTEGER,access=r----R--,values=8,min=0,max=36,step=0
  : values=0,0,0,0,0,0,0,0
  |     | TLV size error (257, 8, 0)!

```

---

