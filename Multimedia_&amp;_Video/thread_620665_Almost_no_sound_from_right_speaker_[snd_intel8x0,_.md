---
title: "*Almost* no sound from right speaker [snd_intel8x0, 6.06)"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by Vyhd on 2007-11-22
This is interesting, since I haven't seen anything around here with a problem quite like this. Anyway, I accidently toggled a setting I couldn't track down, and I ended up just reinstalling the sound system to get it working again. 

Since the reinstallation, however, I noticed the right speaker puts out almost no sound at all. It puts out just enough to be normally audible at maximum volume, while the left speaker acts normally. (Seeing as the left speaker is connected through the right speaker, I think this is an ALSA problem.)

I already ran through alsamixer and all audio settings are set to the same value for both left and right channels, so that probably isn't an issue.

I'm currently running Ubuntu 6.06.1, and the sound driver is snd-intel8x0. All modules appear to be loaded properly. Have some command output!

lspci | grep audio
> 0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)

lsmod | grep snd
> snd_intel8x0           33692  2
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm


cat /var/lib/alsa/asound.state
```

state.SI7012 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Master Surround Playback Volume'
		value.0 28
		value.1 28
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Center Playback Volume'
		value 0
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value true
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'LFE Playback Volume'
		value 25
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 false
		value.1 false
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Surround Playback Volume'
		value.0 16
		value.1 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Master Playback Switch'
		value.0 true
		value.1 true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Master Playback Volume'
		value.0 31
		value.1 31
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Phone Playback Volume'
		value 0
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		iface MIXER
		name 'Mic Playback Volume'
		value 0
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Line Playback Volume'
		value.0 31
		value.1 31
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'CD Playback Switch'
		value.0 true
		value.1 true
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'CD Playback Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Aux Playback Switch'
		value.0 true
		value.1 true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'PCM Playback Switch'
		value.0 true
		value.1 true
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'PCM Playback Volume'
		value.0 26
		value.1 26
	}
	control.26 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 2
		comment.item.0 Mic
		comment.item.1 CD
		comment.item.2 Video
		comment.item.3 Aux
		comment.item.4 Line
		comment.item.5 Mix
		comment.item.6 'Mix Mono'
		comment.item.7 Phone
		iface MIXER
		name 'Capture Source'
		value.0 Line
		value.1 Mic
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
	}
	control.28 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.30 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.31 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.32 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
	}
	control.34 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 3
	}
	control.35 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 AC-Link
		comment.item.1 'A/D Converter'
		iface MIXER
		name 'IEC958 Playback Source'
		value AC-Link
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Exchange Front/Surround'
		value true
	}
	control.37 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Spread Front to Surround and Center/LFE'
		value true
	}
	control.38 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Off
		comment.item.1 '6 -> 4'
		comment.item.2 '6 -> 2'
		iface MIXER
		name Downmix
		value Off
	}
	control.39 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Shared
		comment.item.1 Independent
		iface MIXER
		name 'Surround Jack Mode'
		value Independent
	}
	control.40 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '2ch'
		comment.item.1 '4ch'
		comment.item.2 '6ch'
		iface MIXER
		name 'Channel Mode'
		value '2ch'
	}
	control.41 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Jack Sense'
		value false
	}
	control.42 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Jack Sense'
		value false
	}
	control.43 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
}

```

I'm not sure what else I need to post, or what else might be affecting the sound levels, so please get back to me if there's anything else that needs to be posted.

---

### Post by keithacole on 2007-11-23
i have the same issue, but, my left channel is ALMOST mute, while the right is fine. only except if i raise the volume of the left side by itself i can manually balance the sound, leaving the faders uneven.

the ONLY thing me and you did in common was reinstall alsa, i however am using gutsy with a sound blaster audigy pci card

---

### Post by Vyhd on 2007-11-23
While I can balance the speakers to 42/100 and turn the volume on the speakers almost to maximum, I don't think I should need ugly workarounds when the system worked fine before. :(

Bump.

---

