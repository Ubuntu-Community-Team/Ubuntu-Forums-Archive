---
title: "Spotify connect and mpd - share alsa-output"
date: 2019-03-09
forum: Multimedia Software
---

### Post by martin-sjostrand on 2019-03-09
Hello!
I have a small mediaserver running ubuntu server edition, with Kodi on top. It also serves as an mpd-server. The mpd-server streams the music through a DAC (Music Streamer II). I have also installed this, not official, program to be able to use Spotify Connect: [https://github.com/Spotifyd/spotifyd](https://github.com/Spotifyd/spotifyd)
I built it from source since I didn't manage to get the snap-package working for some unknown reason. Had something to do with the permissions. Anyhow... I managed to get it working, but only on a fresh reboot. Using the mpd-server before or inbetween Spotify Connect somehow occupies the alsa-output and Spoitfy Connect disconnects from Spotify upon trying to use it.

My theory is that MPD, when not playing, is still occupying the ALSA-output, but I have no knowledge of how to make it disconnect, or how to route Spotifyd to use another instance of the DAC, if that's even possible. 

I don't know which relevant information to provide except for the config-files for MPD och Spotifyd:

Spotifyd:
```

[global]
username = MyUserNAme
password = MyPassword
backend = alsa
#device = alsa_audio_device # Given by `aplay -L`
#device = My ALSA Device
device = hw:1
#mixer = PCM
volume-control = softvol #alsa # or alsa_linear, or softvol
onevent = command_run_on_playback_event
device_name = Prometheus # Cannot contain spaces
bitrate = 96|160|320
cache_path = cache_directory
volume-normalisation = true
normalisation-pregain = -10

```

The relevant part of the MPD-config

```

# Audio Output ################################################################
#
# MPD supports various audio output types, as well as playing through multiple
# audio outputs at the same time, through multiple audio_output settings
# blocks. Setting this block is optional, though the server will only attempt
# autodetection for one sound card.
#
# An example of an ALSA output:
#
#Inlagt av Martin för att få ut ljudet i Pulseaudio samt DACen
audio_output {
type            "alsa"
name            "My ALSA Device"
#device          "hw:II"
#name            "card1"
#device          "plughw:1,0"
#device          "hw:1,0"
format           "44100:16:2"
mixer_type      "software"
mixer_device    "default"
mixer_control   "PCM"
mixer_index     "0"

```

I would be grateful for some help on this issue!

---

