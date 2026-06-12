---
title: "My AC3 Passthrough Thread - Help!"
date: 2008-11-10
forum: Multimedia Software
---

### Post by Maheriano on 2008-11-10
I'm trying to set up my Ubuntu desktop as my media centre, no more DVD player. So I just did the following in this order:
- installed 8.04 fresh
- installed all updates available
- upgraded to 8.1
- installed Audacious, Alsa, VLC
- went into volume mixer and changed output device to my Chaintech AV710 soundcard (Envy24 chipset).
- Went into Audacious and changed sound device to my Chaintech card in preferences
- added custom asound.conf file:
```
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
- never touched default /var/lib/alsa/asound.state file:
```
state.CK804 {
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
		value.0 25
		value.1 25
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value false
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
		value 31
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value false
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
		value 0
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
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 0
		value.1 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 25
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value false
	}
	control.12 {
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
		comment.dbmin -3450
		comment.dbmax 1200
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
		value false
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
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
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value false
	}
	control.19 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
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
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
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
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 25
		value.1 25
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
		value.0 Mic
		value.1 Mic
	}
	control.27 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.28 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.29 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.30 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.31 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.32 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value cf00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
	}
	control.33 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Default'
		value '0082000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.34 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Playback Switch'
		value false
	}
	control.35 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 3'
		iface MIXER
		name 'IEC958 Playback AC97-SPSA'
		value 0
	}
	control.36 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Duplicate Front'
		value false
	}
	control.37 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Front Input Switch'
		value false
	}
	control.38 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Shared
		comment.item.1 Independent
		iface MIXER
		name 'Surround Jack Mode'
		value Shared
	}
	control.39 {
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
	control.40 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Capture Switch'
		value false
	}
	control.41 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 PCM
		comment.item.1 'Analog In'
		comment.item.2 'IEC958 In'
		iface MIXER
		name 'IEC958 Playback Source'
		value PCM
	}
	control.42 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
}
state.UART {
	control {
	}
}
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
		value.0 25
		value.1 25
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value false
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
		value 31
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'LFE Playback Switch'
		value false
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
		value 0
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
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Surround Playback Volume'
		value.0 0
		value.1 0
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Headphone Playback Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 22
		value.1 22
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 25
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PC Speaker Playback Switch'
		value false
	}
	control.14 {
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
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Phone Playback Switch'
		value false
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Phone Playback Volume'
		value 0
	}
	control.17 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value false
	}
	control.18 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Mic Playback Volume'
		value 0
	}
	control.19 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Boost (+20dB)'
		value false
	}
	control.20 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Line Playback Switch'
		value false
	}
	control.21 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
	}
	control.22 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD Playback Switch'
		value true
	}
	control.23 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'CD Playback Volume'
		value.0 25
		value.1 25
	}
	control.24 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Video Playback Switch'
		value false
	}
	control.25 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Video Playback Volume'
		value.0 0
		value.1 0
	}
	control.26 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Aux Playback Switch'
		value false
	}
	control.27 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Aux Playback Volume'
		value.0 0
		value.1 0
	}
	control.28 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Playback Switch'
		value true
	}
	control.29 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'PCM Playback Volume'
		value.0 25
		value.1 25
	}
	control.30 {
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
		value.0 Mic
		value.1 Mic
	}
	control.31 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Capture Switch'
		value true
	}
	control.32 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 15'
		comment.dbmin 0
		comment.dbmax 2250
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 0
	}
	control.33 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name '3D Control - Switch'
		value false
	}
	control.34 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mix
		comment.item.1 Mic
		iface MIXER
		name 'Mono Output Select'
		value Mix
	}
	control.35 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic1
		comment.item.1 Mic2
		iface MIXER
		name 'Mic Select'
		value Mic1
	}
	control.36 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name '3D Control - Center'
		value 0
	}
	control.37 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 15'
		iface MIXER
		name '3D Control - Depth'
		value 0
	}
	control.38 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Alternate Level to Surround Out'
		value false
	}
	control.39 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Downmix LFE and Center to Front'
		value false
	}
	control.40 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Downmix Surround to Front'
		value false
	}
	control.41 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'External Amplifier'
		value true
	}
	control.42 {
		comment.access read
		comment.type BYTES
		comment.count 52
		iface CARD
		name 'ICE1724 EEPROM'
		value '172414121c01020210c1ff0000ff0000ff0000000101010001000000000000000000000000000000ff000000ff000000ff000000'
	}
	control.43 {
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
		comment.item.10 '64000'
		comment.item.11 '88200'
		comment.item.12 '96000'
		comment.item.13 '176400'
		comment.item.14 '192000'
		comment.item.15 'IEC958 Input'
		iface MIXER
		name 'Multi Track Internal Clock'
		value '44100'
	}
	control.44 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Locking'
		value false
	}
	control.45 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Multi Track Rate Reset'
		value true
	}
	control.46 {
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
		value 'PCM Out'
	}
	control.47 {
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
	control.48 {
		comment.access read
		comment.type INTEGER
		comment.count 22
		comment.range '0 - 255'
		iface MIXER
		name 'Multi Track Peak'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		value.8 0
		value.9 0
		value.10 1
		value.11 0
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
	control.49 {
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
		value 'PCM Out'
	}
	control.50 {
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
		value 'PCM Out'
	}
	control.51 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'IEC958 Output Switch'
		value true
	}
	control.52 {
		comment.access 'read write'
		comment.type IEC958
		comment.count 1
		iface PCM
		device 1
		name 'IEC958 Playback Default'
		value '0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.53 {
		comment.access read
		comment.type IEC958
		comment.count 1
		iface PCM
		device 1
		name 'IEC958 Playback Con Mask'
		value '3fff000f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
	}
	control.54 {
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
- went to System - Preferences - Sound and changed everything to ALSA
- hooked up my Chaintech sound card to my home theatre receiver via fiber optic cable

IT WORKED! So now I'm playing digital audio (I guess it's digital) through the fiber optic cable from the sound card. Now my mission is to get AC3 Passthrough working for DVD. My computer's pretty updated, nothing crazy, most stuff is probably 2 years old, the DVD burner is the only part that's maybe 4 years old.

So here's what I did in my attempt to get it working, maybe you guys could add onto the end to help me out:
- verified my receiver does indeed to Dolby Digital and DTS by using it successfully with a capable DVD player for the last 3 years
- testing is done by playing The Fast And The Furious which has a choice for 5.1 audio specifically in the Language options. I wait for the actual feature presentation to start and check the digital readout of the receiver which always reads Dolby Prologic (analogue).
- playing video via VLC which I know is capable of AC3
- VLC - Tools - Preferences - All - Input / Codecs - Audio Codecs - A/52 - A/52 dynamic range compression - CHECKED
- VLC - Tools - Preferences - All - Input / Codecs - Audio Codecs - DCA - DTS dynamic range compression - CHECKED

I'm guessing these last 2 need to be unchecked so that it passes the audio straight through (hence the name) to the receiver so that it can be decoded by the receiver and distributed to the speakers. The problem when doing that is a constant ticking noise in the speakers and the receiver still reads Dolby Prologic. What do I do now?

---

### Post by psyke83 on 2008-11-10
There's a problem with your configuration - you're completely ignoring the presence of PulseAudio. If you are running Intrepid (and didn't uninstall PulseAudio), then your custom asound.conf file is most likely being ignored completely (except when you explicitly specify the device per-application, as you seem to have done).

You may want to install the PulseAudio utilities and take a look at the PulseAudio Volume Control and PulseAudio Manager to check if your applications are playing sound via PulseAudio or not.

```
$ sudo apt-get install padevchooser
```

Once installed, you can gain access to these utilities via the "Applications/Sound/PulseAudio Device Chooser" applet.

P.S. Steps 2-5 of [this]("http://ubuntuforums.org/showthread.php?t=866965") guide will ensure you have a properly configured PulseAudio with the necessary libraries and configuration utilities installed. You may want to investigate this solution for your system, as PulseAudio provides a lot of extra functionality over ALSA (if configured properly).

---

### Post by Maheriano on 2008-11-11
I did the line you posted and followed those steps in the guide, now I have no sound. When I changed everything to Auto Detect and clicked Test, there's no sound coming out. There's also no sound for Audacious after changing its preferences to Pulse Audio and nothing for VLC either. What have I done?

---

### Post by psyke83 on 2008-11-12
> **Maheriano said:**
> I did the line you posted and followed those steps in the guide, now I have no sound. When I changed everything to Auto Detect and clicked Test, there's no sound coming out. There's also no sound for Audacious after changing its preferences to Pulse Audio and nothing for VLC either. What have I done?

It may be a trivial problem.

Open the PulseAudio Volume Control (pavucontrol), Output Devices tab. If there are multiple entries listed on that page then it's possible that the wrong output device is set as the default. You can right-click on any entry and choose to make it the default sink (i.e., output device).

N.B. PulseAudio also saves the last-used sink per-application, which means that some applications may not obey your selected default device. Simply delete the file "~/.pulse/volume-restore.table" to fix that problem, or in the PA Volume Control's Playback tab, you can right-click on playback items and choose to move the sink.

Also ensure your volume levels are sane, as many users seem to have a problem with their PCM mixer getting muted:
```
$ alsamixer -Dhw
```

---

### Post by Maheriano on 2008-11-12
I did that and I still have no sound. However when I go to the PulseAudio applet and click Volume Meter (Playback) I can see the bars moving indicating sound going through the 2 channels. That's both when I go to System - Preferences - Sound - Test and also when playing a DVD in VLC. So now how do I get that sound coming through my speakers?

---

### Post by psyke83 on 2008-11-12
> **Maheriano said:**
> I did that and I still have no sound. However when I go to the PulseAudio applet and click Volume Meter (Playback) I can see the bars moving indicating sound going through the 2 channels. That's both when I go to System - Preferences - Sound - Test and also when playing a DVD in VLC. So now how do I get that sound coming through my speakers?

While something is playing (in VLC, for example), open PA Volume Control, Playback tab. You'll see a client connection called something like "ALSA plug-in [VLC]". Right click on that entry and select "Move stream", and try a different sink.

That should almost certainly solve your issue, or the PCM slider is muted. Don't discount the latter possibility, as the PCM mixer sometimes gets hidden via the GUI. In that case you may need to use alsamixer (see my last post).

---

### Post by Maheriano on 2008-11-12
That didn't do it, PulseAudio is set to ICE1724 and the only other option is the Nvidia CK804 which is the on board SPDIF and obviously I don't want to use that. But when I go into AlsaMixer, I see the card is specified as the Nvidia card, it should be the Chaintech or ICE.....how do I change that? Would that cause it?

---

### Post by Maheriano on 2008-11-13
Anyone?

---

### Post by Maheriano on 2008-11-13
Okay so I went into Pulse Audio and changed the sink and the stream to my Nvidia CK804 (on board) SPDIF out for now, I'll worry about switching it to the PCI card later. So I'm getting playback in VLC through my speakers via Pulse Audio. The problem is that it's still Dolby Pro Logic, not Dolby Digital. What else is there left to change?

---

### Post by Maheriano on 2008-11-13
Okay, I got the Dolby Digital and DTS working on the NVidia on board SPDIF. Anyone want to guess why the SPDIF on the sound card isn't working in Pulse Audio but it does work in ALSA alone? And does anyone know exactly what I would need to change to get everything switched over to the sound card? I feel like I don't want to mess with anything but I got to unload the processes from my CPU.

---

### Post by riromero on 2008-11-14
I was never able to configure VLC to pass through AC3. All I did was waste time. What worked for me in the end was to switch to mplayer. The following produced beautiful DVD sound.

```
mplayer dvd:\\1 -ao alsa -ac hwac3
```

Adding insult to injury, I had to remove all my custom configurations that I had generated during testing and use the installed defaults before this worked. Keep in mind, however, that I have a different sound card.

---

### Post by Maheriano on 2008-11-14
There is an option in VLC for "High Quality Audio Resampling" and I figured all resampling would have to be off so I unchecked the box. It wasn't until I checked it on again that the passthrough started working.

---

### Post by FreakNGoat on 2008-11-17
Yeah, here's the thing with the Chaintech card that's kinda weird, and 
probably one of the sources of difficulty for getting it set up. The two 
main reasons why this card is such a great deal is because of it's 
excellent Wolfson DAC and the SPDIF output digital output. The catch is 
that the Wolfson DAC is attached to the REAR outputs of the card (and 
I'm pretty sure to use the SPDIF output you've got to configure 2 
channel output on the rear channels as well, but I'm not sure on this 
point).

It seems all these drivers in Linux want to use the front outputs by 
default. On this card, there's device 0 and device 1; we need it to use 
device 1 I believe. From googling I was able to hack together an ALSA 
configuration to do this, and it worked in some applications (but not 
all, like Wine, and Flash... total bummer having no Pandora). I'd really 
like to setup PulseAudio and get this card up and running right in intrepid.

Following the instructions earlier in the thread, in pavucontrol only 
one device shows up: ALSA PCM on front:0 (ICE1724) via DMA

So it appears PulseAudio only sees the first device on the card, and not 
the second one, which is the one we really want, and the reason we 
bought this dope card to begin with.

---