### Post by FearNoIdea on 2007-11-30
I am having what I believe to be a related issue.  I am running a gateway laptop with Gutsy. Sound was fine until I believe two or three days ago.  Now the left channel is mute, right channel functions fine.  Perhaps something in one of the updates this week broke it?  Not sure if it is related, but I heard mention in some other posts that a language pack update had broken audio on one channel for another user?  

I will post my output too, hopefully the additional information will help.

lsmod | grep snd
```

snd_hda_intel         263712  4 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm


```

cat /var/lib/alsa/asound.state
```

state.Intel {
        control.1 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'Master Playback Volume'
                value.0 15
                value.1 15
        }
        control.2 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Master Playback Switch'
                value.0 false
                value.1 true
        }
        control.3 {
                comment.access 'read write'
                comment.type ENUMERATED
                comment.count 1
                comment.item.0 Mic
                comment.item.1 'Front Mic'
                comment.item.2 Line
                comment.item.3 CD
                iface MIXER
                name 'Input Source'
                value Mic
        }
        control.4 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 15'
                iface MIXER
                name 'Capture Volume'
                value.0 0
                value.1 0
        }
        control.5 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Capture Switch'
                value.0 true
                value.1 true
        }
        control.6 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 4'
                iface MIXER
                name 'Capture Mux Volume'
                value.0 0
                value.1 0
        }
        control.7 {
                comment.access 'read write'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 31'
                iface MIXER
                name 'Front Playback Volume'
                value.0 25
                value.1 25
        }
        control.8 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 2
                iface MIXER
                name 'Front Playback Switch'
                value.0 true
                value.1 true
        }
        control.9 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Off-hook Switch'
                value false
        }
        control.10 {
                comment.access 'read write'
                comment.type BOOLEAN
                comment.count 1
                iface MIXER
                name 'Caller ID Switch'
                value false
        }
        control.11 {
                comment.access 'read write user'
                comment.type INTEGER
                comment.count 2
                comment.range '0 - 255'
                comment.tlv '0000000100000008ffffec1400000014'
                iface MIXER
                name 'PCM Playback Volume'
                value.0 255
                value.1 255
        }
}


```

---

### Post by FearNoIdea on 2007-12-02
If anyone is still following this thread or has this problem I solved it for myself. Interested to hear if my solution works for you.

Problem..

"Sound card was functioning properly. Right and left channels both worked, producing balanced sound.  Now either right or left channel is no longer producing sound."

My solution

```
 amixer set Master unmute,unmute
```

This solved my problem, please post if this solves it for you.

---

### Post by keithacole on 2007-12-02
```
$  amixer set Master unmute,unmute
amixer: Unable to find simple control 'Master',0
```

---

### Post by FearNoIdea on 2007-12-02
Keith

if you run amixer by itself with no parameters you will get a fairly detailed output of your alsa configuration. Note specifically the first entry for me "Master".  The issue I had rendered the Front Left: Playback to [off].  The volume was still balanced with the right, but the channel was off.

```
amixer
```

```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-13.50dB] [on]
  Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 28 [90%] [-4.50dB] [on]
  Front Right: Playback 28 [90%] [-4.50dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]


```

The parameter scontrols will give you a consolidated list of the simple control names you can work with.
```
mixer scontrols
```

```

Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Front',0
Simple mixer control 'Capture',0
Simple mixer control 'Capture Mux',0
Simple mixer control 'Caller ID',0
Simple mixer control 'Input Source',0
Simple mixer control 'Off-hook',0

```

If your audio is functioning out of both channels, though mysteriously unbalanced, you may wish to try... 

```
amixer set Master,0 100%,100%
```

Note that if you have more than one sound card you will have multiple entries for each simple control.  In my case I have one card, so 'Master',0  if I had another it would be 'Master',1

Last interesting thing...  The following command is used to store your current alsa configuration.  side note.  I do not believe that I needed to run this command in order for my changes to stick.  If you notice that your configuration reverts, you will want to run this command.

