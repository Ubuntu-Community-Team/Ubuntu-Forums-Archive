---
title: "Mixer problems with M-Audio Revolution 5.1"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by radu_radu on 2007-12-14
I have a problem with my soundcard M-Audio Revolution 5.1 (module snd_ice1724) related to the CD/AUX input.
I have a TV/FM tuner that's connected to the internal CD/AUX input of the soundcard. I use Kradio and Tvtime. I can hear sounds from Kradio (and from Tvtime, too), but it gives me an error message in Kradio's debug window:
```
ALSA Plugin: Error opening PCM device plughw:0,0
```
Also, Kradio has no access to the mixer (it normally does have - it can change the volume on its own line on an nForce2 board with intel8x0). Tvtime can change the volume only if provided with a sound channel name from a built-in list. Is there any way to change the name of a sound channel to match Tvtime's defaults? And how could I give mixer access to Kradio?
I've tried some .asound files, to no avail. The one below, is my last try.
```

# This is ~/.asoundrc
# "Default" upmixes 2 ch. to 5.1 ch
pcm.!default { 
	type plug 
	slave.pcm "upmix"
	} 
ctl.!default { 
	type hw 
	card 0
	}
# 5.1 native surround
pcm.!surround51 { 
	type copy 
	slave.pcm "duplex51"
	} 
ctl.!surround51 { 
	type hw 
	card 0
	}
# Alias for (converted) digital (S/PDIF) output on the card
pcm.S-PDIF {
	type plug
	slave.pcm "dmix-digital"
	}
ctl.S-PDIF {
	type hw
	card 0
	}
# OSS Mixing
pcm.dsp0 {
	type plug 
	slave.pcm "duplex51"
	} 
ctl.dsp0 { 
	type hw 
	card 0
	}
# Hardware (unmixed) access to the card:
pcm.MAudio-hw { 
	type hw 
	card 0 
	} 
# We upmix the 2 stereo channels to the 6 channels 5.1:
pcm.upmix { 
	type route 
	slave.pcm "duplex51" 
		ttable.0.0 1 
		ttable.1.1 1 
		ttable.2.4 1 
		ttable.3.5 1 
		ttable.4.2 1 
		ttable.5.3 0 
	}
# A duplex PCM to use our card in full-duplex mode:
pcm.duplex51 { 
	type asym 
	playback.pcm "dmix-51_analog" 
	capture.pcm "dsnooper" 
	} 
# And finally, the dmix plugin: 
pcm.dmix-51_analog { 
	type dmix 
	ipc_key 1001 # must be unique! 
	slave { 
		pcm "hw:0,0"
		channels 6 
		period_time 0 
		period_size 1024 
		buffer_size 8192 
		format "S32_LE" 
		rate 48000 
		periods 128 
		} 
	bindings { 
		0 0
		1 1 
		2 4 
		3 5 
		4 2 
		5 3 
		} 
	}
# Microphone
pcm.dsnooper {
	type dsnoop 
	ipc_key 1002 
		slave { 
		pcm "hw:0,0" 
		format "S32_LE" 
		rate 48000 
		} 
	} 
# And S/PDIF
pcm.dmix-digital { 
	type dmix 
	ipc_key 1003 
		slave { 
		pcm "hw:0,1" # IEC958 aka. S/PDIF is hw:0.1"
		period_time 0 
		period_size 1024 
		buffer_size 8192 
		rate 48000 
		} 
	} 
ctl.dmix-digital { 
	type hw 
	card 0 
	} 
# EOF

```

---

