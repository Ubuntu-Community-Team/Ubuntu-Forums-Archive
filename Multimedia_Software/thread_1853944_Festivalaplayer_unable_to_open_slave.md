---
title: "Festival/aplayer unable to open slave"
date: 2011-10-03
forum: Multimedia Software
---

### Post by Bradburts on 2011-10-03
I am running 10.04 server within VirtualBox. My sound card is a USB dongle.
 
**** List of PLAYBACK Hardware Devices ****
card 0: I82801AAICH [Intel 82801AA-ICH], device 0: Intel ICH [Intel 82801AA-ICH]
Subdevices: 0/1
Subdevice #0: subdevice #0
 
I have configured mpd and music playback is fine. /etc/mpd.conf:-
audio_output {
type "alsa"
name "My ALSA Device"
device "hw:0,0" # optional
format "44100:16:2" # optional
mixer_device "default" # optional
mixer_control "PCM" # optional
mixer_index "0" # optional
}
 
I think that this is correct for mixing. I can hear keyboard event sounds mixed with mpd playback.
When I try and read text with Festival 1.9.6 though I get: 
 
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
aplay: main:608: audio open error: Device or resource busy
 
Have I correctly selected dmix? How should I configure the two packages to work together?

---

### Post by Bradburts on 2011-10-04
misread instructions.
My configuration was attempting hardware mixing, fairly obvious when the device was "hw:0,0".
The setting should be "software".
Strange that I still got keyboard events mixing, perhaps I do have a two channel hardware mixer as well.

---