```

sudo alsactl store

```

---

### Post by Don1500 on 2007-12-02
Check your settings for Rhythmbox, (preferencies/music/pefered format) Should be CD Quality, Lossless (FLAC audio). This worked for me.

---

### Post by keithacole on 2007-12-02
```
$ amixer
Simple mixer control 'Line in',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 138 [54%] [-34.50dB]
  Front Right: Capture 138 [54%] [-34.50dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 102 [40%] [-52.50dB]
  Front Right: Capture 102 [40%] [-52.50dB]
Simple mixer control 'Phone',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB]
  Front Right: Capture 207 [81%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 149 [58%] [-14.50dB]
  Front Right: Playback 149 [58%] [-14.50dB]
Simple mixer control 'IEC958 Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 35 [14%] [-43.00dB]
  Front Right: Playback 35 [14%] [-43.00dB]
Simple mixer control 'IEC958 Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 35 [14%] [-43.00dB]
  Front Right: Playback 35 [14%] [-43.00dB]
Simple mixer control 'IEC958 Unknown',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 35 [14%] [-43.00dB]
  Front Right: Playback 35 [14%] [-43.00dB]
Simple mixer control 'Aux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 255
  Front Left: Capture 207 [81%] [0.00dB]
  Front Right: Capture 207 [81%] [0.00dB]
Simple mixer control 'Analog Center/LFE',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 30 [12%] [-44.25dB]
  Front Right: Playback 30 [12%] [-44.25dB]
Simple mixer control 'Analog Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 77 [30%] [-32.50dB]
  Front Right: Playback 77 [30%] [-32.50dB]
Simple mixer control 'Analog Rear',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 30 [12%] [-44.25dB]
  Front Right: Playback 30 [12%] [-44.25dB]
Simple mixer control 'Analog Source',0
  Capabilities: cenum
  Items: 'Phone' 'Mic' 'Line in' 'Aux'
  Item0: 'Mic'
Simple mixer control 'CAPTURE feedback',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Digital Source',0
  Capabilities: cenum
  Items: 'IEC958 out' 'i2s mixer out' 'IEC958 in' 'i2s in' 'AC97 in' 'SRC out'
  Item0: 'i2s in'
Simple mixer control 'Shared Mic/Line in',0
  Capabilities: enum
  Items: 'Line in' 'Mic in'
  Item0: 'Mic in'

```


```
$ amixer scontrols
Simple mixer control 'Line in',0
Simple mixer control 'Mic',0
Simple mixer control 'Phone',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958 Center/LFE',0
Simple mixer control 'IEC958 Front',0
Simple mixer control 'IEC958 Rear',0
Simple mixer control 'IEC958 Unknown',0
Simple mixer control 'Aux',0
Simple mixer control 'Analog Center/LFE',0
Simple mixer control 'Analog Front',0
Simple mixer control 'Analog Rear',0
Simple mixer control 'Analog Side',0
Simple mixer control 'Analog Source',0
Simple mixer control 'CAPTURE feedback',0
Simple mixer control 'Digital Source',0
Simple mixer control 'Shared Mic/Line in',0

```


i dont have a master control volume, i use analog front, with feisty when my surround was working i could also use analog rear.

```
$ amixer set Anolog Front,0 100%,100%
amixer: Unable to find simple control 'Anolog',0

```

---

### Post by The_Fozz on 2007-12-02
I had/have this same issue.  I purge reinstalled ALSA the last time it happened and everything was fixed, but now a week later, it's all broken again, and I haven't touched anything.  I just tried to reinstall ALSA again like last time and it didn't fix it, going to try again.

I have CK804 onboard audio.

--Justin

EDIT: just tried to reinstall again and still broken.

---

### Post by roblarky on 2008-01-22
I have this problem every time I boot up.  I have to go into the volume mixer, unlock the left and right PCM channels, change the volume slider for the right channel; bingo!  Then I lock the left and right back and go on my merry way.  Annoying, yes, but not as much as having nearly no right volume.

Rob

---

