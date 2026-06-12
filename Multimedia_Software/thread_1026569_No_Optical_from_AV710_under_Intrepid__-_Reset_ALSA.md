---
title: "No Optical from AV710 under Intrepid  - Reset ALSA to default?"
date: 2008-12-31
forum: Multimedia Software
---

### Post by prosonik on 2008-12-31
Hi Everybody,

It seems this topic has come up time and time again, 
but I'm not getting any optical from my av710 under Ubuntu 8.10.The weird thing is, when I do a test using aplay, it seems to play, but I do not get any sound out of the card. I have ensured everything is unmuted in alsamixer. I think i have played with alsa configuration too much, and I've overlooked something simple. 

The card was previously working in 8.10 using analog-out I've never had an issue working with it. 

I followed the 8.04 posting here: 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=187920&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=187920&page=2)

Due to the I'm running BOXEE, I have completely uninstalled pulseaudio, so I know that's not getting in the way.

my aplay -l shows:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AV710 [Chaintech AV-710], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AV710 [Chaintech AV-710], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

when I try: 

```
aplay -Dplughw:0,1 /usr/src/alsa/alsa-utils-1.0.16/speaker-test/samples/Front_Center.wav 
Playing WAVE '/usr/src/alsa/alsa-utils-1.0.16/speaker-test/samples/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
```

it plays, but no sound. It just seems like it's muted.

cat /etc/asound.state
```
state.AV710 {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value.0 30
		value.1 30
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
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 19
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
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 21
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 25
		value.1 25
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value false
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		comment.dbmin -4500
		comment.dbmax 0
		iface MIXER
		name 'PC Speaker Playback Volume'
		value 0
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 12
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 22
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
	}
	control.16 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value true
	}
	control.17 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 24
		value.1 24
	}
	control.18 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
		value true
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 27
		value.1 27
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
		value true
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 21
		value.1 21
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value false
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 0
		value.1 0
	}
	control.24 {
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
		value.0 Mix
		value.1 Mix
	}
	control.25 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.26 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 14
		value.1 14
	}
	control.27 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
	control.29 {
		comment.access read
		comment.type BYTES
		comment.count 52
		iface CARD
		name 'ICE1724 EEPROM'
		value '172414121c01020210c1ff0000ff0000ff0000000101010001000000000000000000000000000000ff000000ff000000ff000000'
	}
	control.30 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 '8000'
		comment.item.1 '9600'
		comment.item.2 '11025'
		comment.item.3 '12000'
		comment.item.4 '16000'
		comment.item.5 '22050'
		comment.item.6 '24000'
		comment.item.7 '32000'
		comment.item.8 '44100'
		comment.item.9 '48000'
		comment.item.10 'IEC958 Input'
		iface MIXER
		name 'Multi Track Internal Clock'
		value '12000'
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Locking'
		value true
	}
	control.32 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Reset'
		value false
	}
	control.33 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'IEC958 In L'
		comment.item.4 'IEC958 In R'
		iface MIXER
		name 'H/W Playback Route'
		value 'H/W In 1'
	}
	control.34 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'IEC958 In L'
		comment.item.4 'IEC958 In R'
		iface MIXER
		name 'H/W Playback Route'
		index 1
		value 'PCM Out'
	}
	control.35 {
		comment.access read
		comment.type INTEGER
		comment.count 22
		comment.range '0 - 255'
		iface MIXER
		name 'Multi Track Peak'
		value.0 255
		value.1 255
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		value.8 0
		value.9 0
		value.10 255
		value.11 255
		value.12 0
		value.13 0
		value.14 0
		value.15 0
		value.16 0
		value.17 0
		value.18 0
		value.19 0
		value.20 0
		value.21 0
	}
	control.36 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'IEC958 In L'
		comment.item.4 'IEC958 In R'
		iface MIXER
		name 'IEC958 Playback Route'
		value 'H/W In 0'
	}
	control.37 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 'PCM Out'
		comment.item.1 'H/W In 0'
		comment.item.2 'H/W In 1'
		comment.item.3 'IEC958 In L'
		comment.item.4 'IEC958 In R'
		iface MIXER
		name 'IEC958 Playback Route'
		index 1
		value 'H/W In 1'
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Output Switch'
		value true
	}
	control.39 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 1
		name 'IEC958 Playback Default'
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.40 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		device 1
		name 'IEC958 Playback Con Mask'
		value '3fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.41 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		device 1
		name 'IEC958 Playback Pro Mask'
		value df00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
}

```


finally my ```
cat /etc/asound.conf 
pcm.envy_spdifdmix {
type dmix
ipc_key 1337
slave {
pcm "hw:0,1"
format S32_LE
rate 44100
}
}

pcm.envy_spdif {
type plug
slave {
pcm envy_spdifdmix
}
}

pcm.!default {
type plug
slave {
pcm envy_spdifdmix
}
}

# For ogle
#
pcm.!spdif {
type plug
slave {
pcm "hw:0,1"
format S32_LE
}
}

# For mplayer ao (mplayer -ac hwac3 -ao alsa1x:mplayer)
# For vlc, use mplayer as alsa device
#
pcm.!iec958 {
type plug
slave {
pcm "hw:0,1"
format S32_LE
}
}

pcm.mplayer {
type plug
slave {
pcm "hw:0,1"
format S32_LE
}
}

```

suggestions?

pro

---

