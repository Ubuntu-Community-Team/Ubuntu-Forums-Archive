---
title: "Sorry! New to Ubuntu! - Sound card and USB problems"
date: 2009-09-06
forum: Multimedia Software
---

### Post by tattwood833 on 2009-09-06
Hello,

sorry.

been using ubuntu for a few months now, dual boots on a samsung laptop.

having real sound issues though, and don't really understand them...

according to system-preferences-sound preferences, I have the following options:-

Autodetect
Burr-Brown from TI USB Audio CODEC USB Audio (ALSA)
HDA Intel ALC262 Digital (ALSA)
HDA Intel ALC262 Analog (ALSA)
Burr-Brown from TI USB Audio CODEC USB Audio (OSS)
Burr-Brown from TI USB Audio CODEC USB Audio (OSS)
HDA Intel ALC262 Analog (OSS)
HDA Intel ALC262 Analog (OSS)
HDA Intel ALC262 Analog (OSS)
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
PulseAudio Sound Server

and in the volume control, I have the following...

HDA Intel (ALSA mixer)
USB Audio CODEC (Alsa mixer)
Realtek ALC262 (OSS mixer)
Playback: HDA Intel - ALC262 Analog (PulseAudio Mixer)
Playback: USB Audio CODEC - USB Audio (PulseAudio Mixer)
Capture: Monitor of HDA Intel - ALC262 Analog (PulseAudio Mixer)
Capture: HDA Intel - ALC262 Analog (PulseAudio Mixer)
Capture: Monitor of USB Audio CODEC - USB Audio (PulseAudio Mixer)
Capture: USB Audio CODEC - USB Audio (PulseAudio Mixer)

practially, I have built in soundcard on the laptop, with built in speakers a headphone and mic socket at the front and a built in mic on the keyboard, by the track pad.
also a behringer USB UCA222 sound interface, 2 phonos in, 2 phonos out, monitor out of 3.5mm jack and optical out.

All I want is to be able to have all sound output via the USB - which i can get a CD to do in rhythmbox player, if I set music and movies to Burr-Brown from TI USB CODEC (OSS), but can't get any application or system sounds to do the same.

Equally I want to be able to record in Audacity via the inputs on the USB, and also record sounds from applications in Audacity.

I can't really work any of this out,

can anyone help?

sometimes when clicking test in sound preferences I get this message next to Burr-Brown from TI USB Audio CODEC (Alsa)
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

if that helps....


thanks!


tom x

---

### Post by aaronchall on 2009-09-20
I'm having a similar problem, I'm looking for an answer...

---

### Post by ^rooker on 2009-10-27
Same problem here. :(
Haven't been able to solve it, but I found something out:

I'm somehow suspecting a weird name collision, because Burr_Brown chips are given the name "default" as soundcard name.

Running "gstreamer-properties" from the commandline reveals a more meaningful errormessage:
> Playback open error on device 'default:1': Invalid argument]

It's possible to select it manually as output for pulseaudio (using "pavucontrol") for currently playing audio, but it won't be used as default even if it is set as.

---

